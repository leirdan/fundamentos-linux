# FUNDAMENTOS DE GNU/LINUX

## 1. INTRODUÇÃO

-   Linux é, na verdade, o **Kernel** (núcleo) do sistema operacional, que faz a comunicação entre o hardware e o sistema operacional. O sistema operacional onde o kernel Linux atua é, quase sempre, o **GNU**, nascido do Projeto GNU, o qual busca criar um sistema operacional livre, composto apenas de softwares livres.
-   É desenvolvido por inúmeros desenvolvedores e instituições atualmente.
-   É multitarefa (realiza muitas tarefas simultaneamente) e multiusuário (permite a criação de várias contas e que estas possam acessar os mesmos arquivos).
-   Existe todo o tipo de distribuições Linux espalhados por aí: são "versões" do GNU/Linux que contém características próprias de configurações, interface, entre diversas outras especifidades. Ex.: Ubuntu, Fedora, Manjaro, Red Hat, Kali, etc.

## 2. SHELL

-   O Terminal do Linux é uma ferramenta de linha de comando onde é possível executar comandos e programas para realizar determinadas tarefas (criação de pastas e arquivos, criação de usuários, download de pacotes, etc.)
-   O objetivo é facilitar e automatizar tarefas para os profissionais que o utilizam.
-   Ao entrar no shell, as linhas são antecedidas pelas palavras "leirdan@lunix:~$" - no meu caso.
-   Isso representa, respectivamente, o usuário logado (leirdan), o nome da máquina (lunix), o diretório pessoal (~, a pasta "home" do diretório raiz) e que você está logado como usuário normal($).

## 3. COMANDOS SIMPLES

SINTAXE DOS COMANDOS: [comando] [opções] [argumento]. Exemplo: rm (comando) -r (opção) meusProjetos (argumento)

-   **pwd**: traz a saída do caminho onde o usuário está no momento. Ex. de saída: /home/leirdan
-   **ls**: lista todos os diretórios e arquivos de um determinado caminho. Opções comuns: "ls -a" (lista também arquivos ocultos), "ls -l" (lista arquivos, permissões e outros detalhes), "ls -r" (lista os arquivos em ordem invertida).
-   **cd**: faz a troca entre diretórios. Ex.: **cd Documentos** (sai do diretório atual para o diretório Documentos). Outras opções: "cd .." retorna para o diretório superior (se estiver dentro de uma pasta em 'Documentos', ao executar esse comando, você retornará para o diretório Documentos), "cd -" retorna para o diretório que estava antes, "cd /" vai para o diretório raiz, "cd ~" volta para o seu diretório pessoal.
-   **mkdir**: cria um novo diretório e nomeia-o. Ex.: **mkdir 'Minhas Atividades'** (cria o diretório 'Minhas Atividades' no diretório onde você está).
-   **rm**: remove um diretório ou arquivo. Ex.: **rm -r atividades**. Opções comuns: "rm -r" (o -r é usado para remover diretórios), "rm -rf" (remove diretórios e seus arquivos forçadamente), "rm -i" (remove mas pergunta antes de cada remoção)
-   **mv**: move ou renomeia arquivos/diretórios. Para renomear: mv [nomeArquivo] [novoNomeArquivo]; para mover: mv [nomeArquivo] /[caminhoDiretorioDesejado] (coloca-se o / para saber que é um diretório já existente e não um novo nome para o arquivo)
-   **touch**: cria arquivos vazios. Ex.: **touch index.js**.
-   **cp**: copia determinado arquivo para outro diretório. Ex.: **cp index.js /home/leirdan** (copia o arquivo "index.js" para o diretório /home/leirdan).
-   **history**: traz na saída um histórico de todos os comandos usados no terminal.
-   **whatis**: mostra a função de determinado comando. Ex.: **whatis ls**.
-   **whoami**: retorna o usuário que está logado.
-   **cal**: exibe o calendário do presente mês.
-   **date**: mostra o dia da semana, a hora que o comando foi dado, o mês, ano e etc.
-   **clear**: limpa o terminal poluído.
-   **exit**: desloga do terminal.

