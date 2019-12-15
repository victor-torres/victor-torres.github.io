---
layout: post
title:  "Movendo o blog pro Github Pages"
date: 2019-12-15 16:00:00 -0300
categories: git, github, github-pages, jekyll
comments: true
---
Hoje migrei o blog de um droplet na Digital Ocean para um repositório no Github.

Eu tenho esse droplet já há mais de 6 anos e estou fazendo planos para desativar o servidor que roda nele. O primeiro passo era mover a hospedagem do meu blog pessoal (este site) pra outro lugar.

Há um tempo atrás, eu tomei a decisão de [mover do Wordpress pra Jekyll](/2018/07/18/welcome-to-jekyll). Hoje essa decisão provou ter valido a pena, pois consegui fazer a migração pro Github Pages em apenas 5 minutos.


## Atualizando dependências

Você precisa trocar a gem do `jekyll` pela do `github-pages`. No caso, o diff fica bem simples:

```diff
#
# This will help ensure the proper Jekyll version is running.
# Happy Jekylling!
- gem "jekyll", "~> 3.8.3"
+ # gem "jekyll", "~> 3.8.3"

# This is the default theme for new Jekyll sites. You may change this to anything you like.
gem "minima", "~> 2.0"

# If you want to use GitHub Pages, remove the "gem "jekyll"" above and
# uncomment the line below. To upgrade, run `bundle update github-pages`.
- # gem "github-pages", group: :jekyll_plugins
+ gem "github-pages", "~> 203", group: :jekyll_plugins

# If you have any plugins, put them here!
group :jekyll_plugins do
```

Você pode consultar qual a versão mais atual [nesta página](https://pages.github.com/versions/).

Depois é só mandar um `bundle install` pra instalar e atualizar o restante das dependências.


## Push para o novo repositório

Você precisa criar um repositório com um formato específico baseado no seu nome de usuário no Github. Por exemplo, se o seu usuário é `fulano`, o nome do repositório fica `fulano.github.io`.

Removi o antigo remote origin do repositório:

```shell
git remove remove origin
```

Cadastrei o novo remote e fiz push:

```
git remote add origin git@github.com:victor-torres/victor-torres.github.io.git
git push
```


## Deploy

O deploy é automático, tanto dessa primeira versão quanto dos commits seguintes. Perceba no passo anterior que eu não utilizei uma branch específica, coloquei todo o código dentro da branch master mesmo. O Github é esperto o suficiente pra entender e gerar seu site estático pra você.


## Domínio próprio

A mudança de domínio foi bem tranquila também. Eu só precisei fazer o seguinte no meu registro DNS, que é gerenciado pela Digital Ocean:

- criar um A record apontando meu host `victortorres.net.br` pra um [IP do Github](https://help.github.com/en/github/working-with-github-pages/managing-a-custom-domain-for-your-github-pages-site#configuring-a-subdomain)
- criar um CNAME apontando o `www` para `victortorres.net.br`

Depois disso, foi só cadastrar o apex domain `victortorres.net.br` nos Settings do repositório, direto no Github.


## Certificados SSL

Outro ponto positivo de migrar pro Github Pages é que ele gera e renova automaticamente os certificados SSL do seu site usando o Lets Encrypt. Antes eu tinha de manter uma série de rotinas e tarefas periódicas no meu servidor pra tomar conta disso. Agora tudo acontece de forma _automágica_ e transparente.

Demora alguns minutos (mas pode ser que demore até 24h) para que o primeiro certificado seja gerado. Depois disso, você pode marcar uma caixinha pra forçar o uso de SSL/HTTPS no seu site diretamente dos Settings do repositório.
