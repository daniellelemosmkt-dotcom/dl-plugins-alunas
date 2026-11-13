---
name: editar-video
description: Edita o video falado dela do bruto ao Reels pronto: transcreve, corta erro e silencio, legenda, poe manchete, som e trilha, e entrega o arquivo para postar. Use quando ela mandar um video gravado, pedir para cortar, legendar, editar o Reels, por manchete ou trilha.
---

# O vídeo dela, do bruto ao Reels

## O que esta skill faz

Ela edita vídeo falado conversando. A aluna grava no celular, manda o arquivo, e você corta, legenda,
escreve as manchetes, põe som e entrega o arquivo pronto para postar.

Você faz o trabalho pesado. Ela decide.

## Antes de qualquer coisa

Leia `dados/marca.js`, para as cores e as fontes, e `dados/negocio.js`, para saber do que ela fala.
Se a pasta `cerebro/` existir, leia também.

Confira o kit, com estes dois comandos:

```
ffmpeg -version
```

```
python -c "import faster_whisper; print('ok')"
```

Se faltar o ffmpeg, instale com `winget install ffmpeg` e peça para ela fechar e abrir o terminal.
Se faltar o Whisper, instale com `pip install faster-whisper`. Avise que a primeira transcrição baixa
o modelo e demora alguns minutos.

**Trabalhe sempre numa pasta local**, dentro de `Documentos`, nunca dentro do Google Drive. Vídeo no
Drive trava a máquina. No fim, só o arquivo pronto volta para onde ela quiser.

## 1. Olhe o bruto antes de prometer

```
ffprobe -v error -show_entries format=duration,size -show_entries stream=width,height,r_frame_rate -of default=noprint_wrappers=1 bruto.mp4
```

Diga a ela a duração, o tamanho da tela e se está em pé ou deitado. Reels é em pé, 1080x1920. Se ela
gravou deitado, avise agora, não no fim.

## 2. Transcreva, com o tempo de cada palavra

Rode o Whisper no áudio, em português, com tempo por palavra. Use o modelo `small` para ir rápido, ou
`medium` quando a gravação tiver ruído ou nomes difíceis.

Guarde dois arquivos: a transcrição corrida, que se lê como texto, e os tempos de cada palavra.

**Leia a transcrição inteira antes de cortar qualquer coisa.** É lendo que você descobre onde ela se
perdeu, onde repetiu e onde a ideia realmente começa.

O Whisper erra nome próprio e palavra técnica. Corrija na legenda o que você tiver certeza, e
pergunte a ela o que não entender.

## 3. Proponha o que sai, e espere o sim

Monte a lista do que entra e do que sai, com a minutagem e a frase de cada pedaço, e mostre para ela
antes de cortar.

**O que sai sempre:**
- O silêncio longo, acima de meio segundo, dentro da fala.
- O começo falso e a frase abandonada no meio.
- A repetição: quando ela falou a mesma frase duas vezes, fica a última, que costuma ser a melhor.
- O "corta" falado. **"Corta" é instrução, não palavra para legendar.** Tudo que vem antes dele, até
  o começo daquela tentativa, sai. A tomada refeita entra.
- A corrente de muletas, quando vêm três ou quatro seguidas. Um "né" solto é ritmo, e fica.

**O que nunca sai:**
- Respiro curto dentro da frase. Sem ele a fala fica robótica.
- A frase de ligação. Se depois do corte o vídeo pula de assunto, você cortou uma ponte, não uma
  repetição.
- Conteúdo bom só para caber em 30 segundos. O vídeo tem o tamanho que o assunto pede.

**Onde a tesoura encosta:** depois que a palavra termina de soar e antes da próxima começar. Cortar
em cima do ataque da palavra seguinte deixa um estalo que parece palavra mastigada.

## 4. Corte

Para cada pedaço que fica, gere um arquivo:

```
ffmpeg -y -ss 00:00:12.40 -to 00:00:31.80 -i bruto.mp4 -c:v libx264 -crf 18 -preset fast -c:a aac -b:a 192k p01.mp4
```

Depois junte todos:

```
ffmpeg -y -f concat -safe 0 -i lista.txt -c copy editado.mp4
```

onde `lista.txt` tem uma linha por pedaço, na ordem:

```
file 'p01.mp4'
file 'p02.mp4'
```

**Cubra cada emenda.** Corte seco entre dois trechos da mesma pessoa falando aparece. Não resolva com
transição de dissolver, que sobrepõe o rosto dela em cima dela mesma e fica estranho. Resolva
aproximando a imagem num dos lados da emenda, uns 12%:

```
ffmpeg -y -i p02.mp4 -vf "scale=iw*1.12:ih*1.12,crop=1080:1920" -c:a copy p02z.mp4
```

Um tamanho por pedaço. Nunca fique pulsando entre perto e longe.

## 5. Legenda

Gere a legenda a partir do **áudio já cortado**, nunca do bruto. A cada corte, a legenda do bruto
atrasa, e no fim ela aparece depois da fala.

Rode o Whisper de novo, agora no `editado.mp4`, e salve em `.srt`. Depois queime:

```
ffmpeg -y -i editado.mp4 -vf "subtitles=legenda.srt:force_style='FontName=Poppins,FontSize=18,PrimaryColour=&HFFFFFF&,OutlineColour=&H000000&,Outline=2,Alignment=2,MarginV=260'" -c:a copy com_legenda.mp4
```

Regras da legenda:
- Escreve o que ela falou, não o que você acha que ela quis dizer.
- Nunca em cima do rosto, e nunca na faixa de baixo onde o Instagram põe os botões. A margem de 260
  resolve na maioria dos casos: confira num print.
