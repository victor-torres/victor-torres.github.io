---
layout: post
title:  "Protegendo seu WordPress de ataques ao XML-RPC com fail2ban"
date:   2016-01-23 14:54:00 -0300
categories: linux
---
Esses dias comecei a receber alertas do NewRelic avisando que um dos meus sites WordPress estava fora do ar. Ao entrar no servidor e analisar o log de erros do NGINX em /var/log/nginx/error.log, percebi que estavam atacando o arquivo xmlrpc.php, provavelmente tentando adquirir acesso ao sistema através de força bruta ou simplesmente para tirar meu serviço do ar.

    2016/01/21 19:09:17 [error] 3355#0: *355 connect() to unix:/var/run/php5-fpm.sock failed (11: Resource temporarily unavailable) while connecting to upstream, client: 185.130.5.209, server: myserver.com, request: "POST /xmlrpc.php HTTP/1.0", upstream: "fastcgi://unix:/var/run/php5-fpm.sock:", host: "127.0.0.1"

O sistema estava em execução num Ubuntu, então foi fácil instalar o fail2ban, um firewall simplificado que analisa logs de aplicações em busca de intrusos.

    apt-get install fail2ban

Depois disso, vamos copiar o arquivo de configuração padrão do fail2ban.

    cp /etc/fail2ban/jail.conf /etc/fail2ban/jail.local

Agora vamos adicionar o nosso filtro do XML-RPC. Basta inserir no final do arquivo jail.local o seguinte:

    [xmlrpc]
    enabled = true
    filter = xmlrpc
    action = iptables[name=xmlrpc, port=http, protocol=tcp]
    logpath = /var/log/nginx/error.log
    bantime = 43600
    maxretry = 2

Isso vai olhar o arquivo de log que a gente passou e vai tentar bater com a expressão regular que a gente vai cadastrar no arquivo /etc/fail2ban/filter.d/xmlrpc.conf.

    [Definition]
    failregex = .*client: <HOST>,.*xmlrpc\.php.*
    ignoreregex =

Toda linha de log que bater com esse regex agora irá cadastrar um novo IP na lista de IPs banidos. Para garantir, vamos reiniciar o fail2ban com:

    /etc/init.d/fail2ban restart

Você pode utilizar o fail2ban para tratar outros tipos de ataque ou analisar o log de outros programas e serviços como o Apache e o SSH, por exemplo. Ele é uma alternativa prática e eficaz, bem simples de implementar, para bloquear o acesso de pessoas indesejadas.

Você pode testar a expressão regular com o seguinte comando:

    fail2ban-regex /var/log/nginx/error.log /etc/fail2ban/filter.d/xmlrpc.conf

E também pode verificar o status da regra, quantas linhas de log bateram com a configuração e quantos IPs estão banidos no momento através do comando:

    fail2ban-client status xmlrpc

Para remover um IP da lista de IPs banidos, é simples também:

    fail2ban-client set xmlrpc unbanip 192.168.0.1

E tenha cuidado quando for implementar regras em serviços como o SSH, você pode banir a si mesmo e ficar sem acesso ao servidor!
