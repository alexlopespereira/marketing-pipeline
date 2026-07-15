# ROTEIRO DAS DEMOS — Guia do Professor

> Bloco 5 da aula. **40 minutos.** Quatro demos.
> Tudo o que você precisa está neste arquivo. Prompts prontos para colar.

---

## ANTES DA AULA (faça na véspera — 10 minutos)

```bash
cd aula-marketing-claude-code
claude
```

Rode a **Demo 3** inteira (é a mais rápida). Se ela funcionar, todas funcionam.

**Checklist de tela:**
- [ ] Fonte do terminal em tamanho grande (mínimo 18pt). A turma senta longe.
- [ ] Aba do Claude.ai já aberta, com `plano-b/` pronto para colar.
- [ ] `foundation/` aberta num editor ao lado, para mostrar os arquivos.

**Uma frase para dizer antes de começar:**
> "Tudo aqui é fictício. Numa empresa real, esses arquivos teriam dados de
> clientes — e aí a conversa sobre LGPD que vamos ter no Bloco 6 fica séria."

---

## DEMO 3 — Carregamento seletivo  ⏱ 7 min
### *(Rode esta PRIMEIRO. É a mais barata e prova o mecanismo.)*

**Objetivo:** tornar visível o roteamento automático. A turma precisa VER a IA
decidindo sozinha.

**O que mostrar na tela antes:** abra `foundation/` e mostre os 4 arquivos.
Role até o header de um deles. Diga: *"só isso aqui vai ser lido agora."*

**Prompt (cole no Claude Code):**

```
Escaneie ./foundation/ e leia SOMENTE os headers (tudo acima do primeiro ---).
Não leia o conteúdo dos arquivos.

Para cada uma destas tarefas, diga quais arquivos você carregaria e por quê:
(1) escrever um post de LinkedIn;
(2) escrever a mensagem de lançamento de um recurso novo;
(3) escrever um e-mail para quem travou no onboarding.

Explique cada decisão em uma linha.
```

**Resultado esperado:**
| Tarefa | Carrega |
|---|---|
| Post de LinkedIn | Audience Delight + Creator Style |
| Mensagem de lançamento | Market Positioning + Customer Journey **+ Creator Style** ⚠ |
| E-mail de quem travou | Customer Journey + Audience Delight + Creator Style |

> ⚠ A linha do meio diverge do slide de propósito. Leia a caixa abaixo **antes**
> de rodar — essa divergência é a melhor aula do bloco, não um erro.

**A fala que fecha a demo:**
> "Ninguém programou isso. Eu não disse à IA qual arquivo usar. Ela leu as
> etiquetas e decidiu. É esse o mecanismo inteiro."

---

### ⚠ LEIA ANTES DE RODAR — a divergência da tarefa (2)

O artigo do Kieran diz que uma **mensagem de lançamento** carrega
*Market Positioning + Customer Journey* (2 arquivos). Mas a IA provavelmente
vai carregar **3** — incluindo o Creator Style, porque o header dele diz
"produz palavras", e uma mensagem de lançamento obviamente produz palavras.

**Isso não é um bug. É a melhor aula do bloco.** Não esconda — provoque:

> "O artigo diz 2 arquivos. A máquina carregou 3. Quem está errado?"

**A resposta:** ninguém. O artigo simplificou para ilustrar o conceito. Na
prática, quase todo conteúdo que produz texto vai puxar o Creator Style — e
está certo que puxe: você não quer uma mensagem de lançamento fora da voz da
marca.

**A lição real:** o header é um contrato que **você** escreve. Se você quiser
que o Creator Style fique de fora de tarefas de posicionamento, é o header dele
que precisa mudar — não a skill. Mostre isso na tela:

```
Abra ./foundation/creator-style.md e leia o header.
Ele diz "produz palavras". Uma mensagem de lançamento produz palavras.
Por isso ele carregou.

Se eu quisesse excluí-lo, eu editaria O HEADER — não a skill.
```

Feche assim:
> "É por isso que a inteligência mora nos arquivos. Vocês acabaram de ver: para
> mudar o comportamento de todas as skills, eu mexo em uma linha de um header."

**Se der errado de verdade:** se a IA carregar os 4 arquivos em tudo, algum
header está vago demais. Abra, mostre, e use a seu favor — é exatamente o
Erro nº 1 do método (headers que nunca dizem "não").

---

## DEMO 2 — Post COM vs. SEM fundação  ⏱ 10 min
### *(O momento "aha" da aula. Se só der tempo de uma, é esta.)*

**Objetivo:** contraste genérico vs. peer, lado a lado.

### Rodada 1 — SEM fundação

**Prompt:**

```
Ignore completamente a pasta ./foundation/. Não leia nenhum arquivo dela.

Escreva um post de LinkedIn para a GiroLeve, um SaaS de gestão financeira
para e-commerce, sobre o tema: fechar o caixa no fim do mês.
```

