---
layout: post
title:  "Rolagem de tela natural e tradicional no Mac OS X"
date:   2015-07-19 13:26:00 -0300
categories: macos
comments: true
---
![MacBook gestures](/assets/images/2015-07-19-macbook-gestures.png)

O Mac OS X permite que seja configurada a direção padrão de rolagem da tela – scroll, mas aplica a opção escolhida a todos os dispositivos conectados. Em outras palavras, se eu tenho um mouse tradicional que utilizo junto ao trackpad do MacBook, deverei utilizar a mesma direção de rolagem em ambos os dispositivos.

- Direção natural: como nos celulares e tablets, relativa a página
- Direção tradicional: como nos antigos computadores, relativa a barra de rolagem

Felizmente existe o [Karabiner](https://pqrs.org/osx/karabiner/), programa que permite fazer diversas configurações personalizadas para dispositivos específicos.

![Karabiner no Mac OS X](/assets/images/2015-07-19-karabiner.png)

Existem várias configurações pré-definidas para teclado e mouse, mas criei minha própria configuração para inverter a direção da rolagem para meu Microsoft Wireless Mouse. Aqui está meu arquivo private.xml.

<script src="https://gist.github.com/victor-torres/8cb5b5d826dce0aa5e03.js"></script>

Você pode alterar o Vendor ID e o Product ID (identificação do fabricante e do produto) para que a modificação funcione com seu próprio dispositivo. Para descobri-los, abra as preferências do Karabiner e visite Misc -> EventViwer -> Devices.

Agora eu tenho:

- Trackpad: rolagem natural, relatava a página
- Mouse: rolagem tradicional, relativa a barra de rolagem
