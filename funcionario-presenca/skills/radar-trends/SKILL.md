---
name: radar-trends
description: Duas vezes por semana, procura no Instagram e no TikTok o que esta crescendo nas palavras do nicho dela e traz so o que combina com a marca, ja adaptado. Use quando ela perguntar o que esta em alta, quiser ideia de trend, ou quando for dia do radar.
---

# Radar de trends

## Para que serve

Trend é o que está crescendo agora: um formato, um áudio, um assunto, uma hashtag. Esta skill procura nas palavras do nicho dela e traz **só o que ela consegue adaptar**, com o conteúdo já escrito.

**A regra de ouro é o juízo.** Trend que não combina com a marca não entra. Quando você achar uma trend famosa que não combina, diga isso a ela em vez de empurrar:

> Essa trend está bombando, mas não combina com a sua marca porque [motivo em uma frase]. Deixei de fora.

Seguir trend errada faz a marca perder o jeito dela. Prefira uma trend que encaixa a cinco que forçam.

## Antes de qualquer coisa

Leia `dados/negocio.js`, `dados/marca.js`, `dados/planejamento.js` e `dados/instagram.js`. Se a pasta `cerebro/` existir, leia também. Preste atenção em `palavrasQueNuncaUso` e no tom. Sem isso você não sabe o que combina.

Se `negocio.js` ou `marca.js` estiverem vazios, pare e diga:

> Antes de procurar trend, eu preciso te conhecer, senão eu não sei o que combina com você. Posso fazer umas perguntas rápidas?

E preencha esses dois primeiro.

## Perguntas, uma por vez

Faça uma pergunta, espere a resposta, e só então faça a próxima.

1. Pergunte:

> Me diz 3 ou 4 palavras que descrevem o seu assunto. As palavras que o seu cliente digitaria para te achar.

Exemplos para ela entender: "camiseta estampada", "consultoria de imagem", "perfume importado", "aula na faculdade". Se ela der mais de 4, escolha com ela as 4 mais fortes. Se der palavra vaga demais, como "moda", ajude a deixar mais específica.

2. Pergunte:

> Você topa aparecer em vídeo, ou prefere posts de imagem e carrossel?

A resposta decide quais trends servem. Trend de dancinha não adianta para quem não grava vídeo.

3. Pergunte:

> Tem alguma trend ou assunto que você não quer de jeito nenhum?

Anote a resposta em `dados/marca.js` ou no `CLAUDE.md` da pasta, para não repetir.

## Como procurar

### Caminho 1: com o Apify ligado

O Apify é o conector que deixa o Claude ler o que é público nas redes. Use estes quatro:

- Instagram: `apify/instagram-hashtag-scraper` (posts que usam a palavra como hashtag) e `apify/instagram-search-scraper` (o que aparece quando alguém busca a palavra).
- TikTok: `clockworks/tiktok-scraper` (vídeos por palavra) e `khadinakbar/tiktok-trending-hashtags-scraper` (o que está subindo no momento).

**Limites obrigatórios por rodada, sem exceção:**

- No máximo **4 palavras**.
- No máximo **30 resultados por palavra** em cada ator.
- No máximo **4 chamadas de ator** na rodada inteira. Comece pelo Instagram e use o TikTok só se ela grava vídeo ou se o Instagram trouxe pouco.

**Desligue os extras caros.** No ator de TikTok, deixe desligados: baixar o vídeo, transcrever o vídeo e ler os comentários. Diga a ela, em uma linha:

> Deixei desligado o que baixa vídeo, transcreve e lê comentário, porque isso come o crédito do mês rápido e não muda o resultado.

Se ela quiser ligar algum desses, avise do gasto e peça a confirmação antes.

### Caminho 2: sem o Apify

Não peça para ela instalar e não trave. Procure pelas mesmas palavras no navegador, na busca do Instagram e do TikTok, como qualquer pessoa faria. Leia só o que aparece na tela e entregue menos. Diga:

> Sem o Apify eu olho só o que aparece na tela, então trago menos coisa. Ainda dá para achar boas ideias.

Se o número de visualizações ou curtidas não aparecer, não invente.

## Como separar o que entra