### 3.1 TRUQUES

-   Digitar "!!" no terminal faz seu último comando digitado ser executado novamente.

### 3.2 ESPECIAL

-   Digitar a palavra **sudo** antes de qualquer outro comando (como em **sudo pacman -S nodejs**, um comando de instalação a partir do gerenciador de pacotes "Pacman") faz o comando ser executado pelo usuário em um "nível mais elevado", como **superusuário**, ou **root**.
-   Essa palavra é necessária muitas vezes para executar comandos com algum tipo de risco, adentrar certos diretórios protegidos, definir permissões, entre diversas outras tarefas. Isso porque o usuário root tem todos os privilégios de fazer o que quiser com a máquina. Então, tome cuidado.
-   Para que o comando seja executado a partir do "sudo", você precisa informar a sua senha de usuário antes de executar.

## 4. REDIRECIONAMENTO E MANIPULAÇÃO DE ARQUIVOS

-   Ao criar um arquivo vazio com o comando _touch_, pode-se usar o editor de texto "**nano**" para inserir conteúdo diretamente no arquivo
    e preenchê-lo.
-   O nano é um editor de textos extremamente simples (é por onde estou escrevendo esse arquivo), não sendo nada complexo como o editor "**vi**" (muito adorado por diversos usuários e que serve ao mesmo propósito do nano).
-   Ao escrever um determinado conteúdo dentro do arquivo, basta apenas pressionar _ctrl+o_ e enter para salvar, e _ctrl+x_ para sair do editor.

    ### 4.1. COMANDOS PARA LER ARQUIVOS

-   **cat**: imprime todo o conteúdo de um arquivo (.js, .txt, .md, etc., não importa o formato) no terminal. Opções comuns: "cat -n" exibe o número de linhas do arquivo.
-   **tac**: faz o mesmo que o cat, mas lê o arquivo de baixo para cima.
-   **head**: imprime as 10 primeiras linhas do arquivo. Opções comuns: "head -n 33" exibe as 33 primeiras linhas de um arquivo (é possível alterar o número para imprimir quantas quiser).
-   **tail**: imprime as 10 últimas linhas do arquivo. Opções comuns: "tail -n 44" exibe as 44 últimas linhas de um arquivo (também é possível alterar o número de linhas a serem lidas).
-   **file**: retorna o tipo do arquivo lido. Exemplo de uso: **file README.md** (retorna o seguinte: "README.md: Unicode text, UTF-8 text, with very long lines (520)").
    ### 4.2 COMANDOS DE REDIRECIONAMENTO
    #### 4.2.1. **Operador >**
-   Atribui a saída de um comando para dentro de um novo arquivo. Ex.: **head -n 5 fundamentos-linux.md > introducao-linux.md**
    -   O comando acima pega, com o comando "head", as 5 primeiras linhas de um arquivo e as envia para um novo arquivo chamado "introducao-linux.md"
-   Ao usar este operador, todo o conteúdo antigo do arquivo é apagado e o novo conteúdo é escrito.

    #### 4.2.2. **Operador >>**

-   Mesmo propósito do ">". A diferença é que este operador **não** sobrescreve o conteúdo anterior. Ele **concatena**.
-   Exemplo: **head fundamentos-linux.md && tail -n 4 fundamentos-linux.md >> introducao-linux.md**.
    -   O comando acima vai mandar para o arquivo "introducao-linux.md" (criado anteriormente) as 4 últimas linhas das 10 selecionadas pelo comando "head" (engloba apenas o capítulo 2).
    #### 4.2.3. **Operador | (Pipe)**
-   Utilizado para digitar um comando que é executado a partir do resultado do outro. Exemplo de uso: **cat atividade-quimica.txt | grep Aldeídos**.

    -   A expressão acima lê o arquivo 'atividade-quimica.txt', e o comando "grep" busca nesse arquivo linhas com a palavra "Aldeídos" e as imprime no shell.

    #### 4.2.4 **Operador &**

