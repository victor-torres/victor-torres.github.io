---
layout: post
title:  "Como rodar o Carnê Leão no macOS e outros programas da Receita"
date:   2018-12-14 19:20:00 -0300
categories: macos, receita federal, carne leao, java
comments: true
---
O programa do Carnê Leão 2018 está disponível no site da [Receita Federal](http://idg.receita.fazenda.gov.br/orientacao/tributaria/pagamentos-e-parcelamentos/pagamento-do-imposto-de-renda-de-pessoa-fisica/carne-leao/2018/programa-carne-leao-2018). 

Segundo o próprio site da Receita, o programa foi desenvolvido em Java e pode ser utilizado em qualquer sistema operacional, desde que obedecida a seguinte condição: tenha instalada a Máquina Virtual Java (JVM), versão 1.7 ou posterior.

No entanto, o programa não parece ser compatível com as versões mais novas da JRE ou do JDK. O programa até abre, mas o básico não funciona e não dá pra usar pra gerar as declarações. Então o que precisamos fazer? Instalar o Java 7, como solicitado!

No Windows, ele parece funcionar de boa porque provavelmente os desenvolvedores incluem uma versão portátil do Java dentro do executável do programa. Então vai funcionar independente do Java instalado em seu sistema. Mas nos outros sitemas operacionais, macOS e Linux, a história é diferente.

Não é mais possível fazer o download público dos instaladores antigos do Java 7, por exemplo, segundo o prório [site da plataforma](https://www.java.com/pt_BR/download/faq/java_7.xml).

Mas tem uma página escondida com os arquivos desses instaladores no site da Oracle. Para ter acesso a esta lista, [clique aqui](https://www.oracle.com/technetwork/java/javase/downloads/java-archive-downloads-javase7-521261.html). Você vai precisar fazer um cadastro no site da Oracle para concluir o download.

Eu baixei a versão DMG do JRE 7u80 e instalei normalmente no macOS Mojave 10.14.1.

Como fazemos pra executar o Carnê Leão então? No terminal, supondo que você extraiu o arquivo zip com os arquivos do programa na sua pasta de Downloads, então é só fazer o seguinte:

    $ /Library/Internet\ Plug-Ins/JavaAppletPlugin.plugin/Contents/Home/bin/java -jar ~/Downloads/LEAO2018/PgdCarneLeao.jar

Como eu não quero ter de lembrar desse caminho toda a vida, resolvi criar um link pra deixar a execução mais fácil:

    $ ln -sf /Library/Internet\ Plug-Ins/JavaAppletPlugin.plugin/Contents/Home/bin/java /usr/local/bin/java7

Pra executar eu faço assim agora:

    $ java7 -jar ~/Downloads/LEAO2018/PgdCarneLeao.jar

Espero que tenham gostado e que isso ajude vocês.
