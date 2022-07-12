# Entendendo o funcionamento do GIT

### SHA1:

 Secure Hash Algorithm

- Algoritmo de interpretação;
- Pega um dado e embaralha ele (criptografa) de modo a gerar um conjunto de caracteres de 40 dígitos.
- Pode servir como uma forma curta de representar um arquivo.
- `openssl sha1 “nome do arquivo”`: criptografa o arquivo em questão

### Objetos fundamentais internos do GIT:

- BLOBS: Um objeto que armazena arquivos e seus meta-dados. Arquivos são armazenados da seguinte forma:
    - tipo de objeto
    - tamanho do objeto
    - \0
    - conteúdo
- TREES: Armazenam Blobs
    - também contém metadados
    - aponta para um blob
    - guarda o nome dos arquivos
    
    ![Untitled](Entendendo%20o%20funcionamento%20do%20GIT%200391555e6ef5437a8093d1847fdf433f/Untitled.png)
    
- COMMITS: Aponta para tudo:
    - trees
    - parentes (diretório do arquivo)
    - autor
    - mensagem
    - timestamp (data e hora dessa criação).

### Chave SSH e Token

Formas de autenticação mais seguras que a password.

CHAVE SSH

- Uma forma de estabelecer uma conexão segura e encriptada entre duas máquinas.
- para criar uma chave:
- `$ ssh-key-gen -t ed25519 -C "bea.matos1978@gmail.com"`
- Inicializando o SSH agent (guarda as chaves) e entregando-o a chave que acabamos de criar.
    1. `eval $(ssh-agent -s)`
    2. `ssh-add id_ed25519`

TOKEN DE ACESSO PESSOAL

- Outra forma de estabelecer uma conexão segura e encriptada entre duas máquinas.
- Geração a partir das configurações do git: Settings > developer settings > personal access token
- dá pra utilizar o protocolo https mesmo pra clonar

### INICIANDO O GIT E CRIANDO UM COMMIT

CONFIGURAÇÕES

- $ git config --global user.email "[bea.matos1978@gmail.com](mailto:bea.matos1978@gmail.com)"
- $ git config --global [user.name](http://user.name/) beamatos03^

GIT INIT

Criação do repositório dentro de um diretório

- `$ cd livro\ receitas/` Indo para o diretório que desejamos usar
- `git init`

GIT ADD

Adicionando um arquivo que ainda está untracked (git ainda não sabe de sua existência, provavelmente pois acabamos de cria-lo) ao repositório

- $ git add *

GIT COMMIT

Salva o código naquele momento, como se fosse um snapshot que registra o estado atual do arquivo.

- $ git commit -m "commit inicial”

GIT STATUS

nos dirá o status do arquivo, se ele está untracked, staged ou modified

### IN