-   Utilizado para executar um comando seguido do outro. Exemplo de uso: **cat teste1 & cat teste2**.

    -   Aqui, o shell executa o comando da esquerda primeiro, e só depois executa o da direita; por isso, sua impressão será dividida no terminal por linhas.

    #### 4.2.5 **Operador &&**

-   Utilizado para executar dois comandos paralelamente. Exemplo de uso: **cat teste1 && cat teste2**.
    -   Nesse exemplo, o shell vai imprimir simultaneamente os dois arquivos no terminal sem nenhuma separação.
-   Outro exemplo comum: **mkdir diretorioX && cd diretorioX**; o diretório foi criado e rapidamente o usuário já entra nele.

    ### 4.3 COMANDOS DE PAGINAÇÃO

-   **more**: Usado com uma Pipe após o "cat", separa o arquivo em partes e não imprime tudo logo no terminal. Assim, você pode visualizá-lo por partes e melhor. Exemplo de uso: **cat fundamentos-linux.md | more**.

-   **less**: Com a mesma função do "more" e a mesma sintaxe, a diferença é que nesse caso é possível rolar pelo arquivo como se fosse um documento.

    ### 4.4 OUTROS COMANDOS

-   **find**: Utilizado para procurar arquivos dentro de um determinado diretório. Exemplo de uso: **find Downloads -iname if.pdf** (sintaxe: find [nomeDiretorio] [opções] [nomeArquivo]). Opções comuns: "find . -name '\*.txt'" (procura no diretório corrente todos os arquivos com extensão .txt), "find / -iname hostname -type f" (procura a partir da pasta raiz pelo arquivo 'hostname', independente se está escrito com letras maiusculas ou minusculas; -type f especifica que o objeto a ser buscado é um arquivo, "file").

## 5. DIRETÓRIOS LINUX DENTRO DA PASTA RAIZ (/)

-   **/**bin**/**: guarda os binários (executáveis) do Linux.
-   **/**boot**/**: arquivos do sistema de boot, para inicializar o sistema.
-   **/**dev**/**: contém arquivos dos dispositivos que se conectam ao hardware, como drivers de rede, teclado, som, etc.
-   **/**etc**/**: arquivos de configuração e personalização do sistema, como nome do computador.
-   **/**home**/**: pasta que guarda os usuários comuns e seus diretórios.
-   **/**lib**/**: bibliotecas essenciais do sistema e módulos do Kernel (núcleo do S.O)
-   **/**media**/** e **/**mnt**/**: arquivos de montagem de dispositivos (hd externo, pen-drive, etc.)
-   **/**opt**/**: diretório que armazena programas não-oficiais da distribuição instalados pelo usuário; ao guardar programas aqui, eles são impedidos de agirem contra o seu S.O para ataques maliciosos, por exemplo.
-   **/**sbin**/**: armazena executáveis que representam comandos administrativos (como "shutdown").
-   **/**srv**/**: guarda dados de serviços fornecidos pelo sistema.
-   **/**tmp**/**: área que guarda arquivos temporários
-   **/**usr**/**: guarda os arquivos dos usuários do sistema, seus programas e binários também.
-   **/**var**/**: diretório com arquivos variáveis gerados pelos programas do sistema, como logs e cache.
-   **/**root**/**: diretório do usuário **root** (o superusuário, tem poder total sobre o sistema).
-   **/**proc**/**: controlado pelo Kernel, armazena dados de memória, informações de CPU, entre outras.

### 5.1 ALGUNS DIRETÓRIOS DE INFORMAÇÕES IMPORTANTES

