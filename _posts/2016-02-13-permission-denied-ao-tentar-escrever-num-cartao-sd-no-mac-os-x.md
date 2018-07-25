---
layout: post
title:  "“Permission denied” ao tentar escrever num Cartão SD no Mac OS X"
date:   2016-02-13 11:33:00 -0300
categories: macos
comments: true
---
Fui tentar gravar uma imagem num SD card para utilizar num Raspberry Pi e fiz o procedimento de costume. Desmontei o disco com o diskutil:

    sudo diskutil unmountDisk /dev/disk4

E depois copiei a imagem com o dd:

    sudo dd if=~/raspbian.img of=/dev/rdisk4 bs=4m

Mas logo o terminal respondeu que eu não tinha permissão para realizar a tarefa. Isso geralmente acontece com cartões SD quando a trava ou lock está ativada.

![Wikimedia Commons: cartão de memória destravado e travado para escritas.](/assets/images/2016-02-13-permission-denied-ao-tentar-escrever-num-cartao-sd-no-mac-os-x.png)

Mas verifiquei o cartão e ele estava habilitado para realizar escritas. Então o que mais poderia ser? Pesquisando um pouco cheguei ao [fórum do Ubuntu](http://askubuntu.com/questions/215262/dd-dev-disk4-permission-denied-error-when-making-liveusb-on-mac-os-x), onde foi dito que vez ou outra o sensor do leitor de cartões do MacBook trava e não consegue distinguir se um cartão está destravado ou não.

A solução é **remover o cartão de memória do slot e soprar o próprio slot** com a boca e os pulmões mesmo ou utilizar uma latinha de ar comprimido. Como dizem meus colegas de trabalho: deu certo e tudo!
