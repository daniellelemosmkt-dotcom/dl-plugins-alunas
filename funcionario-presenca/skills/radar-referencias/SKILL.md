---
name: radar-referencias
description: Duas vezes por semana, olha os perfis de referencia dela, acha os posts que foram muito acima da media daquele perfil (carrossel, foto e video) e escreve uma adaptacao pronta para a marca dela. Use quando ela pedir ideias de referencia, quiser saber o que esta funcionando nos perfis que ela admira, ou quando for dia do radar.
---

# Radar de referências

## Para que serve

Todo perfil tem posts que explodem e posts normais. Esta skill acha os que explodiram, descobre por que funcionaram e traz a versão adaptada para a marca dela.

**O critério não é quem tem mais curtida.** Perfil grande sempre tem número maior. O critério é o post que **fugiu da média daquele perfil**: se o perfil costuma ter 200 curtidas e um post teve 1.500, esse é o achado. Um perfil pequeno com um post 6 vezes acima da média ensina mais do que um perfil gigante com um post comum.

Vale carrossel, foto e vídeo. Não olhe só Reels.

## Antes de qualquer coisa

Leia `dados/negocio.js`, `dados/marca.js`, `dados/planejamento.js` e `dados/instagram.js`. Se a pasta `cerebro/` existir, leia também. Sem saber o que ela vende e como ela fala, a adaptação sai genérica.

Se `negocio.js` ou `marca.js` estiverem vazios, pare e diga:

> Antes de olhar as referências, eu preciso te conhecer, senão a adaptação vai sair genérica. Posso fazer umas perguntas rápidas?

E preencha esses dois primeiro.

## Perguntas, uma por vez

Faça uma pergunta, espere a resposta, e só então faça a próxima.

1. Se ela não tiver perfis de referência salvos, pergunte:

> Me diz até 5 perfis que você admira ou que você olha e pensa "queria fazer assim".

Se ela mandar mais de 5, escolha com ela os 5 mais parecidos com o negócio dela. Explique em uma frase: cada perfil gasta o crédito do mês da ferramenta, e 5 já dão material de sobra.

2. Pergunte:

> Algum desses você quer olhar com mais atenção nesta rodada?

3. Se ela ainda não disse, pergunte quantas horas por semana ela tem para postar. A adaptação precisa caber na semana dela.

## Como ler os perfis

### Caminho 1: com o Apify ligado

O Apify é o conector que deixa o Claude ler o que é público no Instagram, com os números de cada post. Use o ator `apify/instagram-post-scraper`. Ele traz carrossel, foto e vídeo, com curtidas e comentários.

**Limites obrigatórios, sem exceção:**

- No máximo **5 perfis** por rodada.
- No máximo **20 posts por perfil**.

Configure o limite na própria chamada do ator. Diga a ela, numa linha, o motivo: cada post lido gasta um pedaço do crédito do mês, e passar disso pode acabar com o crédito antes do fim do mês.

Nunca rode o mesmo perfil duas vezes na mesma semana. Se a rodada anterior ainda está recente, use o que já foi gravado.

### Caminho 2: sem o Apify

Não peça para ela instalar nada e não trave. Abra cada perfil no navegador, como qualquer pessoa abriria, e leia os últimos posts que aparecem. Entregue menos, e diga isso de frente:

> Sem o Apify eu leio só o que aparece na tela, então olho menos posts por perfil. Os achados são menos precisos, mas ainda servem.

Nesse caminho, se o número de curtidas não aparecer, não invente. Diga que não deu para ver e use outro sinal: quantidade de comentários visível, ou o post estar fixado no topo do perfil.

## Como achar o que fugiu da média

Para cada perfil:

1. Some as curtidas dos posts lidos e tire a média.
2. Separe os posts que tiveram pelo menos **2 vezes a média** daquele perfil. Os que passaram de 3 vezes são os melhores.
3. Comentários pesam mais que curtida. Um post com muito comentário gerou conversa, e conversa vende.
4. Se nenhum post passou de 2 vezes a média, diga: "Neste perfil nada fugiu da média agora". Não force achado.

