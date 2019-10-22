---
layout: post
title:  "Reiniciando builds do Travis sem ser dono do projeto"
date: 2019-09-09 08:00:00 -0300
categories: git, github, travis
comments: true
---
O Travis CI é uma plataforma de integração contínua muito utilizada para rodar os testes de diversos projetos no GitHub, públicos ou privados, principalmente em projetos open-source, pois para eles, o uso da ferramenta é gratuito.

Mas às vezes, o build do Travis CI falha por motivos que não estão necessariamente ligados ao seu código-fonte, como, por exemplo, uma falha de rede ou indisponibilidade temporária de um requisito ou dependência do seu pacote. Pra que o teste do seu pull request fique passando, a gente tem que rodar o pipeline de novo.

Pra fazer isso, nós temos três opções:

- se você é o dono do projeto, simplesmente clique no botão para reiniciar a build
- se você não é o dono do projeto, você também pode submeter um novo commit para disparar um novo build (inclusive um commit em branco!)
- se estiver com um pull request aberto, você pode simplesmente fechar e reabrir o pull request para que o processo de build seja reiniciado

Essa última dica é bem prática quando você tá contribuindo com projetos abertos, você já conhecia?
