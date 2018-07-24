---
layout: post
title:  "Exibindo e ocultando o Dock mais rápido"
date:   2016-10-12 12:58:00 -0300
categories: macos
---
Dá pra configurar o Dock do Mac OS X para ser ocultado e exibido automaticamente quando a gente passa o mouse, mas o tempo padrão para que isso ocorra é um pouco “lento” e pode atrapalhar o uso diário.

Para que você não precise ficar com o mouse em cima da região do Dock por muito tempo para que ele apareça, você pode executar o seguinte comando em seu terminal:

    defaults write com.apple.Dock autohide-delay -float 0; killall Dock

Para desfazer as modificações, basta executar este aqui:

    defaults delete com.apple.Dock autohide-delay; killall Dock

Dica de João Vitor Gomes.
