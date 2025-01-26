# Guia Rápido de Docker

Este guia fornece uma introdução rápida aos comandos e conceitos básicos de Docker, com foco na execução de contêineres, gerenciamento de contêineres, operações com arquivos e criação de um contêiner MySQL.

## Executando um Contêiner

### Baixar uma imagem e executar um contêiner
- `docker pull ubuntu`  
  Baixa a imagem do Ubuntu do Docker Hub.

- `docker run ubuntu`  
  Executa o contêiner do Ubuntu em modo interativo, mas sem manter o terminal ativo.

- `docker run ubuntu sleep 10`  
  Executa um contêiner do Ubuntu e faz ele "dormir" por 10 segundos, encerrando automaticamente após.

- `docker run ubuntu sleep 1500`  
  Executa um contêiner do Ubuntu e faz ele "dormir" por 1500 segundos.

- `docker stop [id]`  
  Para o contêiner em execução identificado pelo `[id]`.

- `docker run --help`  
  Exibe informações sobre o comando `docker run` e suas opções.

- `docker run -it ubuntu`  
  Executa o contêiner do Ubuntu de forma interativa, permitindo o uso de um terminal dentro do contêiner.

## Executando Aplicações no Contêiner

### Rodando o contêiner em modo "detached"
- `docker run -dti ubuntu`  
  Executa o contêiner em segundo plano (modo "detached") e permite acesso interativo.

- `docker exec -it [id ou nome] /bin/bash`  
  Acessa o contêiner em execução com um terminal interativo, permitindo executar comandos dentro do contêiner.

## Excluindo e Nomeando Contêineres

### Parando, removendo e renomeando contêineres
- `docker stop [id]`  
  Para o contêiner com o identificador `[id]`.

- `docker rm [id]`  
  Remove o contêiner com o identificador `[id]`.

- `docker rmi [imagem]`  
  Remove a imagem com o nome `[imagem]` do Docker.

- `docker run -dti --name Ubuntu-A ubuntu`  
  Executa o contêiner com o nome `Ubuntu-A`, permitindo acesso interativo e em modo "detached".

## Copiando Arquivos para o Contêiner

### Copiando arquivos para dentro do contêiner
- `docker exec -ti Ubuntu-A /bin/bash`  
  Acessa o contêiner `Ubuntu-A` com um terminal interativo.

- `docker exec Ubuntu-A mkdir /destino/`  
  Cria o diretório `/destino/` dentro do contêiner `Ubuntu-A`.

- `docker exec Ubuntu-A ls -l /`  
  Lista os arquivos e diretórios no diretório raiz dentro do contêiner `Ubuntu-A`.

- `nano Arquivo.txt`  
  Cria ou edita um arquivo `Arquivo.txt` com o editor de texto `nano`.

- `docker cp arquivo.txt Ubuntu-A:/aula/`  
  Copia o arquivo `arquivo.txt` do sistema host para o diretório `/aula/` dentro do contêiner `Ubuntu-A`.

### Copiando Arquivos do Contêiner

- `docker cp Ubuntu-A:/destino/Meuzip.zip Zipcopia.zip`  
  Copia o arquivo `Meuzip.zip` do contêiner `Ubuntu-A` para o sistema host com o nome `Zipcopia.zip`.

## Criando um Contêiner MySQL

### Executando MySQL em um Contêiner Docker
- `docker pull mysql`  
  Baixa a imagem do MySQL do Docker Hub.

- `docker run -e MYSQL_ROOT_PASSWORD=Senha123 --name mysql-A -d -p 3306:3306 mysql`  
  Executa um contêiner do MySQL com a senha `Senha123` para o usuário root, nomeando o contêiner como `mysql-A` e expondo a porta 3306.

- `docker exec -it mysql-A bash`  
  Acessa o contêiner `mysql-A` com um terminal interativo.

- `mysql -u root -p --protocol=tcp`  
  Acessa o MySQL dentro do contêiner usando o protocolo TCP.

- `CREATE DATABASE aula;`  
  Cria um banco de dados chamado `aula` dentro do MySQL.

- `show databases;`  
  Exibe todos os bancos de dados disponíveis no MySQL.

- `docker inspect mysql-A`  
  Exibe informações detalhadas sobre o contêiner `mysql-A`.

## Conclusão

Este guia cobre operações essenciais de Docker, como execução de contêineres, manipulação de arquivos, e como configurar e gerenciar um contêiner MySQL. Para mais detalhes sobre outros comandos e opções, consulte a documentação oficial do Docker.
