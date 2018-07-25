---
layout: post
title:  "Liberando espaço em disco removendo Cache do Apple Bird"
date:   2015-09-30 09:59:00 -0300
categories: macos
comments: true
---
Mais uma dica para quem tem Mac com disco pequeno e está com pouco espaço disponível.

Existe uma pasta de cache no diretório do usuário chamada com.apple.bird, que por vezes adquire o tamanho aproximado de 10GB ou até mais! Ela armazena dados dos serviços na nuvem da Apple e aparentemente não há contra indicações para sua remoção periódica.

Para ver o tamanho que essa pasta ocupa em seu disco execute o comando no terminal:

    du -h -s ~/Library/Caches/com.apple.bird/

Para remover a pasta execute (precisará da senha de administrador):

    sudo rm -R ~/Library/Caches/com.apple.bird/
