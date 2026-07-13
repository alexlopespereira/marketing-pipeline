# Pacote de Demonstração — Pipeline de Marketing com Claude Code

Kit completo para o **Bloco 5** da aula (40 min de demos ao vivo).
Empresa fictícia: **GiroLeve** — SaaS B2B de fluxo de caixa para e-commerce.

---

## Começar em 2 minutos

```bash
cd aula-marketing-claude-code
claude
```

Pronto. Abra o `ROTEIRO-DEMOS.md` e siga.

> **Requisito:** Claude Code instalado e autenticado. Se `claude` não for
> reconhecido, você ainda tem o `plano-b/` — nenhuma demo depende do terminal.

---

## O que tem aqui

```
aula-marketing-claude-code/
│
├── CLAUDE.md                    ← config do sistema (NÃO é fundação!)
├── ROTEIRO-DEMOS.md             ← ⭐ COMECE AQUI. Guia do professor.
│
├── foundation/                  ← CONHECIMENTO (lido, nunca executado)
│   ├── audience-delight-profile.md
│   ├── creator-style.md
│   ├── market-positioning-map.md
│   └── customer-journey-intelligence.md
│
├── skills/                      ← EXECUÇÃO (acionadas por você)
│   ├── post-linkedin/SKILL.md          → carrega 2 arquivos
│   └── newsletter-nutricao/SKILL.md    → carrega 3 arquivos
│
└── material-bruto/
    └── comentarios-lojistas.md  ← insumo da Demo 1
 
```

---

## A distinção que a turma precisa entender

| | Vive em | O que é | É executada? |
|---|---|---|---|
| **CLAUDE.md** | raiz | configuração do sistema | não |
| **Arquivo de fundação** | `foundation/` | **conhecimento** | **não** — é *lido* |
| **Skill** | `skills/` | **instrução** | **sim** — você a aciona |

**O teste rápido:** se você diz *"Claude, rode isto"* → é skill.
Se diz *"Claude, leia isto antes de rodar aquilo"* → é fundação.

---

## As 4 demos (ordem recomendada)

| Ordem | Demo | Tempo | Por que nesta ordem |
|---|---|---|---|
| 1º | **Demo 3** — Carregamento seletivo | 7 min | Mais barata. Prova o mecanismo. |
| 2º | **Demo 2** — COM vs. SEM fundação | 10 min | O momento "aha". Se só der tempo de uma, é esta. |
| 3º | **Demo 1** — Construir o Audience Delight | 10 min | Mostra que o arquivo nasce da escuta. |
| 4º | **Demo 4** — Atualizar e propagar | 10 min | Fecha com o efeito composto. |

Total: **37 min** (sobram 3 de folga nos 40 do bloco).

---

## Note bem: as duas skills têm o MESMO Passo 1

Abra `skills/post-linkedin/SKILL.md` e `skills/newsletter-nutricao/SKILL.md`
lado a lado. O bloco "Passo 1 — Carregar Contexto de Fundação" é **idêntico,
palavra por palavra**.

Mesmo assim, uma carrega 2 arquivos e a outra carrega 3.

**A skill não decide. Os headers decidem.** É esse o mecanismo — e é por isso
que um 5º arquivo de fundação, criado amanhã, seria adotado automaticamente
pelas duas skills sem você tocar em nenhuma delas.

---

## ⚠ Aviso

Todo o conteúdo deste pacote é **fictício e didático**. A GiroLeve não existe.
Os comentários de lojistas foram inventados para a aula.

Num uso real, os arquivos de fundação conteriam transcrições de calls, tickets
e dados de clientes — o que torna a conversa sobre **LGPD e dados sensíveis**
(Bloco 6) obrigatória antes de qualquer implementação.
