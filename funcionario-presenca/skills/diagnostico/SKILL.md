---
name: diagnostico
description: Escreve o diagnostico honesto do perfil de Instagram dela e grava em dados/instagram.js. Use quando ela pedir um diagnostico, uma analise do perfil, perguntar o que esta errado no Instagram dela, por que nao cresce, ou o que ela deveria mudar.
---

# O diagnóstico do perfil dela

## Antes de qualquer coisa

Leia, nesta ordem: `dados/negocio.js`, `dados/marca.js`, `dados/instagram.js`,
`dados/planejamento.js`. Se a pasta `cerebro/` existir, leia também.

Se `dados/instagram.js` estiver vazio ou com mais de sete dias, rode antes a skill **ler-instagram**.
Diagnóstico com dado velho é chute.

## A regra deste diagnóstico

**Seja honesta com ela.** Ela pagou para ouvir a verdade, não elogio. Se a bio não diz o que ela faz,
escreva isso com todas as letras. Se ela posta bonito e ninguém salva, diga.

E ao mesmo tempo: **nada de lista de 15 problemas.** Isso paralisa. No máximo três coisas para fazer
agora, na ordem.

## O que fazer

### 1. Olhe o perfil como quem chega nele pela primeira vez

Pergunte a si mesma, olhando só a bio, a foto e os três primeiros posts:

- Em cinco segundos dá para saber **o que ela faz** e **para quem**?
- Tem um motivo para seguir, ou é só bonito?
- O link leva para onde? Resolve alguma coisa?

### 2. Olhe os números, se tiver

- Os posts que foram melhor têm o que em comum?
- A frequência é regular ou aos trancos?
- Ela cresce, está parada ou cai?

Se não tiver número, diga que o diagnóstico é só do que dá para ver na tela, e siga.

### 3. Escreva o diagnóstico

Em `dados/instagram.js`, no campo `diagnostico`:

- `emUmaFrase`: a coisa mais importante, dita sem rodeio. É o que ela vai ler primeiro.
- `oQueEstaBom`: o que já funciona. Procure de verdade, sempre tem.
- `oQueEstaAtrapalhando`: o que trava o crescimento, ligado ao negócio dela.
- `oQueFazerAgora`: **no máximo três**, na ordem de fazer. Cada uma começando com um verbo.
- `atualizadoEm`: a data de hoje, no formato `AAAA-MM-DD`.

Cada item em uma frase. Nada de parágrafo.

### 4. Mostre antes de gravar

Escreva o diagnóstico na conversa e pergunte:

> É isso que você vê também, ou eu entendi errado alguma coisa?

Se ela corrigir, ajuste e grave. Se ela concordar, grave.

### 5. Registre e avise

Acrescente a linha em `dados/dia.js`, campo `oQueOFuncionarioFez`. Depois diga para ela recarregar o
sistema e ver na tela Meu Instagram.

Termine oferecendo o próximo passo:

> Quer que eu monte a estratégia para resolver a primeira dessas três?

## O que nunca fazer

- Nunca suavize para agradar. Um diagnóstico educado e falso não ajuda ninguém.
- Nunca use palavra de marketing que ela não usa. Nada de engajamento, alcance orgânico, autoridade,
  entregar valor, posicionamento, se essas palavras não estão na marca dela.
- Nunca mande ela "postar mais". Isso não é diagnóstico.
- Nunca mais de três coisas para fazer.