-   **/proc/cpuinfo**: guarda dados sobre o hardware da máquina, como número de processadores, suas versões, tamanho de cache e etc.
-   **/proc/meminfo**: dados sobre a memória RAM da máquina (total, tamanho da memória SWAP, memória ativa e inativa, etc.)
-   **/etc/passwd**: guarda todos os usuários do sistema (root, daemon, bin, mysql, eu mesmo, etc.), mostrando nome dos usuários, a pasta de cada um, onde executam os comandos, etc.
-   **etc/group**: guarda todos os grupos que existem no sistema e seus GID.

### 5.2 COMANDOS DE SISTEMA

-   **lspci**: retorna todos os hardwares conectados via PCI.
-   **lsusb**: retorna todos os dispositivos USB.
-   **lscpu**: traz todas as informações de CPU (processador) de forma bem organizada.
-   **lshw**: exibe a lista de todos os hardwares que compõem a máquina.
-   **lshw --short**: mostra a mesma lista gerada pelo comando acima, mas de forma curta e mais resumida.
-   **arch** ou **uname -m**: mostra o tipo de arquitetura do sistema (64 bits, 32 bits, entre outros).
-   **uname**: mostra o nome do Kernel que a distribuição usa (com frequência, Linux). Outra opção: "uname -r" mostra a versão do Kernel usado.
-   **free**: mostra todos os dados de memória RAM e SWAP do sistema; o SWAP é um tipo de memória criado a partir de uma partição no próprio disco rígido que serve como "memória virtual", uma alternativa para que caso a memória RAM fique cheia o computador não trave por inteiro.
-   **du**: retorna o tamanho do espaço que um determinado diretório ocupa. Exemplo de uso: **du -h ~** retorna o espaço total e que cada arquivo ocupa no diretório pessoal, seguido da unidade de medida (Kb, Mb, Gb).
-   **reboot**: reinicia a distribuição Linux.
-   **shutdown**: desliga a distribuição Linux. Inclui as opções "-h" (halt, interrompe tudo e desliga a máquina), "-p" (power-off, mesma função do halt, além de se desligar da energia) e outras. Além disso, é importante definir o tempo após a opção ("now", "09:00", etc.)

## 6. FUNDAMENTOS DE REDES

-   "Rede de computadores" é um conjunto de equipamentos interligados a fim de trocarem informações e compartilharem recursos, como impressoras, softwares, arquivos, etc.
-   Denomina-se "nó" algum equipamento que está integrado dentro da rede (computador, celular, roteador, etc.).
-   Existem divisões de rede baseada no seu alcance: a 1) **'World Area Network'**, rede WAN, de área mundial e geograficamente distribuída; a 2) **'Metropolitan Area Network'**, rede MAN, que conecta desde redes locais em uma área metropolitana até redes de duas cidades; e 3) **'Local Area Network'**, rede LAN, uma rede que está dentro de apenas um local e abastece apenas este.

### 6.1 PROTOCOLOS

-   São a "linguagem" usada pelos dispositivos de uma rede para que eles consigam se entender.
-   São exemplos de protocolos:
    -   **IP**: protocolo de Internet, gera o Endereço IP, que é uma sequência de números que identifica seu dispositivo na rede (local e mundial);
        -   **Importante** - seu endereço IP local e mundial são diferentes, e podem ser dinâmicos (mutáveis) ou fixos.
    -   **ICMP**: protocolo que provém mensagens de controle na comunicação entre os nós; usado para determinar se os dados estão chegando ao destino;
    -   **DNS**: protocolo responsável por atribuir nomes a endereços IP (e vice-versa) e manter uma tabela com esses dados; por exemplo, atribuir o IP 192.168.175.32 a determinado site da internet.

### 6.2 INTERFACES DE REDE

-   São as responsáveis por estabelecer a comunicação entre dispositivos em uma rede. Podem ser desde softwares até hardwares (como uma placa de rede).
-   No GNU/Linux, as interfaces estão no diretório **/dev**, e são criadas pelos softwares de forma dinâmica (quando requisitado).
-   Exemplos são a interface **eth0**, que representa uma placa de rede Ethernet, e a interface de **loopback**, criada para que o usuário consiga fazer conexões consigo mesmo sem interferir na rede (_importantíssima quando estamos desenvolvendo uma aplicação Web com Node.js por exemplo, onde o servidor não interfere na rede_). Por padrão, a interface loopback tem o endereço IP 127.0.0.1.

