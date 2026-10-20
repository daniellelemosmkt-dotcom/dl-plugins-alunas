# Plugins do Meu Funcionário

Os plugins das alunas do Modo Automático, da DL Estúdio.
Eles escrevem nos arquivos `dados/` do sistema Meu Funcionário, então a tela enche sozinha.

## Como a aluna instala

Ela não digita comando. Na Biblioteca, cada plugin tem um pedido pronto para copiar e colar na aba
Code. O Claude dela faz o resto: instala, liga o conector e avisa quando precisar do login dela.

O endereço do marketplace é este repositório.

## O que tem aqui

| plugin | o que faz | telas que ele enche |
|---|---|---|
| `funcionario-presenca` | Lê o Instagram, olha as concorrentes, escreve o diagnóstico e monta a estratégia | Minhas redes, Meu Instagram, Meu planejamento |
| `funcionario-conteudo` | Escreve os conteúdos da semana na marca dela, gera a arte, agenda o aprovado e traz o relatório | Conteúdos para aprovar, Meu Instagram |

## As regras que valem em todos

1. **Uma pergunta por vez.** Quem conduz é o plugin, não a aluna.
2. **Escrever no lugar dela.** Nunca deixar campo em branco.
3. **Nunca inventar.** Número que não veio fica vazio.
4. **Nunca gravar chave, senha ou token** em arquivo nenhum.
5. **Agendado, nunca publicado na hora.** Ela tem que poder cancelar antes de ir ao ar.
6. **Registrar o que fez** em `dados/dia.js`, para ela conferir.

## Conectores que vêm junto

Os dois trazem o Metricool, em `https://ai.metricool.com/mcp`. A aluna só faz o login uma vez.

## Para quem for mexer

Os moldes de arte ficam em `funcionario-conteudo/moldes/`, de propósito em cinza. Quem personaliza é
o Claude da aluna, na primeira vez, lendo `dados/marca.js`. Nunca escreva dentro da pasta do plugin
na máquina dela: ela é apagada a cada atualização.
