---
layout: post
title:  "Configurações do git push"
date:   2016-03-12 09:27:00 -0300
categories: git
comments: true
---
Você pode escolher como quer que o git faça o envio das modificações em seu repositório local através da configuração push.default. Veja a lista de opções e o que cada uma delas faz:

| Configuração	| O que ela faz                                                                                                     |
|---------------|-------------------------------------------------------------------------------------------------------------------|
| nothing	    | Não faz push de nada                                                                                              |
| matching	    | Faz push de todas as branches em comum entre o repositório local e o remoto                                       |
| upstream	    | Faz push da branch atual para a seu upstream (tracking é um sinônimo obsoleto para upstream)                      |
| current	    | Faz push da branch atual para sua branch de mesmo nome no repositório remoto                                      |
| simple	    | Parecido com o upstream, mas se recusa a fazer push se o upstream remoto da branch tiver um nome dirente da local |

Existe uma configuração padrão e ela muda dependendo da versão do git:

| Versão do git	    | Configuração padrão                       |
|-------------------|-------------------------------------------|
| 1.x	            | matching                                  |
| 2.x	            | simple (disponível a partir do 1.7.11)    |

Para modificar a configuração padrão, você pode fazer, por exemplo:

    git config --global push.default current

As configurações simple, current e upstream são pra quem deseja enviar apenas uma branch. Isso é legal porque após terminar seu trabalho com uma delas você pode simplesmente enviá-la e deixar as que ainda estão pendentes ou inacabadas intactas.

    git push origin <branch name>

Se torna:

    git push

Para mais informações veja a [documentação original do git.config](http://git-scm.com/docs/git-config).
