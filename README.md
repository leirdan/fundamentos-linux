## FUNDAMENTOS DE GNU/LINUX

## 1. INTRODUÇÃO

-   Linux é, na verdade, o Kernel (núcleo) do sistema operacional, que faz a comunicação entre o hardware e o sistema operacional.
-   Desenvolvido por inúmeros desenvolvedores e instituições atualmente.
-   É multitarefa (realiza muitas tarefas simultaneamente) e multiusuário (permite a criação de várias contas e que estas possam acessar os mesmos arquivos).
-   Existe todo o tipo de distribuições linux espalhados por aí: são "versões" do Linux que contém características próprias de configurações, interface, entre diversas outras especifidades. Ex.: Ubuntu, Fedora, Manjaro, Red Hat, Kali, etc.

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
-   **clear**: limpa o terminal poluído.
-   **exit**: desloga do terminal.

### 3.1 TRUQUES

-   Digitar "!!" no terminal faz seu último comando digitado ser executado novamente.

---
