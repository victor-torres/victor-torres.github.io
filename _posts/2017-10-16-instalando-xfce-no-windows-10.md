---
layout: post
title:  "Instalando XFCE no Windows 10"
date:   2017-10-16 14:54:00 -0300
categories: windows
---
Agora que o Windows roda um Linux quase que nativamente, nada mais natural do que imaginar uma interface gráfica rodando junto num mesmo sistema.

- sem mais necessidade de dual boot ou linux em full screen no windows
- possibilidade de executar aplicações linux em janelas do windows

Pode parecer complicado, mas o setup é bem simples. Partindo do pressuposto que você possui o WSL – Windows Subsystem for Linux configurado corretamente, siga os seguintes passos.


# Instalando um servidor de janelas X no Windows

Um servidor de janelas X é o responsável por desenhar na tela o que os programas precisam mostrar para o usuário. No Linux nós temos os nossos próprios servidores X, que nesse caso rodam localmente, mas podemos ter também servidores remotos.

Eu indico o VcXserv para ser instalado no Windows. Ele pode ser encontrado gratuitamente acessando o link [https://sourceforge.net/projects/vcxsrv/](https://sourceforge.net/projects/vcxsrv/).


# Configurando o servidor de janelas X no WSL

No seu Linux dentro do Windows, vamos configurar para qual servidor de janelas X nossos programas vão mandar as coisas que devem aparecer na tela. Para isso, vamos adicionar algumas variáveis no nosso script de inicialização.

Se você usa bash, execute:

    echo 'export DISPLAY=:0.0' >> ~/.bashrc 
    source ~/.bashrc

Se você usa zsh, execute:

    echo 'export DISPLAY=:0.0' >> ~/.zshrc 
    source ~/.zshrc


# Configurando dbus

Há uma thread no reddit explicando por que temos de usar TCP ao invés de Unix Sockets nas configurações de session do dbus. Você pode ler mais sobre isso clicando [neste link](https://www.reddit.com/r/Windows10/comments/4rsmzp/bash_on_windows_getting_dbus_and_x_server_working/) ou apenas executar o comando à seguir.

    sudo sed -i 's$<listen>.*</listen>$<listen>tcp:host=localhost,port=0</listen>$' /etc/dbus-1/session.conf


# Instalando o XFCE

Eu estou usando como exemplo o ambiente gráfico XFCE rodando na distribuição Ubuntu, mas este tutorial pode ser adaptado para diferentes sabores de linux distros e configurações.

    sudo apt-get install xubuntu-desktop -y


# Executanto o XFCE

    xfce4-session

Dá pra configurar o VcXserv para executar de diferentes maneiras.

- uma única janela full screen
- uma única janela ocupando todo o espaço do monitor
- várias pequenas janelas por aplicação
- etc.


# Uma janela por aplicação

Dá pra usar ele em tela cheia, mas eu não achei muito interessante. A performance é boa, mas não é a mesma coisa de rodar o sistema operacional nativamente.

Eu preferi executar o modo de uma única jenela por aplicação. Dessa forma, depois de iniciar o XFCE, eu finalizo o painel superior (também desabilitei o painel inferior) e depois disso executo a aplicação que desejo em background. Ela fica como se fosse uma aplicação nativa do Windows, inclusive com **área de transferência compartilhada**, ou seja, funciona **Ctrl + C** e **Ctrl + V** entre os sistemas, tudo transparente.

Ao invés de rodar xfce4-session, carregando o sistema completo do xfce, você pode fazer apenas **xfsettingsd**. Dessa forma o sistema fica bem mais leve e menos processos são iniciados, apenas os necessários. Ah, as fontes ficam OK na tela também.

    xfsettingsd &
    terminator &
