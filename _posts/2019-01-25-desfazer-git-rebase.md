---
layout: post
title:  "Desfazer git rebase"
date: 2019-01-25 12:00:00 -0300
categories: git
comments: true
---
Dica rápida para quem acabou de fazer um `git pull --rebase origin master` para atualizar uma branch de desenvolvimento e percebeu que acabou escolhendo a branch errada como origem. Ou qualquer outra variação da operação de rebase.

```
git reset --hard ORIG_HEAD
```

Este comando vai simplesmente desfazer o último rebase que você fez.
