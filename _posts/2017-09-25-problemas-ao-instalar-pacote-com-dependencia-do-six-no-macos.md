---
layout: post
title:  "Problemas ao instalar pacote com dependência do six no macOS"
date:   2017-09-25 12:00:00 -0300
categories: macos
---
Se você está tentando fazer um pip install virtualenvwrapper, por exemplo, ou de algum outro pacote que depende do six, pode encontrar o seguinte erro no OS X El Capitan, macOS Sierra ou em diante:

    OSError: [Errno 1] Operation not permitted:

Esse erro acontece por causa das novas políticas de segurança do sistema (algo relacionado ao rootless). Como o macOS mantém uma versão mais antiga do six e alguns pacotes pedem que ela seja atualizada, pode ser que você não consiga fazer isso se estiver com o modo rootless habilitado.

Você pode tentar fazer o seguinte workaround enquanto estiver instalando o pacote desejado, mas não é certeza que dará certo.

    pip install --ignore-installed six

No meu caso, eu só usei pra instalar o virtualenvwrapper. Todos os outros pacotes que preciso instalar eu acabado fazendo isso dentro de um virtual environment, ou seja, não tenho esses mesmo problemas que tive com o Python do sistema.

Consegui essas informações com o usuário [dstufft](https://github.com/dstufft) [nesta issue](https://github.com/pypa/pip/issues/3165) no GitHub do projeto pip.
