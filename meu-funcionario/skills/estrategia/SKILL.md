---
name: estrategia
description: Monta a estrategia de crescimento e de venda dela a partir da meta, e grava em dados/planejamento.js. Use quando ela falar em meta, planejamento, estrategia, quando quiser saber o que postar para vender, ou quando perguntar como chegar a um numero de seguidores ou de clientes.
---

# A estratégia dela

## Antes de qualquer coisa

Leia `dados/negocio.js`, `dados/marca.js`, `dados/instagram.js` (principalmente o `diagnostico`) e
`dados/resultados.js`. Se a pasta `cerebro/` existir, leia também.

Se ela não tiver diagnóstico ainda, rode a skill **diagnostico** antes. Estratégia sem diagnóstico é
palpite bonito.

## A pergunta que vem antes de tudo

Antes de montar qualquer plano, pergunte:

> Quantas horas por semana você tem, de verdade, para cuidar disso?

E acredite na resposta. Um plano que não cabe na semana dela não é um plano, é uma dívida.

## O que fazer

### 1. A meta, uma pergunta por vez

- O que você quer alcançar?
- Qual número diz que você chegou lá?
- Até quando?
- O que muda na sua vida quando isso acontecer?

Espere cada resposta. Se ela responder "crescer no Instagram", não aceite: pergunte crescer para quê,
até chegar num número e numa data.

Se a meta for de seguidor mas o negócio precisa de cliente, diga isso:

> Seguidor não paga conta. Posso montar a meta em cliente e deixar o seguidor como consequência?

### 2. Escreva a estratégia

Em texto corrido, simples, com as palavras dela. Sem palavra de marketing que ela não usa.
Precisa responder: por que esse caminho leva à meta dela, e não outro.

### 3. Monte as ações, separando quem faz

Cada ação com: o que é, **quem faz**, por que isso move a meta, e o prazo.

- `quemFaz: "claude"` para o que você faz sozinho.
- `quemFaz: "voce"` para o que só ela pode fazer: gravar, aparecer, decidir preço, falar com cliente.
- `quemFaz: "juntas"` para o que precisa das duas.

**Seja honesta na divisão.** Se a maior parte depende dela aparecer, diga isso de frente, porque é o
que mais trava aluna.

### 4. Os tipos de post

Para cada tipo: o que é, para que serve na meta dela, e quantos por semana. Some os números e compare
com as horas que ela disse ter. Se não couber, corte você mesma e explique o corte.

### 5. O que trava até ela decidir

Tudo o que depende de uma decisão dela vai em `esperandoVoce`, com a decisão que falta escrita.
Isso aparece na tela Hoje e é o que faz ela destravar.

### 6. Grave

Em `dados/planejamento.js`: `meta`, `estrategia`, `acoes`, `tiposDePost`, `iscas`, `esperandoVoce`.
Datas em `AAAA-MM-DD`. Mantenha o formato `window.DADOS.planejamento = { ... }`.

### 7. Mostre e confirme

Mostre o plano na conversa antes de gravar e pergunte se cabe na semana dela. Depois de gravar,
registre em `dados/dia.js` e mande ela recarregar o sistema.

Termine com:

> Quer que eu já escreva os conteúdos da primeira semana?

## O que nunca fazer

- Nunca monte plano que não cabe nas horas que ela tem.
- Nunca prometa número de seguidor em prazo. Você não controla isso e ela vai cobrar.
- Nunca encha de ação. Três a cinco por semana, bem feitas, valem mais que quinze na lista.
- Nunca deixe uma ação sem dono e sem prazo.
