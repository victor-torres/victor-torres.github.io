---
layout: page
title: Open-source
permalink: /open-source/
---

# [atom-hg](https://github.com/victor-torres/atom-hg)

É a extensão do Mercurial para o editor de texto [Atom](https://atom.io/) com mais de [8.000 instalações](https://atom.io/packages/atom-hg). Mercurial é uma ferramenta livre para gerenciamento e controle de código distribuído. É similar ao Git, mas o Atom não oferece suporte nativo a repositórios Mercurial. Foi por isso que eu decidi implementar essa extensão e foi por isso que a comunidade apreciou bastante o seu lançamento. Ela foi escrita em CoffeeScript e funciona em múltiplas plataformas (Linux, Windows e macOS) utilizando os binários nativos do Mercurial que estão instalados no sistema.


# [sinesp-client](https://github.com/victor-torres/sinesp-client)

É uma interface para a API do SINESP Cidadão, que permite a consulta de placas de licenciamento de veículos brasileiros. O SINESP já oferece uma interface web para a consulta dessas informações, mas requer que o usuário entre com um código captcha. A aplicação Android, por sua vez, não requer a digitação de um código captcha, então a comunidade fez uma engenharia reversa no APK e extraiu algumas informações para imitar as requisições feitas por essa aplicação. A interface foi implementada em Python e é amplamente utilizada por desenvolvedores brasileiros que precisam automatizar as consultas à esta API. Algumas aplicações incluem vigilância e segurança privada e controle de entrada e saída de veículos em estacionamentos. Eu também portei esta interface para C# à pedido de uma empresa particular.


# [python-redis-rate-limit](https://github.com/EvoluxBR/python-redis-rate-limit)

É uma biblioteca para Rate Limit escrita em Python baseada em Redis. Ela utiliza o conjunto de operações INCR, EXPIRE, EVALSHA e EVAL para limitar requisições a diferentes recursos computacionais. Foi desenvolvida por mim durante o período em que trabalhei na Evolux. Em julho de 2016 a biblioteca foi citada na [RedisWeekly](https://web.archive.org/web/20170403114408/http://redisweekly.com/archive/153.html).


# [open-cnl](https://github.com/EvoluxBR/open-cnl)

É uma biblioteca para ler e consultar o banco de dados CNL (Código Nacional de Localidade) seguindo especificações da ANATEL (Agência Nacional de Telecomunicações). Foi escrita em Python durante o período em que trabalhei na Evolux. Essa biblioteca pode ser usada para identificar latitude, longitude, cidade, estado, prestadora e outras informações de um número fixo.


# [verto-docs](https://github.com/EvoluxBR/verto-docs)

É uma [documentação online](http://evoluxbr.github.io/verto-docs/) da biblioteca jQuery do módulo [Verto](https://freeswitch.org/confluence/display/FREESWITCH/mod_verto) do [FreeSWITCH](https://freeswitch.org/). Foi feita usando Jekyll, assim como este site. Criada originalmente por mim e por Stefan Yohansson enquanto trabalhávamos juntos na Evolux. Ela tem uma integração contínua, onde cada commit na branch master gera uma task no Jenkins para que seja feito o deploy automático no GitHub Pages.
