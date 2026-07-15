# Exercício Prático — Construindo uma Fábrica de Conteúdo Agêntica

**Pipeline Hub-and-Spoke com Skills de Marketing**
IA Aplicada ao Marketing · MBA ESPM

> Estudo de caso condutor: o canal de YouTube de **Riley Brown — [@rileybrownai](https://www.youtube.com/@rileybrownai)**.
> Biblioteca de referência: **[superamped/ai-marketing-skills](https://github.com/superamped/ai-marketing-skills)**.
> Este pacote é uma adaptação em português, no estilo da casa deste repositório.

---

## 1. Em uma frase

Cada squad vira a liderança de operações de conteúdo de uma marca e constrói um
**pipeline automatizado Hub-and-Spoke** — uma peça central densa (Hub) desdobrada
em vários canais (Spokes) — trocando o processo manual por uma **biblioteca de Skills
em Markdown** que os agentes de IA executam, sempre com humano-no-loop.

```
                      ┌─────────────────────────┐
        INSUMO 100%   │   HUB (peça-pivô densa)  │   1 artigo de fundo
        HUMANO   ───▶ │  + 5 Hooks psicológicos  │──▶ ou roteiro de videocast
     (entrevista,     └─────────────────────────┘
      tese, áudio)                │
                                  ▼  Content Repurposer + Humanizer
        ┌───────────┬─────────────┼──────────────┬───────────────┐
        ▼           ▼             ▼              ▼               ▼
   Thread X/     Carrossel     Roteiro        E-mail de       (auditoria
   LinkedIn      Instagram     Reels/TikTok   engajamento      SEO no blog)
```

---

## 2. Por que este exercício (e por que o Riley Brown)

Riley Brown ([@rileybrownai](https://www.youtube.com/@rileybrownai)) construiu mais de
1,5 milhão de seguidores em todas as plataformas operando exatamente este modelo:
transforma **uma** peça de esforço humano alto em dezenas de derivados, roda **skills
em paralelo** e conecta agentes aos lugares onde o time já trabalha (Slack, Notion).
No vídeo-base ele mostra como isolou a criação de introduções numa skill própria
(**Hook Outline**), porque os primeiros segundos decidem a retenção — e discute o
problema gerencial de **"Multiplayer Agents"**: permissões, vazamento de dados e
controle editorial quando várias pessoas e agências compartilham a mesma biblioteca.

Usamos o canal dele como **laboratório vivo**: os títulos e ganchos dos vídeos são
material real de análise, e o modelo operacional dele (duas agências de edição +
um designer de thumbnail separado) é o nosso estudo de caso de governança.

Marcadores do vídeo citados ao longo do exercício:
`[00:02:17]` YouTube Researcher · `[00:04:10]` tarefas em paralelo ·
`[00:05:12]` Hook Outline skill · `[00:06:18]` os primeiros segundos decidem ·
`[00:28:30]` Multiplayer Agents · `[00:30:05]` permissões e vazamento.

---

## 3. Formato, duração e ferramentas

| | |
|---|---|
| **Formato** | Squads de marketing, 3 a 4 alunos |
| **Duração** | 2 semanas OU workshop intensivo de 4 a 6 horas |
| **Ferramentas** | Claude Code, Codex, Cursor **ou** ChatGPT (com instruções via arquivos `.md`) |
| **Colaboração** | Notion / Slack / Google Docs |
| **Repositório-base** | [superamped/ai-marketing-skills](https://github.com/superamped/ai-marketing-skills) + este pacote |

> **Não precisa saber programar.** Uma "Skill" aqui é só um arquivo de texto (`.md`)
> com instruções muito específicas para o agente. Quem escreve boas instruções ganha.

---

## 4. Conceito central: Skill + Foundation + Humano-no-loop

Este repositório separa duas coisas — e o exercício exige que o squad respeite a separação:

- **`foundation/` (o cérebro da marca):** arquivos que descrevem *quem é a marca* —
  voz (`creator-style.md`), dores e vocabulário da audiência (`audience-delight-profile.md`).
  São gerados **uma vez** a partir de material humano real e reaproveitados por todas as skills.
- **`skills/` (as mãos):** arquivos que descrevem *como executar uma tarefa* — pesquisar,
  escrever o Hub, gerar hooks, fazer repurpose. Toda skill começa **carregando só os
  arquivos de foundation que importam** para aquela tarefa (roteamento por header).

Regra de ouro herdada da casa: **a skill é um sismógrafo, não um crítico literário.**
Toda instrução tem que ser *aplicável sem interpretação*. "Tom conversacional" é lixo.
"Frase de abertura tem 3 a 7 palavras" é uma regra.

---

## 5. Passo a passo

### Etapa 1 — Mapeamento e Skill de Pesquisa (Research & Hook Analysis)
Conceito no vídeo `[00:02:17]` · Base no repo: *Competitor Content Analysis* + *Keyword Research*.

1. Escolham a marca do squad (sugestão: a fintech fictícia **FictiPay**, em `insumos/briefing-marca-fictipay.md`, ou uma marca real da sua vertical).
2. Identifiquem **3 concorrentes/referências**. No exemplo conduzido em aula, a referência é o canal do **Riley Brown** (`insumos/caso-riley-brown.md`).
3. Adaptem `skills/skill-pesquisa.md` para instruir o agente a analisar o conteúdo de melhor performance dessas referências (títulos, transcrições, relatórios de SEO).
4. **Entregável da etapa:** um **relatório de gap de conteúdo** com **3 ângulos inexplorados** de alto potencial para a sua marca.

### Etapa 2 — A Peça-Pivô (Hub) e a Hook Skill
Conceito no vídeo `[00:05:12]` e `[00:06:18]` · Base no repo: *Content Strategy* + *Ad Angles*.

1. Peguem **um** dos ângulos da Etapa 1 e alimentem o agente com **referência 100% humana**
   (entrevista, tese da empresa, notas de áudio de um executivo, pesquisa própria) — veja
   `insumos/referencia-humana-entrevista.md`.
2. Gerem o **Hub Content**: um artigo de fundo de ~1.200 palavras **ou** um roteiro de videocast de 15 min.
3. Apliquem uma skill dedicada só a hooks: **5 variações** de gancho, cada uma com um gatilho
   psicológico distinto (contrariante, história pessoal, dado chocante, tensão/curiosity gap, prova/autoridade).
4. **Entregável da etapa:** o Hub + as 5 hooks, com o gatilho de cada uma nomeado.

### Etapa 3 — Repurposing e Humanização (Spokes & Anti-AI Tells)
Conceito no vídeo & repo · Base no repo: *Content Repurposer* + *Humanizer / Anti-AI Detection*.

1. Rodem `skills/skill-repurposer-humanizado.md` para transformar o Hub em:
   - 1 thread analítica para X (Twitter) **ou** LinkedIn;
   - 2 carrosséis **ou** roteiros de Reels para Instagram/TikTok;
   - 1 copy de e-mail de engajamento para a base de leads.
2. **O Teste do "Taste" humano:** passem TODO o material pela camada de humanização — cace e
   remova vocabulário clássico de IA ("mergulhe", "revolucionário", "no cenário atual"), quebre
   paralelismos sintáticos e injete o tom opinativo da marca.
3. **Entregável da etapa:** o portfólio **antes/depois** (output bruto vs. output humanizado).

### Etapa 4 — Orquestração, Paralelismo e Governança (o desafio MBA)
Conceito no vídeo `[00:04:10]`, `[00:28:30]`, `[00:30:05]`.

1. **Fluxograma** do pipeline rodando com **agentes em paralelo** (ex.: Agente A faz repurpose
   para LinkedIn enquanto Agente B audita SEO do blog via Notion). Modelo em `prompts/prompts-etapa4-orquestracao.md`.
2. **Política de governança de 1 página:** como manter a biblioteca de skills atualizada, quais
   barreiras de segurança e quais pontos de **humano-no-loop** antes de qualquer publicação.
   Template em `entregaveis/template-politica-governanca.md`.

---

## 6. Entregáveis avaliados

1. **Biblioteca de Skills da Marca** (`.zip` ou repositório) — no mínimo 3 `.md` customizados:
   `skill-pesquisa.md`, `skill-hook-hub.md`, `skill-repurposer-humanizado.md`, mais os arquivos
   de `foundation/` da marca.
2. **Portfólio "Antes e Depois"** — o Hub + os Spokes, mostrando o comparativo entre o output
   bruto da IA e o output pós-humanização/curadoria do time. Template em `entregaveis/`.
3. **Apresentação executiva (10 min)** — defesa da arquitetura, ganho de produtividade estimado
   e estratégia de governança para escalar entre colaboradores e agências terceirizadas.

Rubrica completa: `entregaveis/rubrica-avaliacao.md`.

---

## 7. Como este pacote está organizado

```
exercicio-mba-espm/
├── README.md                         ← você está aqui (briefing do aluno)
├── GUIA-DO-PROFESSOR.md              ← roteiro de aula, tempos, gabaritos, armadilhas
├── skills/
│   ├── skill-pesquisa.md             ← Etapa 1
│   ├── skill-hook-hub.md             ← Etapa 2
│   └── skill-repurposer-humanizado.md← Etapa 3
├── foundation/
│   ├── creator-style-EXEMPLO.md      ← voz da marca (exemplo preenchido: FictiPay)
│   └── audience-delight-profile-EXEMPLO.md
├── insumos/
│   ├── briefing-marca-fictipay.md    ← a marca do exercício (fintech fictícia)
│   ├── caso-riley-brown.md           ← estudo de caso: canal @rileybrownai
│   ├── referencia-humana-entrevista.md← insumo humano do Hub (Etapa 2)
│   └── dados-concorrentes.md         ← dados de referência p/ a Etapa 1
├── prompts/
│   ├── prompts-etapa1-pesquisa.md
│   ├── prompts-etapa2-hub-hooks.md
│   ├── prompts-etapa3-repurpose-humanizar.md
│   └── prompts-etapa4-orquestracao.md
└── entregaveis/
    ├── template-portfolio-antes-depois.md
    ├── template-politica-governanca.md
    └── rubrica-avaliacao.md
```

**Slides de apresentação da aula:** publicados como Artifact (link entregue junto com este pacote)
e reproduzíveis a partir de `slides-exercicio.html`.
