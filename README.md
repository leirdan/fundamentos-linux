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
-   **whatis**: mostra a função de determinado comando.
-   **whoami**: retorna o usuário que está logado.
-   **cal**: exibe o calendário do presente mês.
-   **date**: mostra o dia da semana, a hora que o comando foi dado, o mês, ano e etc.
-   **clear**: limpa o terminal poluído.
-   **exit**: desloga do terminal.

### 3.1 TRUQUES

-   Digitar "!!" no terminal faz seu último comando digitado ser executado novamente.

---

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

-   **more**: Usado com uma Pipe após o "cat", separa o arquivo em partes e não imprime tudo logo no terminal. Assim, você pode visualizá-lo por partes e melhor. Exemplo de uso: **cat fundamentos-linux.md | more**. -**less**: Com a mesma função do "more" e a mesma sintaxe, a diferença é que nesse caso é possível rolar pelo arquivo como se fosse um documento.

    ### 4.4 OUTROS COMANDOS

-   **find**: Utilizado para procurar arquivos dentro de um determinado diretório. Exemplo de uso: **find Downloads -iname if.pdf** (sintaxe: find [nomeDiretorio] [opções] [nomeArquivo]). Opções comuns: "find . -name '\*.txt'" (procura no diretório corrente todos os arquivos com extensão .txt), "find / -iname hostname -type f" (procura a partir da pasta raiz pelo arquivo 'hostname', independente se está escrito com letras maiusculas ou minusculas; -type f especifica que o objeto a ser buscado é um arquivo, "file").
