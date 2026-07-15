# Guia do Professor — Fábrica de Conteúdo Agêntica

> Roteiro de condução, tempos, demonstrações ao vivo e gabaritos. O aluno recebe o `README.md`;
> este arquivo é seu.

## Objetivo de aprendizagem
Ao fim, o aluno deve conseguir: (1) transformar uma tarefa de marketing numa **skill em `.md`**
com regras aplicáveis; (2) montar um pipeline **Hub-and-Spoke**; (3) reconhecer e remover marcas
de voz robótica; (4) desenhar **governança e humano-no-loop** para operar agentes em equipe.

A mensagem central: **o gargalo deixou de ser produzir; virou julgar.** A IA gera; o valor
humano está em escolher o ângulo, dar a matéria-prima da tese e cortar o que soa falso.

## Duas configurações de tempo

### Workshop intensivo (4–6h)
| Bloco | Tempo | O quê |
|---|---|---|
| Abertura + slides 1–6 | 30 min | Contexto, Riley Brown, Hub-and-Spoke, o que é uma skill |
| **Demo ao vivo** (Etapa 1) | 30 min | Professor roda `skill-pesquisa` no canal do Riley Brown |
| Squads — Etapa 1 | 45 min | 3 ângulos de gap |
| Demo + Squads — Etapa 2 | 60 min | Insumo humano → Hub → 5 hooks |
| Squads — Etapa 3 | 60 min | Repurpose + humanização (antes/depois) |
| Squads — Etapa 4 | 45 min | Fluxograma + governança |
| Apresentações + fechamento | 40 min | 10 min/squad + debrief |

### 2 semanas
- Semana 1: Etapas 1 e 2 (entrega intermediária: gap + Hub + hooks).
- Semana 2: Etapas 3 e 4 + apresentação executiva.

## As 3 demonstrações ao vivo (o que projetar)
1. **Etapa 1 — mecanismo vs. assunto.** Abra `youtube.com/@rileybrownai/videos`, pegue 5 títulos
   reais e classifique o mecanismo com a turma. Recuse todo "é sobre IA". Depois rode o Prompt 1.1.
2. **Etapa 2 — a Hook Outline isolada.** Mostre `[00:05:12]` do vídeo: por que ele fez uma skill só
   de hook. Rode o Prompt 2.1 na entrevista da CEO e mostre a **destilação** antes de qualquer texto.
3. **Etapa 3 — o teste do taste.** Gere um Spoke bruto, projete, e cace os termos de IA **com a
   turma** antes de rodar o Prompt 3.2. Eles precisam sentir o "cheiro de IA" no olho.

## Gabaritos parciais
- **Gap (Etapa 1):** um ângulo forte para a FictiPay = *"Quanto REALMENTE cai na sua conta"* —
  passa nos 3 testes (ver `insumos/dados-concorrentes.md`).
- **Destilação (Etapa 2):** tese, provas e inimigo já estão ao fim de `referencia-humana-entrevista.md`.
- **Governança (Etapa 4):** a resposta certa quase sempre inclui "agência **não** publica" e
  "agente **nunca** edita foundation".

## Erros que você vai ver (e como intervir)
- **Skill genérica** ("escreva um bom post"): peça a regra que um estagiário aplica sem interpretar.
- **Hub sem insumo humano:** o output fica bonito e vazio. Pergunte "que prova sustenta esta frase?".
- **Humanização de fachada:** trocaram "mergulhe" por "explore". Mostre que é outro termo de IA.
- **Ganho de produtividade fantasioso:** exija o tempo de **revisão humana** somado.

## Conexão explícita com o repositório
Este pacote é uma adaptação em português das skills de
[superamped/ai-marketing-skills](https://github.com/superamped/ai-marketing-skills):
Competitor Content Analysis + Keyword Research → `skill-pesquisa`; Content Strategy + Ad Angles →
`skill-hook-hub`; Content Repurposer + Humanizer → `skill-repurposer-humanizado`. Vale mostrar o
repo original para o aluno ver que ele está adaptando algo real, não um exercício de brinquedo.
