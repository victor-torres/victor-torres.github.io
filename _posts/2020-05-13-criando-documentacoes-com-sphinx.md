---
layout: post
title:  "Criando documentações com Sphinx"
date: 2020-05-13 12:00:00 -0300
categories: python, docs, sphinx
comments: true
---
Uma parte muito importante de um projeto de software é sua documentação.
Existem diversas maneiras de gerar e gerenciar a documentação de um projeto.
Em Python, uma das principais alternativas é o Sphinx.

## Sphinx

O [Sphinx](https://www.sphinx-doc.org/en/master/) – Python Documentation Generator – é um gerador de documentação que teve seu primeiro release público em 2008. Ele é escrito em Python e é utilizado por projetos famosos como [Django](https://docs.djangoproject.com/) e [SQLAlchemy](https://docs.sqlalchemy.org/en/13/), mas pode ser utilizado em outros ambientes, como é o caso do [Kernel](https://www.kernel.org/doc/html/latest/) do Linux.

Ele converte conteúdo reStructuredText (rst) em páginas web, documentos em PDF, LaTeX, EPub e vários outros. É extremamente extensível e conta com diversos plugins disponíveis na comunidade.

## Read the Docs

O [Read the Docs](https://readthedocs.org/) é uma plataforma open-source de hospedagem para documentações que utiliza Sphinx para gerar o seu conteúdo. Está disponível desde 2010. Vários projetos famosos utilizam o site, por exemplo, o [Scrapy](https://docs.scrapy.org/). Você pode utilizar a plataforma para gerar e hospedar a documentação do seu projeto gratuitamente.

## reStructuredText

reStructuredText é a linguagem de marcação de texto padrão do Sphinx. Ela serve a um propósito semelhante ao do Markdown.

Recomendo que você aprenda pelo menos o básico sobre sua utilização [aqui](https://www.sphinx-doc.org/en/master/usage/restructuredtext/basics.html).

## Antes de começar

Recentemente, comecei a trabalhar no [web-poet](https://github.com/scrapinghub/web-poet), um projeto open-source da [Scrapinghub](https://scrapinghub.com/). É ele que utilizarei como base para escrever esse tutorial.

O primeiro passo para começar a trabalhar na documentação é clonar o repositório e instalar o pacote em modo de desenvolvimento num ambiente virtual:

### Clonando e acessando o repositório

```shell
git clone git@github.com:scrapinghub/web-poet.git
cd web-poet
```

### Criando e ativando um ambiente virtual

```shell
python -m virtualenv ~/.virtualenvs/web-poet
source ~/.virtualenvs/web-poet/bin/activate
```

### Instalando o pacote em modo de desenvolvimento

```shell
python setup.py develop
```

## Criando a documentação

### Instalando o Sphinx

O Sphinx é um pacote Python que pode ser obtido do [PyPI](https://pypi.org/) e instalado com o `pip`.

```shell
pip install sphinx
```

### Inicializando a documentação

Vamos colocar a documentação dentro da pasta docs, para separar seu conteúdo do restante do projeto:

```shell
mkdir docs
cd docs
```

Depois disso, vamos rodar o quick-start do Sphinx:

```shell
sphinx-quickstart
```

Nesse ponto, o utilitário irá fazer diversas perguntas pra você. Vou colar as perguntas e as respostas que dei para que você possa se basear por elas. Onde não tiver *y* ou *n*, foi porque eu optei por utilizar a resposta padrão da pergunta.

```shell
Welcome to the Sphinx 1.8.5 quickstart utility.

Please enter values for the following settings (just press Enter to
accept a default value, if one is given in brackets).

Selected root path: .

You have two options for placing the build directory for Sphinx output.
Either, you use a directory "_build" within the root path, or you separate
"source" and "build" directories within the root path.
> Separate source and build directories (y/n) [n]:

Inside the root directory, two more directories will be created; "_templates"
for custom HTML templates and "_static" for custom stylesheets and other static
files. You can enter another prefix (such as ".") to replace the underscore.
> Name prefix for templates and static dir [_]:

The project name will occur in several places in the built documentation.
> Project name: web-poet
> Author name(s): Scrapinghub
> Project release []: 0.0.1

If the documents are to be written in a language other than English,
you can select a language here by its language code. Sphinx will then
translate text that it generates into that language.

For a list of supported codes, see
http://sphinx-doc.org/config.html#confval-language.
> Project language [en]:

The file name suffix for source files. Commonly, this is either ".txt"
or ".rst".  Only files with this suffix are considered documents.
> Source file suffix [.rst]:

One document is special in that it is considered the top node of the
"contents tree", that is, it is the root of the hierarchical structure
of the documents. Normally, this is "index", but if your "index"
document is a custom template, you can also set this to another filename.
> Name of your master document (without suffix) [index]:
Indicate which of the following Sphinx extensions should be enabled:
> autodoc: automatically insert docstrings from modules (y/n) [n]: y
> doctest: automatically test code snippets in doctest blocks (y/n) [n]:
> intersphinx: link between Sphinx documentation of different projects (y/n) [n]: y
> todo: write "todo" entries that can be shown or hidden on build (y/n) [n]:
> coverage: checks for documentation coverage (y/n) [n]:
> imgmath: include math, rendered as PNG or SVG images (y/n) [n]:
> mathjax: include math, rendered in the browser by MathJax (y/n) [n]:
> ifconfig: conditional inclusion of content based on config values (y/n) [n]:
> viewcode: include links to the source code of documented Python objects (y/n) [n]: y
> githubpages: create .nojekyll file to publish the document on GitHub pages (y/n) [n]:

A Makefile and a Windows command file can be generated for you so that you
only have to run e.g. `make html' instead of invoking sphinx-build
directly.
> Create Makefile? (y/n) [y]:
> Create Windows command file? (y/n) [y]: n

Creating file ./conf.py.
Creating file ./index.rst.
Creating file ./Makefile.

Finished: An initial directory structure has been created.

You should now populate your master file ./index.rst and create other documentation
source files. Use the Makefile to build the docs, like so:
   make builder
where "builder" is one of the supported builders, e.g. html, latex or linkcheck.
```

Basicamente, minhas únicas modificações em relação às respostas padrão do Sphinx foram:

- habilitar o módulo `autodoc` para gerar documentação de código automaticamente
- habilitar o módulo `intersphinx` para relacionar documentações externas de outros projetos sphinx
- habilitar o módulo `viewcode` para disponibilizar links para visualizar o código-fonte
- não gerar um *command file* pra Windows

Neste ponto, agora você já pode gerar a sua documentação utilizando o comando:

```shell
make html
```

Escolhi o formato de página web em que o conteúdo é salvo em `_build/html`. No macOS, usei o seguinte comando para abrir o arquivo no meu navegador, mas você pode apenas abrir a página manualmente através do seu gerenciador de arquivos:

```shell
open -a Google\ Chrome _build/html/index.html
```

A página deve se parecer com isto:

![Sphinx](/assets/images/2020-05-13-sphinx.png)

## Modificando o tema

Com a documentação funcionando, é hora de trocar o tema. Escolhi o tema do Read the Docs, pois é o tema utilizado também na documentação do Scrapy, o que fará com o que o usuário se sinta mais em casa ao ler a documentação do web-poet.

### Instalando o tema

```shell
pip install sphinx-rtd-theme
```

### Configurando o tema

No arquivo `conf.py`, edite a região *Options for HTML output* para que se pareça com o seguinte:

```python
# -- Options for HTML output -------------------------------------------------

# The theme to use for HTML and HTML Help pages.  See the documentation for
# a list of builtin themes.
#
html_theme = 'sphinx_rtd_theme'

# Add any paths that contain custom themes here, relative to this directory.
# Add path to the RTD explicitly to robustify builds (otherwise might
# fail in a clean Debian build env)
import sphinx_rtd_theme
html_theme_path = [sphinx_rtd_theme.get_html_theme_path()]
```

Mais um `make html` e podemos ver como ficou a nossa documentação agora.

![Sphinx RTD Theme](/assets/images/2020-05-13-sphinx-rtd-theme.png)

## Escrevendo o índice

O arquivo `index.rst` é gerado automaticamente, mas eu particularmente não gosto muito da estrutura inicial. Prefiro um arquivo mais sucinto e direto ao ponto. Algo parecido com isto:

```rst
======================
web-poet documentation
======================

web-poet implements Page Object pattern for web scraping.

The goal of this project is to make reusable Page Objects that separates
extraction logic from crawling. They could be easily tested and distributed
across different projects. Also, they could make use of different backends,
for example, acquiring data from `Splash`_ and `AutoExtract`_ API.

Please, see also our Installation guide and our Tutorial for a quick start.

License is BSD 3-clause.

.. _`AutoExtract`: https://scrapinghub.com/autoextract
.. _`Splash`: https://scrapinghub.com/splash
.. _`web-poet`: https://github.com/scrapinghub/web-poet

.. toctree::
   :maxdepth: 2
   :hidden:
```

Note que é importante que o seu arquivo de índice contenha pelo menos uma `toctree`. Você vai entender melhor como essa diretiva funciona na prática, mas resumidamente, é um índice que é utilizado para construir o menu de navegação e organizar suas ligações entre as páginas da documentação.

## Criando páginas

### Licença

A primeira página que vou adicionar vai ser a página que contém a licença do projeto. O arquivo será chamado `license.rst`:

```rst
.. _`license`:

=======
License
=======

.. include:: ../LICENSE
```

Aqui aprendemos duas coisas muito interessantes.

A primeira delas é que podemos nomear uma seção da documentação para referenciá-la posteriormente. Nesse caso, fazemos com ```.. _`license`:```. Com isso, podemos retornar ao arquivo `index.rst` e transformar o texto `License` em uma referência para esta página:

```rst
...

Please, see also our Installation guide and our Tutorial for a quick start.

:ref:`license` is BSD 3-clause.

...
```

Também precisamos adicionar a página `license` a pelo menos uma `toctree`. Faremos isso na principal, também no arquivo `index.rst`, que ficará da seguinte maneira:

```rst
======================
web-poet documentation
======================

web-poet implements Page Object pattern for web scraping.

The goal of this project is to make reusable Page Objects that separates
extraction logic from crawling. They could be easily tested and distributed
across different projects. Also, they could make use of different backends,
for example, acquiring data from `Splash`_ and `AutoExtract`_ API.

Please, see also our Installation guide and our Tutorial for a quick start.

:ref:`license` is BSD 3-clause.

.. _`AutoExtract`: https://scrapinghub.com/autoextract
.. _`Splash`: https://scrapinghub.com/splash
.. _`web-poet`: https://github.com/scrapinghub/web-poet

.. toctree::
   :maxdepth: 2
   :hidden:

   license
```

![Sphinx Index](/assets/images/2020-05-13-sphinx-index.png)

A outra coisa que aprendemos foi como inserir texto de outros arquivos do projeto. Nesse caso, estamos reaproveitando o texto que já existe no arquivo `LICENSE`, na raiz do projeto Python.

```rst
.. include:: ../LICENSE
```

![Sphinx License](/assets/images/2020-05-13-sphinx-license.png)

Nós faremos algo semelhante com o arquivo de changelog.

### Changelog

Nossa página `changelog.rst` será semelhante à nossa página de licença, ela vai incluir um arquivo da raiz do projeto.

```rst
.. include:: ../CHANGELOG.rst
```

Claro, precisamos adicionar a página ao nosso `toctree` principal no `index.rst`:

```rst
.. toctree::
   :maxdepth: 2
   :hidden:

   changelog
   license
```

Quando você abre a página de changelog, veja como fica o sub-menu lateral:

![Sphinx Changelog](/assets/images/2020-05-13-sphinx-changelog.png)

## Guia de contribuição

Precisamos adicionar uma página com informações sobre como contribuir com o projeto. O nome do arquivo será `contributing.rst`:

```rst
============
Contributing
============

web-poet is an open-source project. Your contribution is very welcome!

Issue Tracker
=============

If you have a bug report, a new feature proposal or simply would like to make
a question, please check our issue tracker on Github: https://github.com/scrapinghub/web-poet/issues

Source code
===========

Our source code is hosted on Github: https://github.com/scrapinghub/web-poet

Before opening a pull request, it might be worth checking current and previous
issues. Some code changes might also require some discussion before being
accepted so it might be worth opening a new issue before implementing huge or
breaking changes.

Testing
=======

We use tox_ to run tests with different Python versions::

    tox

The command above also runs type checks; we use mypy.

.. toctree::
   :hidden:

.. _tox: https://tox.readthedocs.io
```

Ele deverá ficar parecido com isto:

![Sphinx Contributing](/assets/images/2020-05-13-sphinx-contributing.png)

## Referência da API

Aqui a brincadeira começa a ficar boa. Vamos usar o módulo `autodoc` para criar documentação de módulos, classes e funções da API do nosso pacote automaticamente. 

Uma opção é pedir pra que o Sphinx gere a documentação do módulo automaticamente:

```rst
=============
API Reference
=============

Pages
=====

.. automodule:: web_poet.pages
   :members:
```

Mas quero um pouco mais de controle e também poder ordenar os itens da melhor forma possível, então vou montar cada um individualmente:

```rst
=============
API Reference
=============

Pages
=====

.. autoclass:: web_poet.pages.Injectable
   :members:
   :no-special-members:


.. automethod:: web_poet.pages.is_injectable

.. autoclass:: web_poet.pages.ItemPage
   :members:
   :no-special-members:

.. autoclass:: web_poet.pages.WebPage
   :members:
   :no-special-members:

.. autoclass:: web_poet.pages.ItemWebPage
   :members:
   :no-special-members:

Page Inputs
===========

.. autoclass:: web_poet.page_inputs.ResponseData
   :members:
   :no-special-members:

Mixins
======

.. autoclass:: web_poet.mixins.ResponseShortcutsMixin
   :members:
   :no-special-members:
```

Não esquecer de atualizar o `toctree` principal:

```rst
.. toctree::
   :maxdepth: 2
   :hidden:

   api_reference
   contributing
   changelog
   license
```

O resultado final fica assim:

![Sphinx API Reference](/assets/images/2020-05-13-sphinx-api-reference.png)

## Guia de instalação

Uma boa documentação deve ter um guia de instalação. A nossa não será diferente. Vamos colocar pela primeira vez uma página dentro de um diretório separado. Vamos criar o arquivo `intro/install.rst`:

```rst
.. _`intro-install`:

==================
Installation guide
==================

Installing web-poet
===================

web-poet is a library that runs on Python 3.6 and above.

If you’re already familiar with installation of Python packages, you can install
web-poet and its dependencies from PyPI with:

::

    pip install web-poet

Things that are good to know
============================

web-poet is written in pure Python and depends on two key Python packages:

- attrs_, reduces boilerplate when creating data-classes
- parsel_, responsible for css and xpath selectors

.. _attrs: https://github.com/python-attrs/attrs
.. _parsel: https://github.com/scrapinghub/parsel
```

Vamos adicionar um novo `toctree` ao nosso `index.rst`:

```rst
.. toctree::
   :caption: Getting started
   :hidden:

   intro/install

.. toctree::
   :caption: Reference
   :maxdepth: 2
   :hidden:

   api_reference
   contributing
   changelog
   license
```

O novo `toctree` e a utilização do parâmetro caption vai permitir que a gente tenha um resultado final assim:

![Sphinx Installation Guide](/assets/images/2020-05-13-sphinx-installation-guide.png)

Não vamos esquecer de atualizar nosso `index.rst` para fazer referência à nossa nova página:

```rst
Please, see also our :ref:`intro-install` and our Tutorial for a quick start.
```

Vou fazer a mesma coisa para o Tutorial, mas pra não alongar muito o post, vou deixar pra você conferir o resultado final neste [pull request](https://github.com/scrapinghub/web-poet/pull/5) disponível no Github do projeto.

## Interligando documentações externas

Dá pra fazer referência a outras documentações usando Sphinx. O seguinte código, por exemplo:

```rst
How to create a :ref:`spider <scrapy:topics-spiders>`
```

Pode gerar o seguinte texto:

> How to create a [Spider](https://docs.scrapy.org/en/latest/topics/spiders.html#topics-spiders)

Para isso, precisamos configurar as ligações externas no arquivo `conf.py`. Neste exemplo, eu adiciono a documentação do Scrapy além da documentação do Python.

```python
# -- Extension configuration -------------------------------------------------

# -- Options for intersphinx extension ---------------------------------------

# Example configuration for intersphinx: refer to the Python standard library.
intersphinx_mapping = {
    'python': ('https://docs.python.org/3', None, ),
    'scrapy': ('https://docs.scrapy.org/en/latest', None, ),
}
```

No momento da build, o Sphinx vai carregar as referências desses outros projetos e gerar sua documentação com links atualizados.

## Detalhes

### .gitignore

Gosto de ignorar as pastas temporárias para que elas não sejam versionadas no repositório.

Adicionei isto ao .gitignore do projeto:

```shell
# Docs
docs/_build
docs/_static
docs/_templates
```

### requirements.txt

É sempre bom guardar as dependências necessárias para gerar a documentação. 

Criei um arquivo requirements.txt dentro da pasta `docs` exclusivo para a documentação:

```shell
pip freeze | grep -i sphinx > requirements.txt
```

Isso gerou o seguinte conteúdo:

```python
Sphinx==3.0.3
sphinx-rtd-theme==0.4.3
sphinxcontrib-applehelp==1.0.2
sphinxcontrib-devhelp==1.0.2
sphinxcontrib-htmlhelp==1.0.3
sphinxcontrib-jsmath==1.0.1
sphinxcontrib-qthelp==1.0.3
sphinxcontrib-serializinghtml==1.1.4
```

Esse arquivo pode ser utilizado pelo Read the Docs para instalar dependências necessárias para a construção da documentação, por exemplo, módulos que serão linkados por alguma parte do texto ou gerados automaticamente com o `autodoc`.

O deploy no Read the Docs é algo que eu planejo escrever sobre em um próximo artigo.

Espero que tenham gostado. Acho que esse foi o maior post aqui no blog até agora :)
