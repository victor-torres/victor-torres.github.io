---
layout: post
title:  "pbcopy e pbpaste do macOS no Linux"
date:   2018-02-26 12:00:00 -0300
categories: linux
comments: true
---
Tem dois comandos muito legais no macOS que servem pra copiar e colar texto a partir de terminais do sistema. São muito úteis para fazer scripts de automatização. Eu também uso eles pra integrar a área de transferência do tmux com a do sistema operacional.

Equivalentes ao CTRL + C

    echo "me copia" | pbcopy

    cat arquivo.txt | pbcopy

Equivalentes ao CTRL + V

    pbpaste

    pbpaste > arquivo.txt

Como no Linux não tem pbcopy nem pbpaste, a gente pode usar o xclip (ou outras opções baseadas no servidor de janelas X) para fazer as mesmas tarefas. Mas como eu gosto de manter a compatibilidade dos meus scripts (e a forma de usar o pbcopy e o pbpaste é muito mais fácil), preferi fazer alguns scripts de atalho:

pbcopy.sh

    xclip -selection clipboard

pbpaste.sh

    xclip -o -selection clipboard

Depois eu copiei (você também pode fazer um link simbólico) esses arquivos para o /usr/local/bin:

    sudo cp pbcopy.sh /usr/local/bin/pbcopy
    sudo cp pbpaste.sh /usr/local/bin/pbpaste

E dei permissão de execução:

    sudo chmod +x /usr/local/bin/pbcopy
    sudo chmod +x /usr/local/bin/pbpaste

Pronto. Você tem algo muito semelhante ao que temos funcionando no macOS. Espero que essa dica facilite sua vida. Depois eu publico sobre como usar esse comando para facilitar com que a cópia de texto do tmux vá para a área de transferência do seu sistema operacional.
