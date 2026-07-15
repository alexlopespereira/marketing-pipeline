# Política de Governança da Biblioteca de Skills — [MARCA] (1 página)

> Máximo 1 página. Escrita para ser lida por um colaborador novo ou uma agência terceirizada
> no primeiro dia. Referência de cenário: modelo do Riley Brown (2 agências + designer + agentes
> em Slack/Notion) — `insumos/caso-riley-brown.md`.

## 1. Papéis e permissões
| Papel | Pode LER | Pode EDITAR skills | Pode EDITAR foundation | Pode PUBLICAR |
|---|---|---|---|---|
| Editor-chefe (interno) | tudo | sim | sim (com aprovação de 2) | sim |
| Redator (interno) | tudo | propõe (PR) | não | não |
| Agência terceirizada | skills + briefing | propõe (PR) | não | não |
| Agente de IA | o que a skill roteia | não | **nunca** | **nunca** |

## 2. Humano-no-loop: os gates obrigatórios
Nenhum conteúdo vai ao ar sem passar por, no mínimo:
1. **Gate de fato:** um humano confere que todo número/afirmação tem fonte rastreável.
2. **Gate de voz:** um humano roda o teste da COMPARAÇÃO (Creator Style) na peça final.
3. **Gate de marca/compliance:** um humano confere as restrições editoriais do briefing.

O que pode ir ao ar **sem** aprovação: ______ (ex.: nada — tudo passa por gate).
O que **nunca** pode ir sem dois aprovadores: ______ (ex.: peça com dado financeiro).

## 3. Dados que NUNCA entram num prompt
PII de cliente, número de contrato, dado financeiro nominal, credencial, planilha interna
não anonimizada. Insumo humano (entrevistas etc.) só entra **anonimizado**.

## 4. Manutenção da biblioteca
- **Dono da biblioteca:** ______ (uma pessoa nomeada).
- **Cadência de revisão:** ______ (ex.: mensal — revisar listas de banimento e foundation).
- **Como se muda uma skill:** proposta → revisão do dono → teste em 1 peça → merge.
- **Versionamento:** toda skill tem histórico (Git/Drive com versões); nada se edita "por cima" sem registro.

## 5. Riscos e mitigação (mínimo 3)
| Risco | Mitigação |
|---|---|
| Vazamento de dado via prompt | regra da seção 3 + revisão de insumo |
| Voz da marca derretendo com o tempo | gate de voz + foundation versionada |
| Agência publicando sem curadoria | agência não tem permissão de publicar (seção 1) |
