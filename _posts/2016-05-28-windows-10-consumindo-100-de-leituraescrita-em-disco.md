---
layout: post
title:  "Windows 10 consumindo 100% de leitura/escrita em disco "
date:   2016-04-04 22:18:00 -0300
categories: windows
---
![Windows](/assets/images/2016-05-28-windows.png)

Muitos conhecidos e familiares estavam relatando uma lentidão absurda em computadores com Windows 10 recém instalado. Ao abrir o gerenciador de tarefas nessas máquinas, percebi que o sistema estava mostrando 100% de utilização do disco (não de consumo, mas de IO, entrada/saída de dados; leitura/escrita).

Aparentemente não haviam programas em execução que justificassem tamanho consumo de recursos da máquina e pesquisando um pouco mais na Internet descobri que trata-se de um problema crônico da nova versão do sistema operacional da Microsoft.

Para corrigir de maneira “mágica” o problema, basta acessar as **Configurações** do sistema e em **Notificações** desabilitar a opção **Mostrar dicas sobre o Windows**.

Depois disso a utilização de disco passou de 100% para 0% como num passe de mágica. Pode ser que seja necessário fazer log-off e log-in novamente para que a alteração surta efeito.

Obviamente o pessoal do desenvolvimento fez besteira com essa funcionalidade. É um absurdo um sistema desperdiçar tantos recursos da máquina para realizar uma tarefa aparentemente tão trivial. Além do incômodo com a lentidão do sistema a falha ainda poderá causar outros prejuízos como dano permanente ao sistema de arquivos e ao disco rígido ou unidade de armazenamento em estado sólido devido ao alto número de leituras e escritas desnecessárias.