- Blocos curtos, de duas ou três palavras, e nunca uma palavra sozinha na quebra.

## 6. As manchetes

Manchete não é a legenda em letra maior. **Manchete é a ideia do trecho**, escrita curta, para quem
está vendo sem som entender.

Como achar as suas:
1. Escreva o argumento do vídeo em quatro ou cinco pontos: o gancho, o problema, a virada, o ganho e
   a chamada.
2. Para cada ponto, ache no que ela falou a frase mais próxima, e encurte com as palavras dela.
3. Faça dois testes. **O teste do mudo:** lendo só as manchetes, de cima a baixo, dá para entender o
   vídeo? **O teste do card:** aquela frase funcionaria sozinha num post?

Não vira manchete: exemplo, analogia, lista de detalhe, frase de ligação, nem o que o vídeo já está
mostrando na tela.

Para pôr na tela:

```
ffmpeg -y -i com_legenda.mp4 -vf "drawtext=fontfile='C\:/Windows/Fonts/poppins-bold.ttf':text='A frase da manchete':fontcolor=white:fontsize=64:borderw=3:bordercolor=black:x=(w-text_w)/2:y=420:enable='between(t,3.2,7.0)'" -c:a copy com_manchete.mp4
```

- A manchete entra na palavra em que o assunto aparece na fala, e sai quando a ideia acaba.
- Nunca em cima do rosto. Nada abaixo de três quartos da altura, que é onde a interface do Reels come.
- Frase comprida quebra em duas linhas. Nunca encolha a letra até virar formiga.

## 7. O som

**Efeito sonoro.** Todo acontecimento na tela pede um som, e nenhum som existe sem acontecimento.
Um som de cada vez, nunca dois no mesmo instante.

**O nível é medido, não é no ouvido.** Meça a voz e o som:

```
ffmpeg -i com_manchete.mp4 -af volumedetect -f null -
```

O efeito fica por volta de **12 dB abaixo da voz**. A trilha fica por volta de **18 dB abaixo**.
Nesse nível a música é presença, não concorrência. Se ela disser que a trilha atrapalha, o problema
quase nunca é volume: é a faixa errada. Troque a faixa antes de mexer no volume.

Para juntar a trilha:

```
ffmpeg -y -i com_manchete.mp4 -i trilha.mp3 -filter_complex "[1:a]volume=-18dB,afade=t=out:st=55:d=3[m];[0:a][m]amix=inputs=2:duration=first:dropout_transition=0" -c:v copy -c:a aac -b:a 192k com_trilha.mp4
```

**Onde achar som sem dor de cabeça:** Pixabay e Freesound, filtrando por CC0. Os dois permitem uso
comercial e não exigem que ela escreva crédito na legenda. Banco que exige crédito fica de fora,
porque ninguém quer uma linha de crédito no meio da legenda. Música de artista conhecido não entra no
arquivo: essa entra pelo áudio do próprio Instagram, na hora de postar.

## 8. Quando falta imagem

Primeiro procure o material real dela: print, foto, gravação de tela, o produto na mão. **Tudo na tela
precisa ser verdade.** Ilustração genérica e tela inventada estragam a confiança.

Se não existe e não dá para gravar, aí sim vale uma imagem gerada. Descreva a cena com as cores da
marca dela, mostre a descrição antes de gerar, e gere uma vez.

Para pôr por cima do vídeo, um pedaço curto, de um ou dois segundos:

```
ffmpeg -y -i com_trilha.mp4 -i foto.jpg -filter_complex "[1:v]scale=1080:-1[ov];[0:v][ov]overlay=0:(H-h)/2:enable='between(t,10,12)'" -c:a copy com_broll.mp4
```

## 9. A capa

A capa é um quadro do próprio vídeo. Procure um em que ela esteja olhando para a câmera, com a **boca
fechada**, e com expressão boa.

```
ffmpeg -y -ss 00:00:04.20 -i com_broll.mp4 -frames:v 1 -q:v 2 capa.jpg
```

Mostre três ou quatro opções e deixe ela escolher. Lembre que na grade do perfil a capa aparece
cortada em três por quatro: confira que o rosto e o título não ficam fora desse recorte.

## 10. A entrega

```
ffmpeg -y -i com_broll.mp4 -c:v libx264 -preset slow -b:v 6000k -maxrate 7000k -bufsize 12000k -pix_fmt yuv420p -c:a aac -b:a 192k -movflags +faststart REELS.mp4
```

Entregue na pasta do vídeo: o bruto, o `REELS.mp4`, a `capa.jpg` e a legenda do post num arquivo de
texto. Nada de rascunho na mesma pasta.

Grave o conteúdo em `dados/conteudos.js`, com o caminho do vídeo e da capa, status `esperando`, para
ela aprovar na tela. Depois do sim dela, a skill `agendar` publica.

## As regras que não se quebram

- **Nunca acelere a voz dela** para o vídeo caber num tempo. Encurtar é cortar, não correr.
- **Nunca invente** fala, número, print ou cena que não existe.
- **Nada parado.** Se passarem mais de dez segundos sem nada acontecer na tela, entra uma manchete,
  uma aproximação ou uma imagem.
- **Nada publicado sem o sim dela.** Você entrega o arquivo e a capa. Quem posta é ela.
- Mostre a lista de cortes antes de cortar, e a lista de manchetes antes de desenhar. É muito mais
  rápido ela corrigir uma lista do que um vídeo pronto.
