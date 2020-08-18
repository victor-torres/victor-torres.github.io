---
layout: post
title:  "You have new mail"
date: 2020-08-18 10:00:00 -0300
categories: linux, mac, unix, mail
comments: true
---
Já logou num terminal do Linux ou do macOS e se deparou com a mensagem "You have new mail"?
Geralmente, são mensagens de cron jobs ou relatórios de segurança do sistema.
É bom ler pra descobrir o que é! Se não for nada importante, a gente apaga.

# Lendo o mail

O conteúdo dessas mensagens fica salvo num arquivo de texto puro,
geralmente em `/var/mail/<usuário>` ou `/var/spool/mail/<usuário>`.
Você pode simplesmente abrir esse arquivo, editar e ver o que tem dentro.
Porém, existe um programa para facilitar a leitura e a exclusão dessas mensagens,
é o `mail`. Para executá-lo, basta abrir num terminal:

```shell
mail
```

Você deverá ver uma lista dos e-mails disponíveis,
como esta que montei para esse exemplo:

```shell
Mail version 8.1 6/6/93.  Type ? for help.
"/var/mail/victortorres": 2 messages 2 new
>N  1 victortorres@MacBook  Tue Aug 18 09:38  14/596   "Testando"
 N  2 victortorres@MacBook  Tue Aug 18 09:38  14/604   "Testando 2"
?
```

Se você prestar atenção, tem um prompt sinalizado pelo caracter `?`.
Você pode enviar comandos para a aplicação.
Vou falar os mais básicos e necessários:

## Abrir mensagem

Para abrir uma mensagem, basta digitar o número dela e teclar ENTER.
Se eu quiser ler a mensagem 2, por exemplo, basta digitar 2 no prompt e teclar ENTER:

```shell
? 2 <ENTER>
```

O conteúdo da mensagem irá ser impresso na tela e um novo prompt irá aparecer:

```shell
Message 2:
From victortorres@MacBook-Pro-de-Victor.local  Tue Aug 18 09:38:40 2020
X-Original-To: victortorres
Delivered-To: victortorres@MacBook-Pro-de-Victor.local
To: victortorres@MacBook-Pro-de-Victor.local
Subject: Testando 2
Date: Tue, 18 Aug 2020 09:38:40 -0300 (-03)
From: victortorres@MacBook-Pro-de-Victor.local (Victor Torres)

Veja essa outra mensagem

?
```

## Removendo mensagens

Para remover uma mensagem, também é muito simples.
Vamos supor que queremos remover a mensagem 2 que acabamos de ler:

```shell
? d 2 <ENTER>
```

Quer apagar todas as mensagens de uma vez? É possível!

```shell
? d * <ENTER>
```

## Saindo do programa

Terminou de ler e apagar as mensagens? Agora é só sair do programa:

```shell
? q <ENTER>
```
