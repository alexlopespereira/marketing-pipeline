# Tarefa: criar um dashboard Power BI programaticamente (formato PBIP), versionável em git

Quero gerar um relatório Power BI **por código** (sem cliques no Power BI Desktop),
de forma **determinística e versionável em git**, a partir de um CSV de fato.
Já apliquei essa metodologia antes; abaixo está o que funcionou e, sobretudo, os
problemas que precisei resolver por tentativa e erro até os visuais **abrirem** no
Power BI Desktop. Siga isto de perto.

## 1. Formato de saída: PBIP (Power BI Project)
Gere uma pasta PBIP, não um `.pbix` binário. Estrutura:

```
<projeto>/
  <projeto>.pbip                      # launcher (JSON)
  <projeto>.SemanticModel/
    definition.pbism, .platform
    definition/
      model.tmdl, database.tmdl, relationships.tmdl, expressions.tmdl
      tables/*.tmdl                   # 1 arquivo por tabela (TMDL), medidas DAX inclusas
  <projeto>.Report/
    definition.pbir, .platform
    definition/
      report.json, version.json
      pages/pages.json
      pages/<pagina>/page.json
      pages/<pagina>/visuals/<visual>/visual.json   # 1 pasta por visual
```

O modelo é **TMDL** (texto); o relatório é **PBIR** (JSON, um arquivo por visual) —
ambos são preview no Desktop, mas são o que permite diff em git.

## 2. Arquitetura recomendada do gerador
- Um script Python (`gerar_pbip.py`) + **templates Jinja2** para cada arquivo.
- Uma estrutura `PAGES_SPEC` (lista de dicts) como **fonte única de verdade** do
  layout: páginas → visuais → posição/projeções. Templates só renderizam.
- Flags: `--validate` (valida todo JSON gerado), `--dry-run` (gera em tempdir e
  descarta), `--force` (sobrescreve a saída).
- **lineageTag/UUID estáveis**: persista os UUIDs num `.lineage.json` e reutilize
  entre execuções. Sem isso, cada regeneração troca todos os IDs e o diff de git
  fica ilegível (e o Desktop perde o "match" incremental).

## 3. Pré-requisitos no Power BI Desktop (documente para o usuário)
- Versão ≥ 2024.05.
- Habilitar em Opções → Recursos de visualização: **"Salvar como projeto do Power
  BI (.pbip)"** e **"Pasta PBIR para relatórios"**. Reiniciar.

## 4. PROBLEMAS QUE PRECISEI RESOLVER (a parte que mais custou)

### 4.1. Caminho do CSV TEM que ser ABSOLUTO  ← erro mais recorrente
Sintoma ao abrir: **"The supplied file path must be a valid absolute path."** em
TODAS as tabelas. Causa: usei caminho **relativo** no parâmetro M `CsvPath`. O
Power Query exige caminho **absoluto** em `File.Contents`.
- Solução: embuta o caminho **absoluto** (com `/`, que o Power Query aceita no
  Windows) no parâmetro. Faça isso ser o **padrão** do gerador — se ficar como
  opção "relativa", toda regeneração reintroduz o erro.
- Padrão do parâmetro (expressions.tmdl):
  ```
  expression CsvPath = "C:/caminho/abs/dados.csv" meta [IsParameterQuery=true, Type="Text", IsParameterQueryRequired=true]
  ```
- Partição M da tabela:
  ```
  Source = Csv.Document(File.Contents(CsvPath), [Delimiter=",", Encoding=65001, QuoteStyle=QuoteStyle.Csv]),
  Promoted = Table.PromoteHeaders(Source, [PromoteAllScalars=true]),
  Typed = Table.TransformColumnTypes(Promoted, { {"col", type text}, ... })
  ```
- Consequência: ao mover o repositório de pasta, é preciso **regenerar** o PBIP.
  Documente isso.

### 4.2. Encoding e quebras de linha dos arquivos gerados
Escreva **UTF-8 sem BOM** e **LF** (não CRLF). Em Python: `open(path, "w",
encoding="utf-8", newline="\n")`. BOM ou CRLF podem fazer o Desktop recusar.

### 4.3. Estrutura das projeções do visual (o que fazia o visual não abrir)
Cada `visual.json` tem `query.queryState.<role>.projections[]`. Diferencie:
- **medida**: `field.Measure = {Expression:{SourceRef:{Entity}}, Property}`,
  `queryRef = "<Medida>"`, `nativeQueryRef = "<Medida>"`.
