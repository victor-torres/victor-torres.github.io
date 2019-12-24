---
layout: post
title:  "Instalando dependências do git em Python"
date: 2019-12-24 08:30:00 -0300
categories: git, python, pip, pipenv
comments: true
---
Supondo que nós queremos instalar a biblioteca request, mas ao invés de usar a origem padrão, queremos que ela seja instalada a partir de seu repositório git. Pra fazer isso, basta adicionar a seguinte linha no seu `requirements.txt`:

```
git+https://github.com/requests/requests.git
```

Porém, pode ser que tanto seu editor de código quanto sua aplicação tenham um pouco de dificuldade para encontrar o pacote, então vamos dar uma dica pra eles:

```
git+https://github.com/requests/requests.git#egg=requests
```

Com o `#egg=requests` no final da linha, dizemos qual o nome da biblioteca que estamos instalando a partir desse repositório e evitamos que outras aplicações tenham problemas ao tentar encontrar esse pacote.

Para saber mais informações, estes links podem ser interessantes:

- [pip - VCS Support: Git](https://pip.pypa.io/en/stable/reference/pip_install/#git)
- [pipenv - A Note about VCS Dependencies](https://pipenv-fork.readthedocs.io/en/latest/basics.html#a-note-about-vcs-dependencies)
