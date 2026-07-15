---
name: skill-repurposer-humanizado
description: Transforma uma peça longa (Hub) em múltiplos formatos por plataforma e, na mesma passada, remove marcas de voz robótica de IA e injeta o tom da marca. Use quando o squad tiver um Hub aprovado e precisar dos Spokes (thread, carrosséis/Reels, e-mail) prontos e humanizados. Adapta Content Repurposer + Humanizer / Anti-AI Detection do repositório superamped/ai-marketing-skills.
etapa: 3
---

# Skill: Repurposer Humanizado (Spokes & Anti-AI Tells)

> Adaptação em português de **Content Repurposer** e **Humanizer / Anti-AI Detection**
> de [superamped/ai-marketing-skills](https://github.com/superamped/ai-marketing-skills).
> A Content Repurposer usa templates comprovados e adaptação por plataforma;
> a Humanizer caça o vocabulário robótico. Aqui as duas rodam em sequência, na mesma skill.

## Passo 1 — Carregar Contexto de Fundação

Escaneie `./foundation/`, leia só os headers e carregue os que casam.

> Roteamento típico: **Audience Delight Profile** + **Creator Style** (ambos geram texto).
> A humanização depende inteiramente da seção COMPARAÇÃO do Creator Style. Se ele não
> carregar, **pare** — sem ele você não tem contra o que testar.

## Passo 2 — Receber o Hub aprovado

Confirme que recebeu o **Hub já revisado por humano** (Etapa 2) e a **hook escolhida**.
Se receber um rascunho não aprovado, avise: repurpose de material não curado propaga erro.

## Passo 3 — REPURPOSE por plataforma (a Camada 1)

Produza os Spokes abaixo. Cada plataforma tem regra própria — não use o mesmo texto colado:

- **1 thread (X ou LinkedIn):** 6 a 9 posts. O 1º é a hook escolhida. Um argumento por post.
  Sem "🧵" nem "abre thread". Último post é uma afirmação, não "curtiu? compartilha".
- **2 carrosséis OU roteiros de Reels (Instagram/TikTok):** para carrossel, 1 ideia por slide,
  slide 1 = hook, slide final = 1 ação concreta. Para Reels, roteiro em falas orais de 20 a 40s
  com deixa visual por bloco.
- **1 e-mail de engajamento:** assunto (≤ 6 palavras) + preview + corpo curto. Uma ideia, um clique.

Regras transversais:
- Cada Spoke carrega **uma** ideia do Hub — não o Hub inteiro comprimido.
- Nada de hashtag, emoji ou CTA que o Creator Style não comprove que a marca usa.

## Passo 4 — HUMANIZAR (a Camada 2 — o "Teste do Taste")

Passe CADA Spoke por esta caça. Entregue o antes e o depois.

**4.1 — Cace e remova o vocabulário clássico de IA.** Lista de banimento (amplie com o time):
`mergulhe / mergulhar fundo`, `revolucionário`, `no cenário atual`, `no mundo de hoje`,
`desvende / desbloqueie`, `eleve / eleve o nível`, `game-changer / divisor de águas`,
`nada mais é do que`, `não se trata apenas de… mas de…`, `imagine só`, `é importante notar que`,
`em um mundo cada vez mais`, `potencializar`, `robusto`, `sinergia`, `de forma perfeita/impecável`,
`transformador`, `aproveite ao máximo`, `fique ligado`. Para cada ocorrência: **corte ou troque**
pela palavra que a marca realmente usaria (coluna "Ela diz" do Audience Delight Profile).

**4.2 — Quebre o paralelismo sintático.** IA adora três frases com a mesma cadência
("Faça X. Faça Y. Faça Z."). Reescreva pelo menos uma para ter comprimento e forma diferentes.
Se três frases seguidas têm a mesma estrutura, **isso é uma marca de IA** — quebre.

**4.3 — Injete o tom opinativo.** O material genérico é neutro. Adicione a **opinião** da marca:
uma tomada de posição, um contra-exemplo, uma frase que só esta marca assinaria. Puxe do Hub.

**4.4 — Rode o teste da COMPARAÇÃO.** Para cada Spoke, aponte a frase de maior risco de soar
como a coluna "NÃO soa como a marca" e mostre a versão corrigida.

## Passo 5 — Entregar (formato ANTES / DEPOIS obrigatório)

Para cada Spoke, nesta ordem:

1. **Plataforma e template usado.**
2. **ANTES (output bruto)** — o repurpose da Camada 1, sem humanizar.
3. **DEPOIS (humanizado)** — o texto final.
4. **Log de humanização** — lista curta do que mudou:
   - termos de IA removidos (com o que entrou no lugar);
   - paralelismos quebrados;
   - opinião injetada;
   - a frase de maior risco e por que a versão final está segura.

No fim, uma **tabela-resumo** de todos os termos de IA encontrados em todos os Spokes.

## O que NUNCA fazer

- Não entregue só o "depois". O valor pedagógico e editorial está no **antes/depois** lado a lado.
- Não "humanize" trocando um termo de IA por outro termo de IA (não troque "mergulhe" por "desvende").
- Não invente prova nova ao humanizar. Humanizar é sobre **voz**, não sobre inventar fatos.
- Não deixe os 4 formatos com a mesma cara. Se a thread e o e-mail dizem a mesma coisa com as
  mesmas palavras, o repurpose falhou — cada plataforma pede um recorte diferente do Hub.
