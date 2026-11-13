---
description: Prepara o computador para editar video: instala o ffmpeg, o Python e o transcritor, cria a pasta de trabalho e confere tudo.
---

Você vai preparar esta máquina para editar vídeo. Quem está do outro lado nunca instalou nada e não
sabe o que é terminal. Conduza você, um passo de cada vez, explicando em português simples, sem termo
técnico, e pare na hora em que der erro.

Escreva sempre em português do Brasil. Nunca use "pra", nunca "a gente", nunca travessão.

## Antes de começar, avise

Diga, em três linhas:

> Vou instalar três coisas aqui na sua máquina. O **ffmpeg**, que é quem corta e monta o vídeo. O
> **Python**, que é o idioma em que o transcritor foi escrito. E o **transcritor**, que escuta o seu
> vídeo e escreve o que você falou.
>
> Pode aparecer uma caixa pedindo permissão. É normal, é eu te perguntando se posso rodar. Aceite.
>
> Tudo isso fica no seu computador, e os seus vídeos não saem daqui.

## 1. O ffmpeg

Rode `ffmpeg -version`.

Se responder com uma versão, diga que já está instalado e siga.

Se não responder, instale com `winget install Gyan.FFmpeg`. Avise que pode aparecer uma janela azul
do Windows pedindo confirmação, e que é só clicar em Sim.

Se o `winget` não for reconhecido, pare e diga:

> O instalador do Windows nesta máquina está desatualizado. Abra a Microsoft Store, procure por
> "Instalador de Aplicativo" e atualize. Depois é só me chamar de novo.

## 2. O Python

Rode `python --version`.

Se responder com uma versão 3.9 ou maior, siga.

Se não responder, instale com `winget install Python.Python.3.12`.

Se falhar, diga para instalar pela Microsoft Store, procurando por "Python 3.12", e depois chamar
você de novo.

## 3. O transcritor

Rode `pip install faster-whisper`.

Avise antes que isso demora uns dois minutos e escreve muita linha na tela, e que isso é normal.

Se o `pip` não for reconhecido, é porque o Python não entrou. Volte ao passo 2.

## 4. Confira

Rode os três de novo: `ffmpeg -version`, `python --version` e `pip show faster-whisper`.

Se algum não responder, diga qual faltou e o que fazer. **Se o ffmpeg tiver acabado de ser
instalado**, avise que é preciso fechar o Claude Code e abrir de novo, porque o computador só enxerga
o programa novo na próxima abertura.

## 5. A pasta de trabalho

Crie a pasta `meus videos` dentro de Documentos, se ela não existir, e diga o caminho completo.

Explique em uma linha por que o trabalho é feito ali e não dentro do Google Drive: vídeo é arquivo
pesado, e o Drive fica sincronizando o tempo todo, o que deixa a máquina lenta.

## 6. Feche

Diga, em três linhas, o que ficou instalado e para que serve cada coisa, e termine assim:

> Está tudo pronto. Agora é só pôr um vídeo dentro da pasta e me dizer o que você quer fazer com ele.
> Se quiser começar do começo, me peça para transcrever.
