---
layout: post
title:  "Devo executar um “SELECT *”?"
date:   2016-02-06 14:54:00 -0300
categories: database
---
A resposta curta é não e podemos justificá-la por dois motivos simples.


# Performance

Quando você realiza um SELECT * está estressando o banco porque ele deve primeiro descobrir todas as colunas disponíveis para só então retornar todas elas. Imagine isso acontecendo com tabelas com muitas colunas, um grande volume de dados, alguns JOINs e alguns métodos… Isso tudo pra depois você querer ver apenas um ID e mais um ou dois outros campos.


# Integridade

Para garantir o ordenamento dos dados você deve especificar as colunas que deseja trazer na consulta. É comum ver códigos que selecionam dados de uma tabela e armazenam eles em estruturas de dados sequencialmente. Por exemplo, imagine uma tabela com ID, Nome e E-mail. Você pode fazer um SELECT * e mapear os resultado para as variáveis id, nome e email. Mas e se por acaso a consulta retornar ID, E-mail e Nome? Você terá seus valores trocados e muita coisa pode dar errado por causa disso. Isso pode acontecer por diversos motivos, por exemplo utilizando migrations diferentes ou editando o banco de dados manualmente em produção, adicionando ou alterando colunas.