Para cada trend encontrada, faça três testes:

1. **Está crescendo de verdade?** Vários posts recentes, de perfis diferentes, com número acima do normal. Um post só não é trend.
2. **Combina com a marca?** Confira o tom, o público e `palavrasQueNuncaUso`. Se não combina, descarte e conte.
3. **Ela consegue fazer?** Cabe nas horas dela, no formato que ela topa e com o que ela tem em mãos. Se pede equipamento ou pessoa que ela não tem, descarte.

Fique com **2 a 4 trends** por rodada. Se só uma passar nos três testes, entregue uma. Se nenhuma passar, diga isso de frente, sem inventar para preencher.

## O que escrever para cada trend

Em linguagem simples:

- **O que é**: em uma ou duas frases, como se explicasse para uma amiga. Sem jargão.
- **Onde está crescendo**: Instagram ou TikTok, e o sinal que você viu.
- **Por que combina com a marca dela**: uma frase.
- **A adaptação pronta**: o conteúdo escrito, no tom de `dados/marca.js`. Legenda inteira, primeira linha forte e, se for carrossel, o texto de cada card numerado. Se for vídeo, o roteiro curto e o gancho falado.
- **Quanto tempo a trend dura**: se é coisa de dias ou de semanas. Se for de dias, o conteúdo precisa ir ao ar logo, e a data proposta deve refletir isso.

Copie o **mecanismo**, nunca texto nem vídeo de outra pessoa. Use só caso, número e depoimento que ela tenha dado.

## Onde gravar

**1. Em `dados/conteudos.js`, no campo `itens`.** Acrescente aos que já existem, sem apagar. Mantenha o formato `window.DADOS.conteudos = { ... }`. Cada adaptação vira um item com:

- `id`: curto e que não se repita.
- `titulo`: curto, para ela reconhecer na grade.
- `tipo`: `copy`, `estatico`, `carrossel` ou `reel`.
- `data`: em `AAAA-MM-DD`. Trend de poucos dias vai para os próximos dias, não para daqui a duas semanas.
- `legenda`: a legenda inteira, pronta para publicar, no tom dela.
- `porQueEstrategico`: **sempre preenchido.** Diga o que o post faz pela meta dela e qual trend ele aproveita, por exemplo: "Aproveita o formato [nome] que está crescendo no Instagram e atrai quem ainda não conhece a loja".
- `objetivo`: um só: salvar, comentar, chamar no direct ou clicar no link.
- `paraQuem`: qual público dela.
- `status`: `esperando`.

Sem `porQueEstrategico`, a ideia não entra.

**2. Em `dados/planejamento.js`**, acrescente um resumo curto da rodada no campo `estrategia`, sem apagar o que já estava lá: a data, as palavras usadas, o que entrou e o que foi descartado. Duas ou três frases.

Depois de gravar, registre em `dados/dia.js` e diga a ela:

> Gravei as ideias. Aperte F5 no painel e abra a tela de Conteúdos para aprovar.

## Como contar para ela

1. As trends que entraram, uma linha cada, com o motivo.
2. As que ficaram de fora e por quê. Isso mostra que você tem critério e evita que ela ache que você não viu.
3. Qual delas é mais urgente.

Termine perguntando qual ela quer que você leve primeiro para a arte.

## Quando for rodar de novo

O radar roda **duas vezes por semana**. Não rode mais do que isso sem ela pedir, por causa do crédito. Se ela pedir uma terceira rodada na mesma semana, avise do gasto e confirme antes.

## O que nunca fazer

- Nunca passe dos limites de palavras, resultados e chamadas.
- Nunca ligue download, transcrição de vídeo ou leitura de comentários no ator de TikTok sem ela confirmar o gasto.
- Nunca empurre trend que não combina com a marca. Descarte e explique.
- Nunca chame de trend o que um post só fez.
- Nunca copie texto, áudio narrado nem vídeo de outra pessoa.
- Nunca invente número, caso ou depoimento.
- Nunca grave ideia sem `porQueEstrategico`.
- Para saúde e advocacia: nunca adapte trend que prometa cura ou resultado, nem que use caso de paciente ou de processo. Trend de humor com paciente ou cliente fica de fora.
