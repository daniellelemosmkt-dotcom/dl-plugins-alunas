---
name: oportunidades-de-contato
description: Uma vez por dia, le os comentarios dos posts recentes dela, separa quem demonstrou interesse real de quem so elogiou, cria a ficha em dados/leads.js e escreve um modelo de mensagem de direct para ela copiar e mandar. Use quando ela perguntar quem comentou com interesse, quiser achar clientes nos comentarios, ou quando for a checagem do dia.
---

# Oportunidades de contato

## Para que serve

Muitos clientes comentam num post querendo comprar e ninguém responde a tempo. Esta skill lê os comentários dos posts recentes dela, acha quem demonstrou interesse de verdade e deixa a mensagem de direct pronta.

**Quem manda a mensagem é ela. Sempre.** Você nunca manda nada sozinho. Você escreve o modelo, ela lê, ajusta se quiser, copia e envia.

## Antes de qualquer coisa

Leia `dados/negocio.js`, `dados/marca.js`, `dados/instagram.js` e `dados/leads.js`. Do `leads.js`, veja como as fichas já existentes estão escritas e **siga o mesmo formato**, para não quebrar o painel. Veja também quem já está lá, para não criar ficha repetida.

Se `negocio.js` ou `marca.js` estiverem vazios, pare e diga:

> Antes de escrever mensagem para alguém, eu preciso saber como você fala e o que você vende, senão sai com cara de robô. Posso fazer umas perguntas rápidas?

E preencha esses dois primeiro.

## Perguntas, uma por vez

Faça uma pergunta, espere a resposta, e só então faça a próxima. Se ela já respondeu isso antes e está gravado em `dados/`, não pergunte de novo.

1. Pergunte:

> Qual é o seu @ no Instagram?

2. Pergunte:

> Quantos dos seus últimos posts você quer que eu leia? Sugiro os 5 mais recentes.

3. Se ainda não estiver claro em `dados/negocio.js`, pergunte:

> Quando alguém te chama no direct querendo comprar, o que você costuma responder primeiro?

Essa resposta é a base do tom das mensagens.

## Como ler os comentários

### Caminho 1: com o Apify ligado

O Apify é o conector que deixa o Claude ler o que é público no Instagram. Para os comentários, use:

- `apidojo/instagram-comments-scraper`: **prefira este**, é bem mais barato.
- `apify/instagram-comment-scraper`: use só se o primeiro falhar ou vier incompleto.

**Limites para não gastar o crédito do mês:**

- No máximo **5 posts** por rodada, os mais recentes.
- No máximo **100 comentários por post**.
- Rode **uma vez por dia**, não mais. Guarde na cabeça (e em `dados/dia.js`) a data da última rodada. Comentário que já foi analisado não entra de novo.

Diga a ela, numa linha, o motivo: cada comentário lido gasta um pedaço do crédito do mês.

### Caminho 2: sem o Apify

Não peça para ela instalar e não trave. Abra os posts recentes no navegador e leia os comentários que aparecem na tela. Diga:

> Sem o Apify eu leio só os comentários que aparecem na tela, então posso perder alguns. Ainda assim dá para achar quem tem interesse.

## Como separar interesse de elogio

**Interesse real** é quando a pessoa:

- pergunta preço ou valor ("quanto custa?", "qual o valor?");
- demonstra vontade de comprar ("quero", "eu quero uma", "como faço para comprar?");
- pergunta como funciona ou como contratar ("como faço?", "você atende em [cidade]?", "tem na cor X?");
- tem uma dúvida específica sobre o produto ou o serviço (tamanho, prazo, entrega, aroma, horário);
- pede para ser chamada, ou marca uma amiga dizendo que quer isso para as duas.

**Elogio** é "lindo", "amei", "parabéns", emoji de coração, "perfeito". Elogio é bom para a marca, mas não é oportunidade de contato. Não crie ficha para elogio puro.

Em dúvida, pergunte a si mesmo: se eu respondesse isso por mensagem, a pessoa teria algo a ganhar? Se sim, é interesse. Se não, é elogio.

Ignore: o comentário da própria dona do perfil, perfis que parecem robô ou spam, e quem já virou lead em `dados/leads.js`.

## A mensagem de direct

Escreva uma mensagem para cada oportunidade. Ela só vai copiar e enviar, então precisa estar pronta.

### Regras da mensagem