**O que vai sair (mais ou menos):** *"Otimize sua gestão financeira e potencialize
os resultados do seu e-commerce..."* — corporativês puro.

**Pause aqui.** Pergunte à turma: *"de que empresa é esse post?"*
A resposta certa é: **de qualquer uma.** É esse o ponto.

### Rodada 2 — COM fundação

**Prompt:**

```
Use a skill de post-linkedin (./skills/post-linkedin/SKILL.md).
Siga o Passo 1 dela: carregue os arquivos de fundação apropriados.

Tema: fechar o caixa no fim do mês.
```

**O que vai sair:** *"Você vendeu R$ 80 mil esse mês. E não sobrou nada."* —
vocabulário real, frase curta, tensão na primeira linha.

**A fala que fecha:**
> "Mesmo modelo. Mesmo pedido. Mesma empresa. A única coisa que mudou foi o
> contexto que ele leu antes de escrever."

---

## DEMO 1 — Construir um Audience Delight  ⏱ 10 min

**Objetivo:** mostrar que o arquivo não nasce da sua cabeça — nasce da escuta.

**Prompt (cole no Claude Code):**

```
Leia ./material-bruto/comentarios-lojistas.md

Você é um ETNÓGRAFO, não um copywriter. Registre a linguagem que já existe
no material — nunca a melhore, traduza ou polia.

ANTES DE ESCREVER, faça esta triagem (não me mostre este passo):
1. Separe o que foi dito pela AUDIÊNCIA do que foi dito por vendedores,
   suporte ou pela marca. Só a fala do CLIENTE conta.
2. Marque as passagens com CARGA EMOCIONAL — é ali que mora o vocabulário
   verdadeiro.

Agora produza um Audience Delight Profile em markdown, com:
- Header "Load this file when" / "Do NOT load"
- Uma tabela VOCABULÁRIO REAL com no mínimo 8 pares (Ela diz | Ela NÃO diz)
- O que a faz brilhar
- Do que ela reclama quando a marca não está na sala
- EVIDÊNCIA: cite o verbatim que sustenta cada item
- Marque [INFERÊNCIA] tudo que você deduziu sem base direta

NUNCA invente vocabulário que não esteja no material.
```

**Resultado esperado:** a IA vai extrair "no muque", "planilha virou uma zona",
"a taxa que come", "tô voando às cegas", "vivo apagando incêndio".

**A fala que fecha:**
> "Repare: eu não escrevi nenhuma dessas expressões. Elas estavam nos
> comentários. O trabalho não foi criar — foi escutar."

**Momento de ouro, se acontecer:** se a IA marcar algo como `[INFERÊNCIA]`,
pare e aponte. *"Olhem: ela está dizendo o que NÃO tem base. É esse o freio
de mão contra alucinação."*

---

## DEMO 4 — Atualizar e propagar  ⏱ 10 min
### *(A prova do efeito composto. Precisa das DUAS skills.)*

**Objetivo:** mudar UM arquivo e ver o ganho aparecer em DUAS skills.

### Passo 1 — Estabeleça a linha de base

**Prompt:**

```
Use a skill de post-linkedin. Tema: por que vender bem não significa lucrar.
```

Guarde o resultado na tela. **Não feche.**

### Passo 2 — Atualize UM arquivo

**Prompt:**

```
Abra ./foundation/audience-delight-profile.md

Adicione à seção "Do que ela reclama quando a nossa marca NÃO está na sala"
esta nova dor, com as palavras dela:

- "O frete grátis me sangra. Mas se eu tirar, ninguém compra."

Salve o arquivo.
```

### Passo 3 — Rode DUAS skills diferentes

**Prompt:**

```
Agora rode DUAS skills, uma depois da outra:

1. A skill de post-linkedin. Tema: por que vender bem não significa lucrar.
2. A skill de newsletter-nutricao. Público: lojista que travou no stall point
   nº 1 (importou os dados, mas não confia nos números).

Em cada uma, declare quais arquivos de fundação você carregou.
```

**Resultado esperado:** as duas peças — de skills diferentes, com combinações
diferentes de arquivos — passam a refletir a dor do frete. **Você editou um
arquivo. Melhorou dois canais.**

**A fala que fecha a aula:**
> "Eu não melhorei uma skill. Melhorei a fundação. E o ganho desceu sozinho
> para tudo que lê aquele arquivo. É isso que o Catmull fez na Pixar."

---

## SE TUDO FALHAR — Plano B

Abra `plano-b/COMO-USAR.md` e siga. Você reproduz as quatro demos no Claude.ai,
colando os arquivos no chat. O conceito é idêntico; só o carregamento vira manual.

**Não peça desculpas pela falha técnica.** Diga:
> "Vou fazer no navegador — e vocês vão ver que o conceito não depende do
> terminal. Depende dos arquivos."
