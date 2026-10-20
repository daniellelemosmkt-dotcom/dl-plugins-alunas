---
name: conteudo-da-semana
description: Escreve os conteudos da semana dela, cada um com o motivo de existir, e grava em dados/conteudos.js para ela aprovar na tela. Use quando ela pedir conteudo, post, legenda, carrossel, Reels, pauta da semana, ou quando perguntar o que postar.
---

# Os conteúdos da semana dela

## Antes de qualquer coisa

Leia, nesta ordem:

1. `dados/negocio.js`, para saber o que ela vende e para quem.
2. `dados/marca.js`, para escrever **no tom dela, não no seu**.
3. `dados/planejamento.js`, para saber a meta e os tipos de post combinados.
4. `dados/instagram.js`, para ver o que já foi melhor.
5. A pasta `cerebro/`, se existir.

Se `negocio.js` ou `marca.js` estiverem vazios, pare e diga:

> Antes de escrever, eu preciso te conhecer, senão vai sair genérico. São dez minutos. Posso
> perguntar agora?

E preencha esses dois primeiro.

## A regra que não se quebra

**Todo conteúdo chega com o motivo de existir escrito.** Se você não souber dizer o que aquele post
faz pela meta dela, ele não entra na grade. Sem exceção.

## O que fazer

### 1. Duas perguntas, uma por vez

> Quantos conteúdos você quer para esta semana?

Depois:

> Tem alguma data, lançamento ou assunto que não pode faltar?

Se ela não souber quantos, olhe `tiposDePost` em `dados/planejamento.js` e proponha o número de lá.

### 2. Escreva cada conteúdo

Para cada um:

- **titulo**: curto, para ela reconhecer na grade. Não é o título do post.
- **tipo**: `copy`, `estatico`, `carrossel` ou `reel`.
- **data**: quando vai ao ar, em `AAAA-MM-DD`. Espalhe na semana, não jogue tudo num dia.
- **legenda**: a legenda inteira, pronta para publicar. No tom dela.
- **porQueEstrategico**: o que esse conteúdo faz pela meta. Ligue com a meta de verdade, não com
  frase solta.
- **objetivo**: o que ela quer que a pessoa faça depois de ver. Um só: salvar, comentar, chamar no
  direct, clicar no link.
- **paraQuem**: qual público dela.
- **status**: `esperando`.
- **id**: curto e que não se repita.

Se for carrossel, escreva o texto de cada card dentro da legenda, numerado, para a skill de arte
usar depois.

### 3. Varie de propósito

Numa semana tem que ter conteúdo que **atrai quem não conhece**, conteúdo que **aproxima quem já
segue** e conteúdo que **vende**. Se der tudo igual, você errou. Diga a ela qual é qual.

### 4. Grave

Em `dados/conteudos.js`, no campo `itens`. Acrescente aos que já existem, não apague os antigos.
Mantenha o formato `window.DADOS.conteudos = { ... }`.

### 5. Avise

Diga quantos você escreveu, como eles se dividem (atrair, aproximar, vender) e mande ela abrir a tela
**Conteúdos para aprovar** e decidir. Lembre que ela clica em cada um para ler a legenda inteira.

Termine com:

> Depois que você marcar, me chama que eu gero as artes e agendo o que você aprovou.

## Quando ela recusar um conteúdo

Pergunte o motivo, anote em `oQueEuAchei` daquele item, e **reescreva levando o motivo em conta**.
Se o mesmo motivo aparecer duas vezes, vire regra: acrescente ao `CLAUDE.md` da pasta, para não
repetir nunca mais.

## O que nunca fazer

- Nunca escreva no seu tom. O tom é o de `dados/marca.js`.
- Nunca use palavra que está em `palavrasQueNuncaUso`.
- Nunca invente caso de cliente, número ou depoimento. Se precisar de um exemplo real, pergunte a ela.
- Nunca ponha conteúdo sem `porQueEstrategico` e sem `objetivo`.
- Nunca prometa resultado que ela não pode cumprir.
- Para saúde e advocacia: nunca prometa cura nem resultado, nunca cite caso de paciente ou de
  processo, nem disfarçado.
