---
layout: post
title:  "Construindo um hackintosh"
date:   2015-08-16 16:13:00 -0300
categories: macos
comments: true
---
Hackintosh é como chamam uma máquina genérica (não-apple) que possui instalado e consegue executar o sistema operacional Mac OS X. Já fiz alguns, todos com hardware Intel, mas nunca documentei o processo. A seguir, algumas informações sobre as peças que eu utilizei e os procedimentos que foram executados.


# Hardware utilizado

| Componente	| Descrição                 |
|---------------|---------------------------|
| Placa-mãe	    | Asus LGA 1150 H81M-A/BR   |
| Processador	| Intel Core i3 3,6GHz 4560 |
| Memória	    | Kingston 4GB 1333 MHz     |
| Armazenamento	| Kingston 120GB SSD V300   |
 

A máquina ficou muito rápida, não senti falta de processamento e não colocaria um i5 no lugar do i3 escolhido, acho que não compensa o investimento. No entanto, seu eu pudesse colocaria mais um pente de memória para fazer 8GB em dual-channel. Não que a memória comprometa o desempenho da máquina, mas pra executar máquinas virtuais ou trabalhar com Photoshop, por exemplo, mais memória ajuda.

São peças relativamente baratas e fáceis de encontrar no mercado brasileiro, quer seja em lojas físicas ou em lojas virtuais. Tudo custou um pouco mais de mil reais porque acrescentei o SSD. Não tive custos com o gabinete, nem com a fonte, pois herdei eles da antiga máquina. Tenho um monitor Samsung de 23″ Full HD e kit de Teclado e Mouse Microsoft, baratos e muito bons.


# Criando um disco de instalação

| Componente	| Descrição                 |
|---------------|---------------------------|
| Pendrive	    | Kingston 8GB DataTraveler |
| Aplicativo	| Instalador do Yosemite    |
| Aplicativo	| Unibeast                  |
 

Como já possuo Mac OS X (utilizo um Macbook Air 13″), utilizei o Unibeast para gerar um disco de instalação do Mac OS X Yosemite, que pode ser baixado gratuitamente pela App Store e já veio atualizado para o 10.10.4, última versão disponível quando fiz o procedimento. Precisei de um pendrive de 8GB formatado pelo Disk Utility.

Devem haver outras alternativas pra quem utiliza Windows, Linux ou outro sistema operacional para gerar um disco de instalação, mas não vou cobrir elas aqui.


# Instalando o Mac OS X

Com a máquina montada, faremos algumas verificações na BIOS, como conferir se o modo SATA AHCI está habilitado. Se você utilizar a mesma placa que citei, provavelmente ele já deverá vir ativado, junto com o boot UEFI. Não tive problemas com nada disso e o instalador iniciou normalmente.

Não existe, basicamente, nenhuma alteração no instalador original da Apple. O Unibeast adiciona apenas um bootloader alternativo e injeta algumas kexts (kernel extensions ou drivers) para que ele consiga ser iniciado em sua máquina. É só ir prosseguindo com a instalação normalmente, selecionar um disco de instalação etc.


# Instalando drivers e configurando o boot

| Componente	| Descrição                 |
|---------------|---------------------------|
| Kext	        | Intel HD Graphics 4400    |
| Kext	        | Realtek ALC887b/888       |
| Aplicativo	| Kext Wizard               |
| Aplicativo	| Multibeast                |
| Aplicativo	| TRIM Enabler              |
 

É raro tudo funcionar 100% numa máquina hackintosh. No meu caso, ficou faltando apenas o driver da placa de rede Ethernet e o driver de vídeo. O sistema iniciou com vídeo, inclusive em alta resolução, mas não havia aceleração gráfica, o que significa nada de transparência ou vídeos.

Não procurei instalar o driver de rede, pois acesso a Internet através de um adaptador Wi-Fi USB, que comprei quando fiz o hackintosh no meu ultrabook HP, ano passado (o adaptador Wi-Fi embutido não era suportado).


# Vídeo

O que fiz foi apenas inserir duas kexts para ativar o suporte completo ao vídeo da minha GPU On-board da Intel, a HD 4400. Mais abaixo, na inicialização, haverão algumas configurações que permitem o carregamento dessas kexts e a correta identificação do hardware de vídeo pelo sistema.

[Clique aqui](http://www.insanelymac.com/forum/topic/253395-kext-wizard-easy-to-use-kext-installer-and-more/) para baixar o Kext Wizard, programa que permite a fácil instalação de novas kexts no sistema operacional e [clique aqui](https://bitbucket.org/RehabMan/os-x-fake-pci-id/downloads) para baixar as kexts de vídeo citadas.

Instale apenas as kexts FakePCIID_HD4600_HD4400.kext e FakeCPIID.kext.


# Áudio

O hardware de áudio dessa placa-mão é bem genérico, apesar de não estar disponível por padrão no Mac OS X, pode ser facilmente instalado através do MultiBeast. Abra o programa e clique em Clear para limpar a auto-seleção de coisas. Selecione a aba Drivers e marque apenas o driver de áudio referente aos dispositivos com chipset Realtek ALC887b/888 (current). Avance com a instalação. Após concluí-la, reinicie o computador.


# Disco

Além disso, teve mais uma coisa que eu instalei, o programa TRIM Enabler. Ele não é extremamente necessário para o funcionamento do sistema, mas como o próprio nome sugere, ele ativa o TRIM em discos SSD não-oficiais (não originais da Apple). Isso aumenta consideravelmente a velocidade de gravação em disco e prolonga a vida útil da peça.

[Clique aqui](https://www.cindori.org/software/trimenabler/) para acessar o site de download. Há uma versão paga e uma gratuita, mas a gratuita já serve para o que queremos. Nem precisa instalar, basta abrir e executar o programa.


# Inicialização

Com a ajuda do Multibeast, instale o bootloader Chimera no disco principal onde você instalou o Mac OS X. Depois, edite o arquivo de configuração com o seguinte comando no Terminal do sistema (vai precisar inserir a senha de administrador do próprio usuário, configurada durante a instalação):

    sudo vim /Extra/org.chameleon.Boot.plist

O conteúdo deverá ser o seguinte:

<script src="https://gist.github.com/victor-torres/e2cdb52e415bab69e7abbeb5f7480ef0.js"></script>


# Corrigindo problemas

Se por acaso algum problema acontecer durante a instalação do OS X, inicie o instalador com a opção `-v`. Isso quer dizer para ele iniciar em modo verboso e emitir um registro de todo e qualquer erro que acontecer na interface de vídeo. Dessa forma você poderá identificar o problema pesquisando em fóruns e blogs na Internet, como por exemplo os famosos Kernel Panics.
