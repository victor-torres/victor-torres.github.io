---
layout: post
title:  "Publicando pacotes Python"
date: 2020-08-18 16:50:00 -0300
categories: python, pypi
comments: true
---
Sabe aquele pacote que você instala com o `pip`?
Já pensou em fazer um `pip install seu_pacote`?
Publicar seu pacote no PyPI – Python Package Index é muito fácil!
Veja resumidamente como fazer isso.

# Primeiros passos

Em primeiro lugar, você deve ter um `setup.py` para o seu pacote.
Não irei cobrir como fazer um arquivo de setup aqui neste post,
mas você pode se basear em outros projetos open source.

# Preparando seu pacote

Quando estiver com o `setup.py` pronto,
é hora de gerar suas distribuições:

```shell
python setup.py dist bdist_wheel
```

Você pode adicionar estas pastas ao seu `.gitignore` pra evitar fazer um commit com elas dentro!

```gitignore
build/
dist/
```

# Instalando o Twine

O Twine é um utilitário feito para ajudar na publicação de pacotes Python no PyPI.
Você pode instalá-lo com o pip:

```shell
pip install twine
```

É preciso configurar o Twine com sua conta no PyPI para poder publicar seu pacote no índice.
Para isso, entre no site e faça o seu cadastro: https://pypi.org/.

# Verificando seu pacote

Para ver se o seu setup gerou tudo direitinho,
conforme os passos anteriores,
vamos rodar o seguinte comando:

```shell
twine check dist/*
```

# Fazendo upload do seu pacote

Você pode primeiramente fazer o upload no índice de testes ([Test PyPI](https://packaging.python.org/guides/using-testpypi/)):

```shell
twine upload -r testpypi dist/*
```

Quando estiver pronto e seguro, pode fazer isso de forma definitiva:

```shell
twine upload dist/*
```

O Twine deve pedir suas credenciais pra cada uma dessas operações de envio.
Você pode configurar um arquivo na sua home de usuário para que ele não fique perguntando sempre. Coloque isto em `~/.pypirc`:

```
[distutils]
index-servers=
    pypi
    pypitest

[pypi]
username=<username>
password=<password

[pypitest]
username=<username>
password=<password>
```

Depois desse passo, seu pacote já deve estar disponível no PyPI.
