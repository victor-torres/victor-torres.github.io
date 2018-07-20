---
layout: post
title:  "Desabilitando backups do Time Machine no disco local"
date:   2015-06-15 21:28:00 -0300
categories: macos
---
![Time Machine](/assets/images/2015-06-15-time-machine.png)
O Time Machine faz backups automáticos do seu sistema no disco local ou num disco externo de forma automática e periódica, basta ativar essa funcionalidade nas Preferências do Sistema do seu Mac OS X.

No entanto, se você optar por utilizar um disco externo, o sistema ainda assim irá salvar backups mais recentes no seu disco local, ocupando um bom espaço dele. Quanto mais arquivos você tiver, maior o espaço gasto.

Por um lado isso pode ser útil, pois se precisarmos recuperar alguma coisa recente, os últimos backups estarão sempre disponíveis. Por outro, isso pode ocupar um bom espaço do seu disco local, que muitas vezes é limitado (128 ou 256 GB). Então como fazer para desabilitar os backups no disco local e utilizar apenas o disco externo?

A Apple deixou uma opção bem escondida para fazer isso. Abra o terminal do seu computador e digite o seguinte comando:

    sudo tmutil disablelocal

Pronto. Agora seus backups consumirão apenas o espaço do seu disco externo. Para desfazer as alterações e ativar os backups locais novamente, digite:

    sudo tmutil enablelocal
