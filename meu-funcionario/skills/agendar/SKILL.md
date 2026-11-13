---
name: agendar
description: Agenda no Metricool os conteudos que ela aprovou, e atualiza dados/conteudos.js. Use quando ela disser que aprovou, que ja marcou na tela, que quer agendar, publicar ou por na fila os conteudos.
---

# Agendar o que ela aprovou

## A regra que não se quebra

**Agendado, nunca publicado na hora.** Tudo entra na fila com data e hora, e ela pode cancelar antes
de ir ao ar. Mesmo que ela peça para publicar agora, ofereça agendar para daqui a uma hora:

> Eu prefiro deixar agendado para daqui uma hora, assim você consegue cancelar se ver algo errado.
> Quer assim, ou publico agora mesmo?

Só publique na hora se ela disser que sim depois dessa pergunta.

## Antes de qualquer coisa

1. Veja se o conector do **Metricool** está ligado. Se não estiver, pare e diga:

   > Preciso que você ligue o Metricool uma vez. Configurações, Personalização, Conectores, aba
   > Descobrir, pesquise Metricool e clique em Conectar. Me avise quando terminar.

2. Leia `dados/conteudos.js` e `dados/planejamento.js`.

## O que fazer

### 1. Junte o que está aprovado

Pegue os itens com status `aprovado`. Se não houver nenhum, diga assim:

> Nenhum conteúdo está marcado como "quero usar" ainda. Abre a tela Conteúdos para aprovar e me
> chama quando terminar de decidir.

Se ela tiver marcado na tela mas não estiver gravado, pergunte item por item o que ela decidiu e
grave antes.

### 2. Confira antes de mandar

Para cada um, confira e só então agende:

- Tem legenda?
- Se é carrossel, estático ou Reels, tem arquivo de arte? Se não tiver, rode a skill
  **arte-na-minha-marca** antes.
- A data já passou? Se passou, pergunte a nova data.

### 3. Escolha o horário

Peça ao Metricool o **melhor horário** para a conta dela e use. Se ele não devolver, use o horário
que já estiver no `planejamento.js`. Se não houver nenhum, pergunte a ela.

Não agende dois conteúdos no mesmo horário. Espalhe.

### 4. Mostre a fila antes de agendar

Liste na conversa: o quê, que dia, que hora, para qual rede. Depois pergunte:

> Pode mandar essa fila para o Metricool?

Espere ela responder. **Nunca agende sem esse sim.**

### 5. Agende

Crie o agendamento no Metricool. Para cada um que entrar:

- Mude o status para `publicado` em `dados/conteudos.js` só quando ele de fato for ao ar. Enquanto
  está na fila, deixe `aprovado` e anote a data e a hora agendadas na legenda do item, no fim, assim:
  `[agendado para AAAA-MM-DD HH:MM]`.
- Registre em `dados/dia.js`, campo `oQueOFuncionarioFez`.

### 6. O limite do plano dela

O plano de graça do Metricool dá **20 agendamentos por mês**. Antes de mandar a fila, conte quantos
já foram no mês. Se a fila passar do teto, avise antes:

> Isso vai passar do limite do plano de graça do Metricool, que é 20 por mês. Posso agendar os
> primeiros e deixar o resto para o mês que vem, ou você prefere subir de plano?

Não deixe ela descobrir o limite quando o post não for ao ar.

### 7. Conte a ela

Quantos entraram, quando o primeiro vai ao ar, e o que ficou de fora e por quê.

## O que nunca fazer

- Nunca publique sem ela confirmar.
- Nunca agende conteúdo sem legenda ou sem arte.
- Nunca agende no perfil errado. Se ela cuidar de mais de um, pergunte qual antes.
- Nunca apague agendamento que já existe sem perguntar.
