---
layout: post
title:  "Arch Linux: key “CEB167EFB5722BD6″ could not be looked up remotely"
date:   2018-02-25 15:50:00 -0300
categories: linux
---
Passei um tempo sem atualizar meus pacotes do Arch Linux no meu notebook porque só estava dando boot no Windows 10, lá eu uso uma outra instalação do Arch rodando com o Virtual Box (estou achando melhor do que usar o WSL e dá pra manter mais fácil, tem suporte a snapshots, o sistema de arquivos é mais rápido, funciona também como uma espécie de sandbox…).

Quando eu tentava atualizar um dos pacotes, eis que surge o seguinte erro: key “CEB167EFB5722BD6″ could not be looked up remotely.

Para corrigir, recorri ao [fórum do Antergos](https://forum.antergos.com/topic/8880/key-ceb167efb5722bd6-could-not-be-looked-up-remotely/9), uma distro linux tamém baseada no Arch. Lá eles sugeriram rodar os seguintes comandos:

    sudo pacman -Scc
    sudo pacman -Syy
    sudo pacman -S archlinux-keyring
    sudo pacman-key --init
    sudo pacman-key --populate archlinux
    sudo pacman-key --refresh-keys
    sudo pacman -Syu 

Um desses comandos pergunta se você quer remover do cache todos os pacotes. Veja se você realmente quer fazer isso antes de confirmar.

Como eu uso o Arch puro e não o Antergos, não coloquei as opções referentes a esses repositórios, mas no fórum vocês poderão ter acesso aos comandos origináis.