### 6.3 COMANDOS DE REDES

-   Importante: para executar esses comandos, instale o pacote **net-tools** na sua distribuição usando o seu gerenciador de pacotes (apt para Ubuntu, pacman para Manjaro, entre outros).
-   **ifconfig**: exibe todas as interfaces de rede do computador e informações como endereço IPv4 na rede local, máscara de sub rede, endereço IPv6, endereço MAC (da placa de rede, fixa) e outras. As minhas são "wlp0s20f3", uma interface de rede wireless (sem fio), e "lo", a interface loopback.
-   **hostname -I** & **hostname -i**: mostra o endereço IP da máquina da rede e o endereço da interface de rede loopback, respectivamente.
-   **who**: retorna o usuário que está usando o computador e quando ele entrou.
-   **ping [endereçoIpOuNomeDoHost]**: comando que faz parte do protocolo ICMP (enviando mensagens de teste para outro host para testar a conexão). Exemplo de uso: **ping www.google.com**.
-   **dig**: traz informações de DNS (protocolo que atribui nome a endereços IP). Exemplo de uso: **dig www.google.com** (traz, entre outras informações, o endereço IP correspondente ao nome "www.google.com"). Para saber apenas o endereço IP do outro host, usa-se "dig [nomeHost] +short".
-   **traceroute**: imprime no terminal uma lista de cada host que é percorrido até chegar num host específico, como o do Google.
-   **whois**: comando que traz muitas informações (não apenas de rede) sobre determinado domínio, como "whois youtube", "whois netflix"...
-   **finger**: informa todas as informações do usuário que está logado na máquina.

## 7. CONTROLE DE USUÁRIOS, GRUPOS E PERMISSÕES

-   Existem dois tipos de usuário no Linux, basicamente: o usuário normal e o usuário **root** (ou superusuário), este que é capaz de realizar qualquer operação no sistema operacional, pois tem mais privilégios que todos os outros.
-   Ao criar um usuário comum, é também criado um grupo com o mesmo nome e identificador dele. Por exemplo, ao criar o usuário "Lutz" que vem com o UID (id de usuário) 1003, cria-se também um grupo chamado "Lutz" com o GID (id de grupo) 1003.
    -   Os identificadores de usuário (UID) e de grupo (GID) são gerados automaticamente pelo sistema na criação de novos usuários/grupos; os números destinados a esses identificadores são sempre igual a 1000 ou maior, pois os ID's anteriores são reservados ao sistema (número 1 ao 999).
-   Grupos são importantes para organizar os usuários e definir as permissões destes de forma mais fácil.

-   Importante: apenas usuários root podem realizar a maioria dos seguintes comandos. Para poder executá-los, insira, antes de cada comando, a palavra **sudo** para obtenção desses privilégios de superusuário (enquanto usuário normal). Outra opção é simplesmente digitar **sudo su -** e trocar para o usuário root para realizar essas operações de forma direta.

### 7.1 COMANDOS DE USUÁRIOS