- **coluna**: `field.Column = {...}`, `queryRef = "<entidade>.<coluna>"`
  (com o prefixo da entidade!), `nativeQueryRef = "<coluna>"`.
Errar o `queryRef` (ex.: esquecer o prefixo da entidade nas colunas) faz o visual
falhar silenciosamente. `roles` comuns: `Category`, `Series`, `Y`, `Values`,
`Rows`, `Columns`.

### 4.4. Correspondência de lineageTag entre modelo e relatório
Colunas/medidas referenciadas nos visuais precisam existir no TMDL com nomes
idênticos. Ao renomear/remover uma coluna (ex.: trocar `ia` por `categoria`),
atualize **todos**: TMDL da tabela, TMDL da dimensão, projeções dos visuais,
slicers e o `.lineage.json`. Sobra de referência antiga = visual quebrado.

### 4.5. Nomes de `visualType` (PBIR é preview)
Use nomes válidos: `card`, `lineChart`, `barChart`,
`hundredPercentStackedBarChart`, `clusteredColumnChart`, `tableEx`,
`pivotTable`, `slicer`, `textbox`. Se um visual não carregar, o suspeito nº1 é o
`visualType`.

### 4.6. Valide JSON a cada geração
Rode um passo que faça `json.loads` de todo `*.pbip/*.pbir/*.pbism/*.json/.platform`.
Pega vírgula sobrando/escape antes de abrir no Desktop. (Isso valida sintaxe, não
semântica — veja 4.7.)

### 4.7. Não dá para validar semântica sem o Desktop
Ambiente headless valida só o JSON. Abra o `.pbip` no Desktop ao menos uma vez a
cada mudança estrutural. Itere: gerar → validar JSON → abrir → ajustar.

## 5. Receitas de recursos (guardei os JSON que funcionaram)

- **Filtro de nível de relatório** (ex.: restringir o relatório a um subconjunto):
  `report.json` → `"filterConfig": {"filters": [ <filtro Categorical "In"> ]}`.
  O filtro Categorical usa `field.Column`, `type:"Categorical"`, e
  `filter.Where[0].Condition.In` com `Expressions` + `Values` (literais
  `{"Literal":{"Value":"'IA'"}}`).
- **Interação entre visuais (filtrar vs destacar)**: por padrão, clicar numa
  tabela **destaca** (esmaece) o gráfico alvo. Para **filtrar** (mostrar só o
  item), defina em `page.json` → `"visualInteractions": [{"source": "<visualOrigem>",
  "target": "<visualAlvo>", "type": "DataFilter"}]`. Enum de `type`: `Default`,
  `DataFilter` (filtra), `HighlightFilter` (destaca), `NoFilter` (ignora).
- **Rótulos de valores** (barras e linhas): `visual.objects` →
  `{"labels":[{"properties":{"show":{"expr":{"Literal":{"Value":"true"}}}}}]}`.
- **Slicer como dropdown**: `objects` →
  `{"data":[{"properties":{"mode":{"expr":{"Literal":{"Value":"'Dropdown'"}}}}}]}`.
- **Eixo categórico** (histograma por valor discreto): `objects.categoryAxis` com
  `axisType = 'Categorical'` (senão vira eixo contínuo).
- **Ordenação + Top N**: `query.sortDefinition` (measure + Descending) +
  `filterConfig` com filtro `TopN` (subquery com OrderBy/Top).
- **KPI card**: `visualType:"card"`, role `Values` com uma medida (pode ser de
  qualquer tabela, inclusive uma tabela estática pré-computada).

## 6. Detalhe de dados (não é PBIP, mas me travou no Windows)
Ao pré-processar CSV grande em Python no Windows: `csv.field_size_limit(sys.maxsize)`
estoura (`C long` é 32-bit). Reduza o limite até caber num laço try/except.

## 7. Entregáveis que quero
1. `gerar_pbip.py` + templates Jinja2 conforme a arquitetura acima.
2. `PAGES_SPEC` com as páginas/visuais que eu descrever.
3. Caminho do CSV **absoluto por padrão**.
4. `--validate` passando 100%.
5. README curto: pré-requisitos do Desktop + "regenerar ao mover o repo".

Comece propondo a estrutura de arquivos e o `PAGES_SPEC` mínimo (1 página, 1 KPI,
1 gráfico) para eu abrir e validar antes de escalarmos o resto.