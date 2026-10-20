---
name: relatorio-semanal
description: Monta o relatorio da semana com os posts que funcionaram melhor e o que fazer na semana seguinte. Use quando ela pedir relatorio, resultado da semana, o que funcionou, quais posts foram melhor, ou quando a rotina semanal disparar.
---

# O relatório da semana

## O que esta skill faz

Nenhuma ferramenta entrega "os posts que funcionaram melhor" pronto. O Metricool dá os números do
período. **Quem monta o ranking e escreve a leitura é você.**

Rode **uma vez por semana**. Mais que isso gasta o limite dela à toa, e ninguém muda estratégia todo
dia.

## Antes de qualquer coisa

Leia `dados/conteudos.js`, `dados/instagram.js`, `dados/planejamento.js` e `dados/negocio.js`.
Confira se o Metricool está ligado.

## O que fazer

### 1. Pegue os números do período

Para cada post publicado nos últimos sete dias: alcance, curtidas, comentários, salvamentos e
compartilhamentos.

Se o Metricool não devolver alguma métrica, trabalhe com as que vieram e diga quais faltaram.

### 2. Monte o ranking de verdade

Não ordene por curtida. Curtida é a métrica mais fácil e a que menos diz.

Ordene pelo que importa para a meta dela, em `dados/planejamento.js`:

- Meta de **crescer**: compartilhamento e alcance de quem não segue.
- Meta de **vender**: comentário, mensagem no direct e clique no link.
- Meta de **autoridade**: salvamento.

Diga em uma frase por qual critério você ordenou, e por quê.

### 3. Ache o padrão, não o campeão

O post que foi melhor importa menos que **o que ele tem e os outros não têm**. Compare:

- Formato: carrossel, Reels, estático.
- Assunto.
- O gancho da capa.
- O dia e a hora.
- O objetivo que estava escrito em `objetivo`.

Se três posts bons tiverem a mesma coisa em comum, é padrão. Se for um só, pode ser sorte, e diga que
pode ser sorte.

### 4. Olhe também o que foi mal

É onde está o aprendizado. Pelo menos um item sobre isso, sem drama.

### 5. Escreva o relatório

Guarde em `dados/instagram.js`, no campo `diagnostico`, atualizando `emUmaFrase` e `oQueFazerAgora`
com o que a semana mostrou. Mantenha no máximo três coisas para fazer.

Na conversa, escreva assim, curto:

- **A frase da semana:** o que aconteceu, em uma linha.
- **Os três melhores:** cada um com o número que importa e o que ele tinha de diferente.
- **O padrão:** o que repetir.
- **O que não funcionou:** e o que você acha que foi.
- **Para a semana que vem:** no máximo três coisas, na ordem.

### 6. Ofereça o próximo passo

> Quer que eu já escreva os conteúdos da semana que vem usando esse padrão?

Se ela disser sim, chame a skill **conteudo-da-semana** e leve o padrão junto.

### 7. Registre

Acrescente em `dados/dia.js`, campo `oQueOFuncionarioFez`.

## O que nunca fazer

- Nunca invente número. O que não veio, não veio.
- Nunca diga que foi uma boa semana se não foi.
- Nunca compare a conta dela com conta de outro tamanho. Compare com ela mesma na semana anterior.
- Nunca entregue relatório sem dizer o que fazer na semana seguinte. Número sem decisão não serve.
