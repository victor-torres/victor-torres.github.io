---
layout: post
title:  "Problemas com o pip após atualização"
date:   2017-09-26 07:30:00 -0300
categories: macos
comments: true
---
> pkg_resources.DistributionNotFound: pip==1.5.4

Se você está tentando **atualizar** ou **instalar o pip** ou algum outro pacote Python e está encontrando um erro parecido com este, experimente seguir estes passos para reestabelecer seu funcionamento (e atualizar sua versão):

    # Livre-se dos pacotes que podem estar com problemas 
    python -m pip uninstall -y setuptools
    python -m pip uninstall -y distribute
    # O comando a seguir deverá falhar agora
    python -c "import pkg_resources"
    # Reinstale os pacotes removidos e o pip
    python -m pip install -U --force-reinstall setuptools
    python -m pip install -U --force-reinstall pip
    # Verifique se está tudo igual e funcionando
    python -m pip --version
    pip --version
    pip list

Consegui essas informações com o usuário [Ivoz](https://github.com/Ivoz) [nesta issue](https://github.com/pypa/pip/issues/1800) no projeto do pip no GitHub.
