---
layout: post
title:  "Instalando o Python para um usuário específico num servidor compartilhado"
date:   2018-12-14 18:30:00 -0300
categories: linux, python
comments: true
---
Hoje eu precisei rodar um código num servidor compartilhado que fica na AWS. O problema é que o código fazia uso extenso de f strings, disponíveis a partir do Python 3.6 e o servidor só disponibilizava Python 3.5.

Como a máquina é compartilhada entre alguns desenvolvedores e diversas aplicações rodam ali, seria arriscado demais e irresponsável instalar um novo binário Python à nível de sistema.

Foi aí que conversando com alguns colegas eu cheguei na solução de instalar o Python 3.7 apenas para o meu próprio usuário utilizando o [miniconda](https://conda.io/miniconda.html).

Lá tem instaladores do Python 2.7 e do Python 3.7 disponíveis para download para as três plataformas: Windows, macOS e Linux. No Linux, você pode fazer algo do tipo:

    $ wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh
    $ chmod +x Miniconda3-latest-Linux-x86_64.sh
    $ ./Miniconda3-latest-Linux-x86_64.sh

Esses comandos vão baixar o instalador, dar permissão de execução ao arquivo e executá-lo na máquina. O instalador faz poucas perguntas e uma delas é o local onde você quer instalar o interpretador Python e os demais pacotes. O importante aqui é que por padrão ele coloca isso em `/home/<usuário>/miniconda3`.

Depois de instalar o Python 3.7 com o miniconda, eu criei um ambiente virtual pro meu projeto. Dentro da minha pasta home, eu executei:

    $ source miniconda3/bin/activate
    $ pip install virtualenv
    $ python -m virtualenv ~/.venvs/<projeto>

Depois disso eu nem preciso mais ativar o ambiente do conda em si, posso simplesmente fazer:

    $ source ~/.venvs/<projeto>/bin/activate

A qualquer momento, você pode rodar estes comandos pra verificar que você tá usando os binários do seu usuário e não os do sistema:

    $ which python
    $ which pip

Espero que isso facilite a vida de vocês e forneça um pouco mais de segurança na hora de compartilhar servidores com vários devs.
