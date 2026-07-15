# Estudo de Caso — O canal do Riley Brown (@rileybrownai)

> Este é o **laboratório vivo** do exercício. O professor demonstra cada skill usando o
> canal do Riley Brown como matéria-prima; depois o squad aplica a mesma lógica na própria marca.
> Fontes: [YouTube @rileybrownai](https://www.youtube.com/@rileybrownai) · vídeo-base do exercício.

---

## Por que ele é o caso

Riley Brown construiu **+1,5 milhão de seguidores em todas as plataformas** operando um pipeline
Hub-and-Spoke com skills de IA. Ele não escreve o conteúdo *com* a IA do zero — parte de esforço
humano (a tese, a demo, a fala) e usa agentes para **pesquisar, estruturar e distribuir**.

### Retrato do canal (referência — julho/2026)
| Métrica | Valor aprox. |
|---|---|
| Inscritos | ~256 mil |
| Vídeos publicados | ~194 |
| Views totais | ~10,4 milhões |
| Média por vídeo | ~43,8 mil |
| Engajamento | ~2,83% |
| Nicho | IA aplicada, "vibe coding", agentes para trabalho de conhecimento |

> **Cuidado metodológico:** números de canais mudam. Trate esta tabela como snapshot e marque
> `[SEM MÉTRICA ATUAL]` se o squad não conseguir confirmar ao vivo. A skill de pesquisa exige isso.

---

## Material de análise 1 — Anatomia dos títulos/hooks (para a Etapa 1)

Os títulos do Riley são hooks. Repare que o que se repete não é o **assunto** (IA), e sim o
**mecanismo psicológico**. Esta é a distinção que a `skill-pesquisa.md` cobra.

| Título (representativo do estilo do canal) | Mecanismo do hook |
|---|---|
| "Não acredito que codamos um app com IA em 67 minutos" | **Descrença** + **compressão de tempo** |
| "Construí o 'Perplexity do YouTube' em 20 minutos" | **Compressão de tempo** + prova de velocidade |
| "Ganhando $125 mil/mês como criador de IA" | **Prova de renda** (número que faz parar) |
| "7 Skills que eu uso todo dia pra marketing dentro do Codex" | **Especificidade numérica** + utilidade |
| "Criei um app de anotações com IA (sem escrever código)" | **Curiosity gap** + remoção de barreira |

**Padrão que se repete (≥3 peças):** compressão de tempo ("em X minutos"), número concreto no
título, e a promessa de um resultado que parecia difícil feito fácil.

> Exercício em aula: o professor projeta a página `/videos` do canal e a turma classifica 5 títulos
> reais **ao vivo**, nomeando o mecanismo de cada um. Nenhum "é um vídeo sobre IA" é aceito — só mecanismo.

---

## Material de análise 2 — A "Hook Outline" como skill isolada (para a Etapa 2)

No vídeo-base `[00:05:12]`, Riley conta que **tirou a criação de introduções do fluxo geral e
fez uma skill só para isso**, porque os primeiros segundos decidem a retenção `[00:06:18]`.
É exatamente o que a `skill-hook-hub.md` faz no Passo 4: uma etapa dedicada, 5 gatilhos distintos.

Lição para o squad: **hook não é enfeite do fim; é peça de engenharia própria.** Vale isolar.

---

## Material de análise 3 — O modelo operacional (para a Etapa 4, Governança)

Riley não opera sozinho. A estrutura dele é o nosso estudo de caso de **Multiplayer Agents**
`[00:28:30]` e de governança:
- **Duas agências de edição** (terceirizadas, no exterior).
- **Um designer de thumbnail** separado.
- **Skills em paralelo** `[00:04:10]`: enquanto uma tarefa roda, outra já está em andamento.
- Agentes conectados aos lugares onde o time trabalha (Slack, Notion), o que abre a questão de
  **permissões e vazamento de dados** `[00:30:05]`.

Perguntas que o squad precisa responder na política de governança (Etapa 4), inspiradas nesse modelo:
1. Se uma agência terceirizada usa a biblioteca de skills, o que ela **pode** e o que ela **não pode** ver?
2. Quem tem permissão de **editar** um arquivo de `foundation/` (a voz da marca)?
3. Qual conteúdo pode ir ao ar **sem** um humano aprovar, e qual **nunca** pode?

---

## Como usar este caso em cada etapa

| Etapa | Uso do caso Riley Brown |
|---|---|
| 1 — Pesquisa | Analisar os títulos/hooks do canal e mapear mecanismos validados |
| 2 — Hub + Hooks | Espelhar a decisão dele de isolar a Hook Outline em skill própria |
| 3 — Repurpose | Observar como uma peça (vídeo) vira thread, corte, post — e o que se perde sem humanizar |
| 4 — Governança | Usar o modelo "2 agências + designer + agentes em Slack/Notion" como cenário de permissões |
