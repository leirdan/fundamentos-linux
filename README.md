## FUNDAMENTOS DE GNU/LINUX

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
-   **cp**: copia determinado arquivo para outro diretório. Ex.: **cp index.js /home/leirdan**.
-   **history**: traz na saída um histórico de todos os comandos usados no terminal.
-   **whatis**: mostra a função de determinado comando.
-   **whoami**: retorna o usuário que está logado.
-   **cal**: exibe o calendário do presente mês.
-   **date**: mostra o dia da semana, a hora que o comando foi dado, o mês, ano e etc.
-   **clear**: limpa o terminal poluído.
-   **exit**: desloga do terminal.

### 3.1 TRUQUES

-   Digitar "!!" no terminal faz seu último comando digitado ser executado novamente.

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
-   **/**srv**/**: guarda dados de serviços fornecidos pleo sistema.
-   **/**tmp**/**: área que guarda arquivos temporários
-   **/**usr**/**: guarda os arquivos dos usuários do sistema, seus programas e binários também.
-   **/**var**/**: diretório com arquivos variáveis gerados pelos programas do sistema, como logs e cache.
-   **/**root**/**: diretório do usuário **root** (o superusuário, tem poder total sobre o sistema).
-   **/**proc**/**: controlado pelo Kernel, armazena dados de memória, informações de CPU, entre outras.

### 5.1 ALGUNS DIRETÓRIOS DE INFORMAÇÕES IMPORTANTES

-   **/proc/cpuinfo**: guarda dados sobre o hardware da máquina, como número de processadores, suas versões, tamanho de cache e etc.
-   **/proc/meminfo**: dados sobre a memória RAM da máquina (total, tamanho da memória SWAP, memória ativa e inativa, etc.)
-   **/etc/passwd**: guarda todos os usuários do sistema (root, daemon, bin, mysql, eu mesmo, etc.), mostrando nome dos usuários, a pasta de cada um, onde executam os comandos, etc.

### 5.2 COMANDOS DE SISTEMA

-   **lspci**: retorna todos os hardwares conectados via PCI.
-   **lsusb**: retorna todos os dispositivos USB.
-   **lscpu**: traz todas as informações de CPU de forma bem organizada.
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
    -   **ICMP**: protocolo que provém mensagens de controle na comunicação entre os nós; usado para determinar se os dados estão chegando ao destino;
    -   **DNS**: protocolo responsável por atribuir nomes a endereços IP (e vice-versa) e manter uma tabela com esses dados; por exemplo, atribuir o IP 192.168.175.32 a determinado site da internet.

### 6.2 INTERFACES DE REDE

-   São as responsáveis por estabelecer a comunicação entre dispositivos em uma rede. Podem ser desde softwares até hardwares (como uma placa de rede).
-   No GNU/Linux, as interfaces estão no diretório **/dev**, e são criadas pelos softwares de forma dinâmica (quando requisitado).
-   Exemplos são a interface **eth0**, que representa uma placa de rede Ethernet, e a interface de **loopback**, criada para que o usuário consiga fazer conexões consigo mesmo sem interferir na rede (_importantíssima quando estamos desenvolvendo uma aplicação Web com Node.js por exemplo, onde o servidor não interfere na rede_). Por padrão, a interface loopback tem o endereço IP 127.0.0.1.

---
