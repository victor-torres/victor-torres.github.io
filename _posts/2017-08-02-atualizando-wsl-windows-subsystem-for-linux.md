---
layout: post
title:  "Atualizando WSL – Windows Subsystem for Linux"
date:   2017-08-02 21:10:00 -0300
categories: windows
comments: true
---
Verifique em que versão você está agora:

    $ lsb_release -d
    Description:    Ubuntu 14.04.5 LTS

Atualize para a versão mais nova com o comando:

    $ sudo -S RELEASE_UPGRADER_NO_SCREEN=1 do-release-upgrade

Você vai precisar de sua senha de administrador. Não esqueça da flag RELEASE_UPGRADER_NO_SCREEN, caso contrário terá um erro de screen terminated. A partir daí é só seguir as instruções.


# ATUALIZAÇÃO

Você pode ter problemas com o sudo, dizendo que não há tty disponível etc. Basta criar um alias como solução temporária (ou não rsrs):

    alias sudo='sudo -S'

Pode adicionar no seu .bashrc ou .zshrc