Fique com os **3 a 5 melhores achados da rodada inteira**, não com tudo.

## O que escrever para cada achado

Em linguagem simples, curto:

- **Quem e qual post**: o perfil, o formato (carrossel, foto ou vídeo) e o link.
- **Quanto foi acima da média**: "teve 4 vezes mais curtida que o normal desse perfil".
- **Por que funcionou**: o gancho (primeira linha ou primeira frase), o formato, a capa, o que a pessoa ganha ao ler.
- **Adaptação para a marca dela**: o que ela posta, com o texto já escrito, no tom de `dados/marca.js`.

A adaptação precisa ser **concreta**: legenda completa, primeira linha, e para carrossel o texto de cada card, numerado. Se for vídeo, o roteiro curto e o gancho falado.

## Como adaptar

- Copie o **mecanismo**, nunca o texto nem a arte. Mecanismo é a ideia por trás: uma lista de erros, um antes e depois, uma pergunta que todo cliente faz.
- Troque o assunto pelo negócio dela e o exemplo pela realidade de quem ela atende.
- Se o mecanismo só funciona porque o perfil de referência tem um posicionamento diferente do dela, diga: "Isso funciona lá por causa de X, e aqui não encaixa". Descarte e explique.
- Use só caso, número e depoimento que ela tenha dado. Nunca invente.

## Onde gravar

**1. Em `dados/conteudos.js`, no campo `itens`.** Acrescente aos que já existem, sem apagar. Mantenha o formato `window.DADOS.conteudos = { ... }`. Cada ideia vira um item com:

- `id`: curto e que não se repita.
- `titulo`: curto, para ela reconhecer na grade.
- `tipo`: `copy`, `estatico`, `carrossel` ou `reel`.
- `data`: em `AAAA-MM-DD`, espalhada na semana. Se ela não escolheu, proponha.
- `legenda`: a legenda inteira, pronta para publicar, no tom dela.
- `porQueEstrategico`: **sempre preenchido.** Diga o que o post faz pela meta dela e de qual perfil veio a ideia, por exemplo: "Traz quem ainda não conhece. O mecanismo deu 4 vezes a média no perfil de [nome]".
- `objetivo`: um só: salvar, comentar, chamar no direct ou clicar no link.
- `paraQuem`: qual público dela.
- `status`: `esperando`.

Se `porQueEstrategico` ficar vazio, a ideia não entra.

**2. Em `dados/planejamento.js`**, acrescente um resumo curto da rodada no campo `estrategia`, sem apagar o que já estava lá: a data, quais perfis foram lidos, o padrão que apareceu. Duas ou três frases.

Depois de gravar, registre em `dados/dia.js` e diga a ela:

> Gravei as ideias. Aperte F5 no painel e abra a tela de Conteúdos para aprovar.

## Como contar para ela

Três coisas, no máximo:

1. O melhor achado da rodada, com o motivo em uma frase.
2. Quantas ideias ficaram esperando aprovação.
3. Um padrão que se repetiu, se houver.

Termine perguntando qual ideia ela quer que você leve primeiro para a arte.

## Quando for rodar de novo

O radar roda **duas vezes por semana**. Não rode mais do que isso sem ela pedir, por causa do crédito. Se ela pedir uma terceira rodada na mesma semana, avise do gasto e confirme antes.

## O que nunca fazer

- Nunca passe de 5 perfis nem de 20 posts por perfil.
- Nunca trate o post com mais curtida como achado. O que vale é o que fugiu da média daquele perfil.
- Nunca copie legenda, texto de card nem arte de outra pessoa.
- Nunca invente número, caso ou depoimento.
- Nunca fale mal de pessoa. Você analisa o post, não a pessoa.
- Nunca grave ideia sem `porQueEstrategico`.
- Nunca encha a grade. Poucas ideias boas valem mais do que muitas fracas.
- Para saúde e advocacia: nunca adapte ideia que prometa cura ou resultado, nem que cite caso de paciente ou de processo.
