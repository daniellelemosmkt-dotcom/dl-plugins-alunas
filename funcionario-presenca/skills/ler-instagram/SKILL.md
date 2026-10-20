---
name: ler-instagram
description: Le o perfil de Instagram da pessoa e as metricas da conta dela, e grava em dados/instagram.js e dados/redes.js do Meu Funcionario. Use quando ela pedir para ler o Instagram dela, atualizar o perfil, ver quantos seguidores tem, puxar as metricas, ou quando outra skill precisar do perfil atualizado e ele estiver vazio ou velho.
---

# Ler o Instagram dela

## Antes de qualquer coisa

1. Confira se você está na pasta do **Meu Funcionário**, aquela com `index.html` e a pasta `dados/`.
   Se não estiver, pergunte onde ela está e espere a resposta.
2. Leia `dados/negocio.js` e `dados/marca.js`. Se a pasta `cerebro/` existir, leia também.
   Sem isso você não sabe para quem ela fala.
3. Veja se o conector do **Metricool** está ligado. Se não estiver, pare e diga assim:

   > Preciso que você ligue o Metricool uma vez. Vá em Configurações, Personalização, Conectores,
   > aba Descobrir, pesquise Metricool e clique em Conectar. Me avise quando terminar.

   Não tente contornar. Sem ele você não tem as métricas dela.

## O jeito de falar com ela

Ela não é técnica. Uma pergunta por vez, curta, em português simples, e espere a resposta antes da
próxima. Nunca use palavra técnica sem explicar na mesma frase. Nunca use travessão, nunca escreva
"pra", nunca escreva "a gente".

## O que fazer

### 1. Descubra qual é o perfil

Se `dados/redes.js` já tiver o Instagram dela, use esse. Se não tiver, pergunte o @ dela e espere.

### 2. Puxe o que dá pelo Metricool

Pegue, para a conta dela: seguidores, seguindo, número de publicações, alcance do período, os posts
recentes com curtidas, comentários e alcance de cada um, e o melhor horário de publicar.

Se o Metricool não devolver alguma coisa, não invente. Deixe o campo como está e anote para contar a
ela no fim.

### 3. Complete o que falta perguntando

A bio, o link e os destaques você pede a ela, porque é mais rápido do que caçar:

> Me manda a sua bio exatamente como ela está, com as quebras de linha.

Depois:

> Quais são os seus destaques, na ordem em que aparecem no perfil?

Uma pergunta por vez.

### 4. Grave

Escreva em `dados/instagram.js`, respeitando os campos que já estão no arquivo:
`perfil`, `destaques`, `grade`, `crescimento`.

Regras de gravação que não se quebram:

- **Em `crescimento`, acrescente um ponto novo.** Nunca apague os anteriores: é o histórico dela.
  Se já existir um ponto com a data de hoje, troque só esse.
- Datas sempre no formato `AAAA-MM-DD`.
- Números sempre como número, sem ponto e sem texto.
- Mantenha o formato `window.DADOS.instagram = { ... }`.
- Atualize `dados/redes.js` também, com os seguidores e a bio.

### 5. Registre o que você fez

Acrescente uma linha em `dados/dia.js`, no campo `oQueOFuncionarioFez`, com a data, a hora e o que
você atualizou.

### 6. Conte a ela

Em três frases, no máximo: o que você atualizou, o que mudou desde a última leitura e o que não
conseguiu pegar. Depois diga para ela recarregar a página do sistema.

Se o crescimento tiver dois pontos ou mais, diga quantos seguidores ela ganhou ou perdeu no período,
com o número.

## O que nunca fazer

- Nunca invente número. Se não veio, fica vazio.
- Nunca escreva senha, chave ou token em arquivo nenhum.
- Nunca apague o histórico de `crescimento`.
- Nunca diga que ela cresceu se o número caiu. Fale a verdade, com a mesma calma.
