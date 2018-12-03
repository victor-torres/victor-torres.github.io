---
layout: post
title:  "Como usar mais de uma shave SSH com git"
date:   2018-12-03 12:00:00 -0300
categories: git, ssh
comments: true
---
Quando alguém vai me adicionar em algum repositório no GitHub, não tem erro: colocam meu nome de usuário [victor-torres](https://github.com/victor-torres) e é sucesso! 

Mas quando alguém precisa me adicionar num repositório no Bitbucket, principalmente quando esse alguém é uma empresa, que te fornece uma conta de e-mail com o domínio dela, por exemplo, aí fica um pouquinho mais complicado.

Digo isso porque você não pode associar uma mesma chave SSH a mais de uma conta no Bitbucket (o que até faz sentido), então fica um pouco chato pra clonar os repositório e fazer push das modificações. Não é mesmo? Não!

Dá pra resolver isso fácil, fácil. Basta criar uma outra chave SSH, que será exclusiva para essa outra conta. 

```
ssh-keygen -t rsa -b 4096 -C "nome@empresa.com"
```

Esse comando vai criar a chave pública e privada e quando ele te perguntar onde salvar os arquivos, você escolhe algo diferente do nome padrão, `id_rsa`. Pode ser algo que identifique melhor a chave, por exemplo `nome-empresa`. Não esqueça de proteger sua chave com uma senha para aumentar um pouco a segurança.

```
Enter a file in which to save the key (/Users/you/.ssh/id_rsa): [Press enter]
```

Agora vamos fazer o pulo do gato, vamos configurar a chave para ser usada com um domínio específico em `~/.ssh/config`:

```
Host bitbucket.org-empresa
	HostName bitbucket.org
	User git
	IdentityFile ~/.ssh/nome-empresa
```

Percebam que a gente colocou um traço e o nome do domínio da empresa que a gente tem a conta de e-mail! Toda vez que bater esse host a gente vai traduzir em bitbucket.org, como seria normalmente, e vamos sempre usar a chave SSH `nome-empresa` que a gente acabou de criar.

E como faz pra clonar um repositório agora? Digamos que você faria normalmente assim:

```
git clone git@bitbucket.org:empresa/repositorio.git
```

Agora você adiciona aquele traço e o nome de domínio da empresa que a gente definiu nos passos anteriores:

```
git clone git@bitbucket.org-empresa:empresa/repositorio.git
```

O restante das operações permanece do mesmo jeito. Pronto, chega de problemas ou desculpas na hora de usar múltiplas contas com o git.

E aí, curtiu?

Referência: [Generating a new SSH key and adding it to the ssh-agent](https://help.github.com/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent/)
