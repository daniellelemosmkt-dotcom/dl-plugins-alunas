---
name: calendario-do-mes
description: Monta o calendario de conteudo do mes inteiro dela, com feed, Reels e stories, a partir da meta e das referencias, e grava em dados/conteudos.js e dados/planejamento.js. Use quando ela pedir calendario, planejamento do mes, pauta do mes, ou quando perguntar o que postar nas proximas semanas.
---

# O calendário do mês dela

## O que esta skill faz

A skill `conteudo-da-semana` escreve os posts de uma semana. Esta aqui vem antes: ela desenha o mês
inteiro, decide o que cada semana precisa fazer pela meta, e só então distribui as peças nos dias.

Quem faz o mês não decide post a post. Decide o caminho, e os posts caem dentro dele.

## Antes de qualquer coisa

Leia, nesta ordem:

1. `dados/negocio.js`, para saber o que ela vende e para quem.
2. `dados/marca.js`, para escrever no tom dela.
3. `dados/planejamento.js`, para a meta e o prazo.
4. `dados/instagram.js`, principalmente o `diagnostico` e os posts que já foram melhor.
5. `dados/conteudos.js`, para não repetir o que já está na fila.
6. A pasta `cerebro/`, se existir.

Se não houver meta em `planejamento.js`, pare e rode a skill **estrategia** antes. Calendário sem
meta é lista de tarefa bonita.

Se ela ainda não vende nada, não force produto. Pergunte:

> Hoje você quer que as pessoas te conheçam, te procurem, ou comprem alguma coisa?

E monte o mês para a resposta que ela der. Quem ainda não vende tem meta de ser procurada, e isso é
uma meta legítima.

## As três perguntas, uma por vez

> Quantos dias por semana você consegue postar, de verdade?

Acredite na resposta e nunca proponha mais do que isso. Um calendário que não cabe na semana dela
vira culpa, não conteúdo.

> Tem alguma data, lançamento, viagem ou evento neste mês que eu preciso respeitar?

> Tem algum assunto que você está cansada de falar, ou algum que você quer falar e nunca fala?

## O que fazer

### 1. Escreva a lógica do mês antes das peças

Em até 8 linhas, no campo `estrategia` de `dados/planejamento.js`, responda:

- Onde o perfil dela está hoje, em uma frase.
- O que precisa acontecer neste mês para a meta andar.
- O que cada semana vai fazer. Dê um trabalho a cada semana, por exemplo: semana 1 fazer ela ser
  entendida, semana 2 provar que funciona, semana 3 quebrar a objeção que mais aparece, semana 4
  convidar.

Mostre essa lógica para ela e espere o aceite antes de escrever qualquer post:

> Este é o caminho do mês. Faz sentido para você, ou eu mudo alguma coisa antes de eu escrever os
> posts?

### 2. Distribua os formatos

Use os `tiposDePost` de `dados/planejamento.js` quando existirem. Se não existirem, vale esta
divisão, que é a que funciona hoje:

- **Reels**: o que leva pessoas novas até ela. É o formato que mais alcança quem ainda não a segue.
  Pelo menos metade das peças do mês.
- **Carrossel e post de foto**: o que transforma quem chegou em quem segue e confia. Aqui entram
  método, bastidor, prova e antes e depois.
- **Stories**: o que faz quem já segue comprar. Entra no calendário como roteiro curto do dia, não
  como peça pronta.

Cada semana precisa ter pelo menos um conteúdo que fale do que ela vende. Mês sem oferta não vende,
e mês só de oferta cansa.

### 3. Use o que o radar trouxe

Se as skills `radar-referencias` e `radar-trends` já tiverem rodado, leia o que elas deixaram em
`dados/conteudos.js` e aproveite as ideias que combinam com a lógica do mês.

Use como ferramenta, nunca como regra. Trend que não tem a ver com ela fica de fora, e você diz
isso em uma linha em vez de empurrar.

### 4. Escreva as peças

Para cada peça, grave em `dados/conteudos.js`, com status `esperando`:

- `titulo`: como ela reconhece aquele post na grade.
- `tipo`: `reel`, `carrossel`, `estatico` ou `copy`.
- `data`: o dia em que vai ao ar, no formato AAAA-MM-DD, respeitando os dias que ela disse.
- `legenda`: a legenda inteira, escrita no tom dela, pronta para copiar.
- `porQueEstrategico`: **obrigatório**. O que aquele post faz pela meta. Sem isso, não entra.
- `objetivo`: alcançar, aproximar ou vender.

Para Reels, escreva também o roteiro falado dentro da legenda, separado por "ROTEIRO:", com o
gancho da primeira frase. Para stories, uma peça do tipo `copy` por dia de story, com a sequência
em tópicos.

### 5. Mostre o mês e pare

Mostre a lista agrupada por semana, uma linha por peça: dia, formato, título, objetivo.

Pergunte:

> Aprovo tudo, ou você quer trocar alguma coisa antes?

E diga para ela apertar F5 no painel e ver o mês na tela "Conteúdos para aprovar". O que ela aprovar
ali é o que vira arte e agendamento depois.

## As regras que não se quebram

- **Todo conteúdo chega com o motivo de existir.** Sem `porQueEstrategico`, a peça não entra.
- **Nunca invente número, prova ou cliente.** Se a peça precisa de um resultado para funcionar,
  pergunte a ela qual resultado usar.
- **Nunca prometa o que ela não entrega.** Se a legenda diz que tem material, o material tem que
  existir.
- **Um mês cabe na vida dela.** Na dúvida entre mais peças e peças melhores, escolha melhores.
- **Nada é publicado aqui.** Esta skill escreve e põe para aprovar. Quem agenda é a skill `agendar`,
  depois do sim dela.
