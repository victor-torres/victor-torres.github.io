---
layout: post
title:  "A maneira correta de forçar um git push"
date: 2019-10-30 12:00:00 -0300
categories: git, github
comments: true
---
Não é legal forçar um git push porque você pode estar sobrescrevendo coisas importantes na história do repositório. Porém, tem certas situações em que um `push --force` é necessário. Por exemplo, quando você faz rebase da sua branch de desenvolvimento puxando as últimas modificações ou quando você precisa remover um commit que expõe informações sensíveis da história do repositório.

Mas isso não significa que não existe uma opção melhor. Sempre que precisar fazer um `git push --force`, substitua por um `--force-with-lease` ou "com força, mas com jeitinho".

O `--force-with-lease` vai forçar o envio das mudanças locais para o repositório remoto, mas antes ele verifica se o repositório remoto está exatamente igual ao repositório que você tem em mãos. Se ele não estiver, significa que alguém alterou a história do repositório antes que você pudesse a sobrescrever, então ele impede que você faça isso. Dessa forma fica mais difícil perder informações, caso outra pessoa do seu time tenha feito commit de algo importante na mesma hora.

**TL; DR;** 

- Evite condições de corrida e perda de arquivos
- Use `git push --force-with-lease`
- Não use `git push --force`
