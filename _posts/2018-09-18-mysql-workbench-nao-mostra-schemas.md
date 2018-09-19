---
layout: post
title:  "MySQL Workbench não mostra schemas no Windows"
date:   2018-09-19 20:00:00 -0300
categories: mysql, windows
comments: true
---
Esses dias eu tive de instalar o MySQL 8 no Windows 10 pra executar o projeto de um colega meu e juntamente com o banco de dados,
instalei o MySQL Workbench, uma interface gráfica para gerenciamento do banco, schemas, usuários e permissões.

Depois de criar um novo schema para utilizar numa aplicação web de testes, percebi que era impossível visualizar o schema criado
na barra lateral da aplicação e o botão para recarregar os schemas disponíveis também não estava funcionando.

Para resolver, eu apaguei alguns arquivos que, segundo pesquisas na internet, servem como uma espécie de cache para essas informações.

Fechei a aplicação, executei os seguintes comandos e depois abri novamente o MySQL Workbench. Funcionou que é uma beleza =D

```
cd %AppData%\MySQL\Workbench
del wb_options.xml
del wb_state.xml
```

Fiz usando o CMD do Windows (ou Prompt de Comando), mas você também pode chegar no mesmo resultado utilizando o Explorer.
