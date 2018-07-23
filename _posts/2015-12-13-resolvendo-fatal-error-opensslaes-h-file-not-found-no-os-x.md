---
layout: post
title:  "Resolvendo “fatal error: ‘openssl/aes.h’ file not found” no OS X"
date:   2015-12-13 17:18:00 -0300
categories: macos
---
A Apple parou de utilizar o OpenSSL no OS X El Capitan e em seu lugar utiliza seu próprio TLS e bibliotecas de criptografia.

Geralmente, não há nenhum problema nisso, mas alguns softwares que dependem dessa biblioteca podem ter problemas com isso. Um exemplo é o cryptography. Se você tentar executar o comando pip install cryptography provavelmente encontrará um erro na compilação dizendo que o cabeçalho aes.h da lib openssl não foi encontrado.

Para corrigir, primeiro vamos instalar o OpenSSL utilizando o Homebrew.

    brew install openssl

Depois, vamos tentar instalar o cryptography novamente (ou o software que depende da lib openssl), mas passando algumas informações adicionais de onde se encontram os arquivos necessários para o build.

    env LDFLAGS="-L$(brew --prefix openssl)/lib" CFLAGS="-I$(brew --prefix openssl)/include" pip install cryptography

Pronto. Tudo deve ter funcionado agora :)