-   **adduser** ou **useradd**: adiciona um novo usuário no sistema. Exemplo de uso: **adduser gilmour**. É possível adicionar também diretamente um novo usuário a um grupo inserindo o nome do grupo logo após o do usuário. Exemplo: **useradd gilmour pinkfloyd** - gilmour: usuário; pinkfloyd: grupo.
-   **su**: troca entre os usuários do sistema. Exemplo de uso: **su gilmour**. Para fazê-lo, você deve digitar a senha do usuário para o qual deseja trocar; você será encaminhado para o diretório pessoal desse usuário, e o diretório do usuário no qual estava logado fica "inacessível" para este novo.
-   **passwd**: altera a senha de um usuário. Exemplo de uso: **passwd gilmour**. A nova senha deve ser **segura** - não coloque senhas fáceis ou pessoais, como o nome de alguém da sua família; misture letras maiúsculas e minúsculas, números e caracteres especiais.
-   **lastlog**: exibe informações de login de todos os usuários do sistema.
-   **last**: exibe uma listagem das entrada e saídas do usuário logado no sistema.
-   **logname**: retorna o nome do usuário logado atualmente.
-   **id**: imprime todos os identificadores do usuário logado (uid, gid e a quais grupos ele pertence).
-   **userdel**: remove o usuário desejado. Para remover sua pasta pessoal também, adiciona-se a opção "-r". Exemplo de uso: **userdel -r gilmour**.

### 7.2 COMANDOS DE GRUPOS

-   **groups**: exibe o nome dos grupos no qual o usuário logado faz parte.
-   **addgroup** ou **groupadd**: cria um novo grupo no sistema. Exemplo de uso: **groupadd phantasystar**.
-   **gpasswd -a**: permite associar um usuário já existente a um grupo. Exemplo de uso: **gpasswd lutz phantasystar** - lutz: usuário; phantasystar: grupo. Com a opção "-d", é possível remover o usuário de um grupo. Exemplo: **gpasswd -d rockman phantasystar**.
-   **groupdel**: remove um grupo. Exemplo de uso: **groupdel revolver**.

### 7.3 COMO FUNCIONAM AS PERMISSÕES

-   As permissões de diretórios e arquivos servem para definir o que cada usuário pode ou não fazer com tal diretório/arquivo. As permissões são 3: **read** (ler), **write** (escrever) e **execution** (executar).
    -   Na prática, serve para **restringir o acesso** de determinados usuários em certos lugares. Por exemplo, impedir que um usuário recém-criado possa acessar a pasta pessoal de um outro usuário.
-   Permissões de um documento ou pasta podem ser verificadas a partir do comando **ls -l**, que tem a seguinte saída: **-rw------- 1 leirdan leirdan 28356 nov 16 16:09 data-machine**
-   A linha acima é apenas um dos arquivos do meu diretório pessoal. Foram listadas várias informações, como o usuário que criou (leirdan), o grupo que está associado (leirdan), a data de criação (nov 16) e etc., mas vamos focar nessas letrinhas e tracinhos do começo.
    -   Cada espaço de **-rw-------** representa algo:
        -   o 1º espaço, se estiver preenchido com um "d", indica que é um diretório. Como está vazio, indica que é um **arquivo**.
        -   do 2º ao 4º espaço são as permissões de **usuário** (o que eu posso fazer nesse arquivo, o Owner). O espaço com um "r" indica que esse arquivo pode ser **lido** por mim, e o espaço com "w" indica que eu posso **escrevê-lo**. Contudo, o 4º espaço não está preenchido com um "x", indicando que eu **não posso executar esse arquivo**.
        -   do 5º ao 7º espaço são as permissões de **grupo** (o que usuários do mesmo grupo que o meu podem fazer com esse arquivo). Como percebemos, nenhum dos espaços está preenchido, logo, os usuários do mesmo grupo que eu **não podem ler, escrever ou executar esse arquivo**.
        -   do 8º ao 10º espaço são as permissões de **outros usuários** (que não estão no mesmo grupo que eu). Novamente, esses usuários **não tem nenhuma permissão para mexer nesse arquivo**.

### 7.4 COMANDOS DE MANIPULAÇÃO DE PERMISSÕES

