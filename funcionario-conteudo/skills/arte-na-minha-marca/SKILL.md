---
name: arte-na-minha-marca
description: Gera a arte dos carrosseis e dos posts dela na maquina, na marca dela, a partir dos moldes do plugin. Use quando ela pedir a arte, a capa, os cards, o carrossel pronto, ou quando um conteudo aprovado ainda nao tiver imagem.
---

# A arte, na marca dela

## O que esta skill faz

O plugin traz **moldes genéricos** em `${CLAUDE_PLUGIN_ROOT}/moldes/`. Eles são cinza de propósito.
Na primeira vez, você lê a marca dela e reescreve os moldes com as cores, as fontes e o jeito dela.
Depois disso, toda arte sai pronta, sem ela escolher nada.

A arte é gerada **na máquina dela**, em PNG. Não depende de plano de ferramenta nenhuma.

## Antes de qualquer coisa

Leia `dados/marca.js`. Se estiver vazio, pare e diga:

> Para a arte sair com a sua cara, eu preciso saber as suas cores e as suas fontes. São cinco
> perguntas. Posso?

E preencha a marca primeiro. **Nunca gere arte com cor inventada.**

## A primeira vez: personalizar os moldes

1. Leia os moldes em `${CLAUDE_PLUGIN_ROOT}/moldes/`.
2. Copie para `arte/moldes/` dentro da pasta dela. **Nunca escreva dentro da pasta do plugin**, que
   é apagada quando o plugin atualiza.
3. Troque, nos moldes copiados:
   - as cores pelas de `dados/marca.js`, com o hexadecimal de cada uma, respeitando o campo `onde`
     (fundo, texto, destaque, botão);
   - as fontes pelas de `marca.fontes`. Se ela não tiver o arquivo da fonte, use uma do Google Fonts
     parecida e diga qual você escolheu e por quê;
   - o selo ou logo, se `marca.arquivos` apontar para um.
4. Gere **uma capa de exemplo** e mostre para ela antes de seguir:

   > Ficou assim. Está com a sua cara, ou eu mudo alguma coisa?

   Se ela pedir mudança, mude nos moldes copiados, não só naquela arte.

## Toda vez

1. Pegue em `dados/conteudos.js` os itens com status `aprovado` e sem arquivo de arte.
2. Para cada um, pelo tipo:
   - **carrossel**: um PNG por card, 1080x1350, na ordem. O texto de cada card está na legenda,
     numerado.
   - **estatico**: um PNG 1080x1350.
   - **reel**: a capa em 1080x1920. O vídeo em si é outro assunto: se ela tiver o kit de vídeo
     instalado, chame ele. Se não tiver, diga que a capa está pronta e que o vídeo ela grava.
   - **copy**: não tem arte. Pule.
3. Salve em `arte/<id do conteudo>/`, com nome na ordem: `01.png`, `02.png`.
4. Grave os caminhos no campo `arquivos` daquele item em `dados/conteudos.js`, na ordem.
5. Mande ela recarregar o sistema: a prévia aparece na grade e no carrossel da ficha.

## As regras de arte que valem sempre

- **O texto tem que caber.** Se não couber, diminua o texto, nunca a fonte abaixo do legível.
- **Contraste de verdade.** Texto claro em fundo escuro, ou o contrário. Na dúvida, escureça o fundo.
- Respeite `oQueNaoPode` de `dados/marca.js`. Se lá disser que não pode foto de banco de imagem, não
  use, nem "só dessa vez".
- O primeiro card é o gancho. Se ele não parar o dedo, o resto não é lido.
- Nada de texto no canto de baixo do card: o Instagram cobre com a interface.

## O que nunca fazer

- Nunca invente cor nem fonte. Se não está na marca dela, pergunte.
- Nunca escreva dentro de `${CLAUDE_PLUGIN_ROOT}`.
- Nunca gere arte de conteúdo que ela ainda não aprovou. Trabalho à toa gasta o limite dela.
- Nunca ponha dado de paciente, de processo ou de cliente dentro de uma arte.
