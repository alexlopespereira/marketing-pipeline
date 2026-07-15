# Prompts — Etapa 1: Pesquisa & Análise de Gap

> Copie e cole no Claude Code / Codex / Cursor / ChatGPT. Os prompts assumem que os arquivos
> deste pacote estão na pasta do projeto. Onde estiver `[ ]`, o squad preenche.

---

## Prompt 1.1 — Ativar a skill de pesquisa

```
Aja como a skill descrita em skills/skill-pesquisa.md. Leia o arquivo inteiro e
SIGA os passos na ordem, inclusive o roteamento de foundation do Passo 1 e o
teste do gap do Passo 4.

Contexto da marca: insumos/briefing-marca-fictipay.md
Foundation disponível: foundation/audience-delight-profile-EXEMPLO.md

Material a analisar (3 referências): insumos/dados-concorrentes.md
Para a referência C, use insumos/caso-riley-brown.md.

Comece declarando quais arquivos de foundation você carregou e por quê. Depois
faça a análise. Não pule o teste do gap. Não invente métricas.
```

## Prompt 1.2 — Forçar o rigor de "mecanismo, não assunto"

```
Revise sua tabela de hooks. Para cada linha, o campo "mecanismo" está descrevendo
o ASSUNTO (ex.: "vídeo sobre IA") ou o MECANISMO psicológico (ex.: "abre com
promessa de tempo comprimido")? Reescreva toda linha que descreve assunto. Só o
mecanismo é reutilizável para a nossa marca.
```

## Prompt 1.3 — Estressar o relatório de gap (papel de professor cético)

```
Assuma o papel de um professor cético. Para cada um dos 3 ângulos que você propôs,
responda com evidência:
1) A audiência REALMENTE procura por isso? Cite o termo/dor do Audience Delight Profile.
2) As 3 referências REALMENTE ignoram? Aponte a ausência.
3) A FictiPay REALMENTE tem autoridade? Cite o briefing ou a entrevista.
Se um ângulo falhar em qualquer uma, descarte e proponha outro. Liste o que
descartou e por quê.
```

## Prompt 1.4 (com marca real) — Coletar material de verdade

```
Vou colar abaixo os 10 títulos de melhor performance de [CONCORRENTE], com as
métricas [views/salvamentos/sessões]. Trate título + primeira frase como a unidade
de análise. Se eu não informar a métrica de alguma peça, marque [SEM MÉTRICA].

[colar títulos + métricas]
```

---

### Saída esperada da Etapa 1 (checklist do aluno)
- [ ] Declaração dos arquivos de foundation carregados.
- [ ] Tabela de mecanismos de hook validados (mecanismo, não assunto).
- [ ] 3 ângulos inexplorados, cada um com dor + evidência de gap + nota de potencial.
- [ ] Seção "o que foi descartado e por quê".
- [ ] Nenhuma métrica inventada; `[SEM MÉTRICA]` onde faltou.
