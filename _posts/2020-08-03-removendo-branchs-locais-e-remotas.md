---
layout: post
title:  "Removendo branches locais e remotas"
date: 2020-08-03 11:15:00 -0300
categories: git
comments: true
---
Mais uma dica simples e muito útil para remover branches locais e remotas no git:

# Removendo branches locais

```shell
git branch -d <nome da branch>
```

## Exemplo

```shell
git branch -d bugfix/1234
```

# Removendo branches remotas

```shell
git push <nome do remote> --delete <nome da branch>
```

## Exemplo

```shell
git push origin --delete bugfix/4567
```