1. **Cite o que a pessoa comentou, com as palavras dela, em poucas palavras.** Exemplo: "Vi que você perguntou o valor da camiseta de linho no post de ontem". Isso mostra que é uma conversa de verdade, não uma mensagem em massa.
2. **Responda a dúvida primeiro.** Se ela perguntou preço, a mensagem traz o preço (se estiver em `dados/negocio.js`) ou diz que vai passar. Não responda uma pergunta com outra pergunta.
3. **Primeira linha sem venda.** A abordagem de venda não pode aparecer na primeira linha. Comece pela conversa: um agradecimento curto, ou a resposta da dúvida.
4. **Curta.** No máximo 4 ou 5 linhas. Quem lê no celular não lê parágrafo grande.
5. **No tom dela.** Releia `dados/marca.js`. Se ela é descontraída, a mensagem é descontraída. Se é mais séria, também. Nada de "Prezada cliente".
6. **Termine com uma pergunta fácil** que convide a pessoa a continuar, por exemplo sobre o tamanho, a cor ou o prazo.
7. **Sem cara de robô.** Nada de "Olá! Tudo bem? Somos a empresa X e temos o prazer de oferecer...". Nada de lista de benefícios. Nada de três emojis em fila. Escreva como a própria dona escreveria para uma pessoa só.

### Nunca inventar o que a pessoa disse

Só cite o que está **de fato escrito** no comentário. Se o comentário diz "quanto custa?", você não pode escrever "vi que você está procurando um presente". Se você não sabe o motivo da pessoa, não finja que sabe.

Se o comentário for curto ou vago, a mensagem também fica simples:

> Oi, [nome]! Vi seu comentário no post de [assunto]. Posso te ajudar com o valor? Qual tamanho você está pensando?

### Dois exemplos do tom certo

Comentário: "quanto é a camiseta?"

> Oi, Ana! Vi que você perguntou o valor da camiseta no post de hoje. A básica de algodão está R$ 79. Qual tamanho você usa? Já te digo o que tenho em estoque.

Comentário: "queria saber se atende em Campinas"

> Oi, Marcos! Vi sua pergunta sobre Campinas. Atendo sim, por videochamada ou presencial. Você prefere qual?

Os valores e as respostas acima são só para mostrar o tom. Use sempre os dados reais de `dados/negocio.js`. Se uma informação não estiver lá, não invente: deixe a mensagem sem ela ou marque com `[CONFIRMAR]` e avise a aluna.

## Onde gravar

Em `dados/leads.js`, crie **uma ficha por oportunidade**, na coluna `novo`, **seguindo o formato das fichas que já existem no arquivo**. Cada ficha precisa de:

- o nome ou o @ da pessoa;
- `origem`: `"Instagram"`;
- a coluna: `novo`;
- o que ela comentou, **copiado como está** e o post em que foi;
- a data do comentário;
- a mensagem de direct pronta, para ela copiar;
- uma observação curta, se ajudar (por exemplo: "perguntou preço").

Não apague nem mexa nas fichas que já estavam lá. Mantenha o formato do arquivo.

Depois de gravar, registre em `dados/dia.js` a data e quantos comentários foram lidos, e diga a ela:

> Gravei as fichas. Aperte F5 no painel e abra a tela de Leads. As mensagens estão prontas para você copiar.

## Como contar para ela

Curto:

1. Quantos comentários você leu e quantas oportunidades achou.
2. As oportunidades, da mais quente para a mais fria, uma linha cada. A mais quente é quem perguntou preço ou disse "quero".
3. Lembre: **a mensagem é dela para mandar**. Você não enviou nada.

Se não achou nenhuma oportunidade, diga isso de frente. Não force ficha para parecer que trabalhou.

Termine perguntando se ela quer ajustar o tom de alguma mensagem antes de mandar.

## O que nunca fazer

- Nunca mande mensagem sozinho. Quem envia é ela, sempre.
- Nunca crie ficha para elogio puro.
- Nunca escreva abordagem de venda na primeira linha.
- Nunca escreva mensagem com cara de robô, de mensagem em massa ou de lista de benefícios.
- Nunca invente que a pessoa disse algo que ela não disse, nem suponha o motivo dela.
- Nunca invente preço, prazo, estoque ou condição. Use `dados/negocio.js` ou marque `[CONFIRMAR]`.
- Nunca crie ficha repetida para a mesma pessoa e o mesmo comentário.
- Nunca passe de 5 posts nem de 100 comentários por post, nem rode mais de uma vez por dia.
- Para saúde e advocacia: nunca cite diagnóstico, tratamento, processo ou qualquer dado sensível que a pessoa tenha comentado. A mensagem convida para conversar, sem repetir o problema dela em público ou por escrito.
