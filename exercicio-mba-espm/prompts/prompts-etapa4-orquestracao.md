# Prompts — Etapa 4: Orquestração, Paralelismo e Governança (desafio MBA)

> Aqui o squad deixa de ser "usuário de agente" e vira **gestor de operação de agentes**.
> Referência: o modelo do Riley Brown (2 agências + designer + agentes em Slack/Notion),
> os "Multiplayer Agents" `[00:28:30]` e a questão de permissões/vazamento `[00:30:05]`.

---

## Prompt 4.1 — Rascunhar o fluxograma do pipeline em paralelo

```
Você é um arquiteto de operações de conteúdo. A partir das skills deste pacote
(skill-pesquisa, skill-hook-hub, skill-repurposer-humanizado), desenhe o fluxo de
uma semana de produção rodando com agentes EM PARALELO.

Requisitos:
- Mostre onde há trabalho simultâneo (ex.: Agente A faz repurpose p/ LinkedIn
  enquanto Agente B audita SEO do blog via Notion).
- Marque cada ponto de HUMANO-NO-LOOP (onde uma pessoa aprova antes de seguir).
- Marque onde a foundation/ é lida (nunca escrita por um agente sem aprovação).
Entregue como um diagrama em Mermaid (flowchart) que eu possa colar nos slides.
```

## Prompt 4.2 — Gerar o diagrama Mermaid pronto para os slides

```
Converta o fluxo acima em um bloco Mermaid `flowchart LR` com raias (subgraphs)
para: Pesquisa, Hub, Spokes-em-paralelo e Aprovação Humana. Use nós losango para
os gates de humano-no-loop. Só o código Mermaid, sem explicação.
```

## Prompt 4.3 — Redigir a política de governança de 1 página

```
Aja como diretor de marketing responsável por compliance. Escreva a POLÍTICA DE
GOVERNANÇA DA BIBLIOTECA DE SKILLS em no máximo 1 página, usando o template em
entregaveis/template-politica-governanca.md. Baseie-se no cenário do Riley Brown
(insumos/caso-riley-brown.md): 2 agências terceirizadas + 1 designer + agentes
conectados a Slack/Notion.

Responda explicitamente:
1) Quem pode EDITAR foundation/ (a voz da marca) e como se aprova uma mudança?
2) O que uma agência terceirizada pode e NÃO pode acessar da biblioteca?
3) Qual conteúdo pode ir ao ar sem aprovação humana, e qual NUNCA pode?
4) Como a biblioteca de skills se mantém atualizada (dono, cadência de revisão)?
5) Quais dados NUNCA entram num prompt (PII de cliente, número de contrato, etc.)?
```

## Prompt 4.4 — Estimar o ganho de produtividade (para a apresentação)

```
Estime o ganho de tempo do pipeline vs. o processo manual, de forma honesta e
defensável. Para cada etapa (pesquisa, Hub, 4 Spokes, humanização), dê:
- tempo manual estimado (h);
- tempo com o pipeline + revisão humana (h);
- a premissa por trás de cada número.
Não infle. Inclua o tempo de REVISÃO HUMANA — ele não é zero. Some no fim e
apresente como intervalo (mín–máx), não um número mágico.
```

---

### Saída esperada da Etapa 4 (checklist do aluno)
- [ ] Fluxograma (Mermaid) com trabalho em paralelo e gates de humano-no-loop marcados.
- [ ] Política de governança de 1 página (as 5 perguntas respondidas).
- [ ] Estimativa de produtividade honesta, com premissas e tempo de revisão incluído.