-   **chmod**: O comando principal para mudar as permissões de arquivos e diretórios. Existem alguns métodos para fazê-lo:
    -   **Modo Octal**: Um conjunto de três números que é passado ao comando "chmod". Cada um dos números representa uma permissão para o usuário logado (Owner), o grupo e outros usuários, respectivamente.
        -   0: sem permissões;
        -   1: permissão de execução, apenas;
        -   2: permissão de escrita, apenas;
        -   3: permissão de execução e escrita, apenas;
        -   4: permissão de leitura, apenas;
        -   5: permissão de leitura e execução, apenas;
        -   6: permissão de leitura e escrita, apenas;
        -   7: todas as permissões.
        -   Exemplo: **chmod 755 Downloads** atribui todas as permissões ao Owner e permissão de leitura e execução tanto ao grupo quanto a outros usuários no diretório Downloads.
    -   **Modo Convencional**: Aqui, é passado explicitamente as permissões e para quais usuários elas vão. Exemplos de uso:
        -   **chmod u=rwx,g=rx,o=rx Downloads** - tem o mesmo efeito do último exemplo. O Owner tem todas as permissões, e grupo e outros usuários tem apenas as permissões de ler e executar.
        -   **chmod u+x heated.txt** - adiciona a permissão de execução ao arquivo "heated" para o Owner.
        -   **chmod g+w,o+r lucozade.txt** - adiciona ao arquivo "lucozade" a permissão de escrever para o grupo e a permissão de ler para outros usuários.
        -   **chmod -R o-r meteora** - retira a permissão de ler os arquivos do diretório "meteora".

## 8. COMPACTAÇÃO, DESCOMPACTAÇÃO E ARQUIVAMENTO

-   Compactadores são softwares que fazem a diminuição do tamanho de um arquivo/diretório muito grande para ser enviado por e-mail, por exemplo.
-   Cada arquivo/diretório compactado é identificado por uma extensão, que é atribuida a este pelo compactador para que no novo dispositivo ele possa ser descompactado somente por aquele compactador. Extensões comuns são a .zip e .rar.

### 8.1 COMPACTADORES

-   Nos sistemas GNU/Linux, temos as seguintes opções:
-   **gzip**: muito usado e uma taxa excelente de compactação. Exemplo de uso: **gzip mayhem.txt**. Para descompactar use: **gunzip mayhem.txt.gz**. Opções comuns: "gzip -9 mayhem.txt" usa a compactação máxima possível.
-   **zip**: presente tanto no Windows quanto nos sistemas GNU/Linux. Exemplo de uso: **zip projetonode.zip projetonode** (argumento 1 é o nome do novo arquivo compactado e o argumento 2 é o arquivo/diretório a ser compactado). Para descompactar use: **unzip projetonode.zip**
-   **bzip2**: mais atual que os anteriores. Exemplo de uso: **bzip2 traitor**. Para descompactar use: **bzip2 -d traitor.bz2**

### 8.2 ARQUIVADORES

-   Basicamente, junta vários arquivos em um só e pode ser usado aliado a um compactador para armazenar estes arquivos compactados.
-   Nos sistemas GNU/Linux, temos as seguintes opções:
-   **tar**: extremamente popular, manipulando até arquivos de sistema. Exemplo de uso: **tar -cf normanrockwell.txt.rar normanrockwell.txt mac.txt california.txt** - usamos o "tar" para arquivar três arquivos .txt diferentes em um só. Após isso, podemos compactar esse arquivo com algum compactador.
    -   Para descompactar um arquivo .tar compactado pelo gzip, por exemplo, usaremos: **tar -xvf normanrockwell.txt.rar.gz**. Não funciona com o compactador zip - é necessário descompactar primeiro para deixar apenas o arquivo .tar.

## 9. DAEMONS

-   Daemons são, geralmente, processos que são inicializados com o sistema e são executados em segundo plano até o desligamento do PC.
    -   Um exemplo é o daemon **"systemd"** que inicializa o sistema e ativa diversos outros processos por meio de outros daemons.
-   Alguns serviços oferecidos pelo Systemd incluem:

    -   Recursos de **paralelização** (inicializa diversos processos de uma só vez);
    -   Inicializa outros daemons conforme a demanda;
    -   Gerenciamento inteligente de dependência de serviço (um serviço que depende de rede só vai inicializar depois que a rede estiver disponível, por ex.);
    -   Possibilidade de rastrear processos relacionados em conjunto.

### 9.1 UNIDADES DE SERVIÇO

-   Usadas pelo “systemd” para gerenciar diferentes tipos de objetos, existem três tipos principais:
    -   **Unidades de serviço**: têm a extensão “.service”, representam os serviços do sistema e são usadas para acessar os daemons mais frequentes;
    -   **Unidades de soquete**: têm a extensão “.socket” e representam serviços que são ativados por demanda e com menos frequência;
    -   **Unidades de caminho**: têm a extensão “.path” e são usadas para atrasar a ativação de um serviço até que algo aconteça.
-   O comando usado para gerenciar as unidades é o **“systemclt”**, que lista todas as unidades carregadas e ativas.

### 9.2 SYSTEMCTL

-   **systemctl list-units -type=service**: lista todas as unidades de **serviço** do sistema. Para ver as unidades de soquete, caminho e outras, basta trocar o tipo por **socket** ou **path**. Esse comando exibe 4 colunas:
    -   UNIT – nome da unidade;
    -   LOAD – se o systemd analisou e carregou a unidade na memória;
    -   ACTIVE – se a unidade foi iniciada com êxito ou não; estado de alto nível;
    -   SUB – mais detalhes; estado de baixo nível.
-   **systemctl list-units**: lista todas as unidades de serviço carregadas.
-   **systemctl list-units --all**: lista todas as unidades de serviço, ativas ou não.
-   **systemctl list-unit-files**: lista todas as unidades instaladas e os seus status.
-   **systemctl status dbus.service**: lista o status de uma unidade específica. "dbus.service" pode ser substituída por qualquer outra unidade.
-   **systemctl is-active**, **systemctl is-enabled** e **systemctl is-disabled**: lista um status específico de uma unidade.
-   **systemctl --failed**: lista todas as unidades que falharam em iniciar.

### 9.3 CONTROLE DOS SERVIÇOS DO SISTEMA COM SYSTEMCTL

    Importante: "bluetooth.service" é apenas um exemplo. Na prática, basta apenas substituir o nome deste serviço por outro, como "apache.service".

#### 9.3.1 INÍCIO E ENCERRAMENTO

-   **systemctl start bluetooth.service**: inicializa um serviço;
-   **systemctl stop bluetooth.service**: para um serviço.

#### 9.3.2 REINICALIZAÇÃO E RECARREGAMENTO

    A diferença entre as duas operações é que reiniciar altera a ID do processo, enquanto recarregar, não.

-   **systemctl restart bluetooth.service**: reinicia um serviço;
-   **systemctl reload bluetooth.service**: recarrega um serviço;
-   **systemctl reload-or-restart bluetooth.service**: caso não tenha certeza se o serviço tem como ser recarregado.

#### 9.3.3 LISTAGEM DE DEPENDÊNCIAS

    Dependência é quando um serviço depende que outro esteja ativo para poder ser ativado.

-   **systemctl list-dependences bluetooth.service**: lista a hierarquia de serviços a qual o serviço escolhido faz parte.

#### 9.3.4 INCLUIR/REMOVER MÁSCARAS DE SERVIÇOS

    Um sistema pode ter serviços que entram em conflito; quando você mascara um serviço, você impede a ativação desse serviço que entra em conflito com os outros.

-   **systemctl mask bluetooth.service**: mascara o serviço e impede que ele seja iniciado;
-   **systemctl unmask bluetooth.service**: desmascara o serviço mascarado, permitindo que ele seja iniciado.

#### 9.3.5 HABILITAR/DESABILITAR SERVIÇOS NA INICIALIZAÇÃO (NO BOOT)

-   **systemctl enable bluetooth.service**: inicia o serviço na inicialização. Na próxima vez que ligar o computador, esse serviço vai ser ativado;
-   **systemctl disable bluetooth.service**: impede que o serviço selecionado seja inicializado automaticamente no boot.

---
