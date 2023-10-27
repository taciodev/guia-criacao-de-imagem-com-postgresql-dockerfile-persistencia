# Guia de Criação de uma Imagem do PostgreSQL com Persistência de Dados Usando Dockerfile

Neste guia, você aprenderá como criar uma imagem personalizada do PostgreSQL e garantir a persistência dos dados do banco usando um Dockerfile. Siga os passos abaixo para realizar esta tarefa.

## Pré-requisitos

Certifique-se de que os seguintes pré-requisitos estejam instalados no seu sistema:

1. Docker

## Instalação

### Passo 1: Crie um diretório para o Dockerfile

Primeiro, crie um diretório onde você irá armazenar o Dockerfile e os arquivos necessários. Por exemplo:

```bash
mkdir postgres_docker
cd postgres_docker
```

### Passo 2: Crie um Dockerfile

Dentro do diretório postgres_docker, crie um arquivo chamado Dockerfile:

```bash
touch Dockerfile
```

### Passo 3: Configure o Dockerfile

Cole o seguinte conteúdo no arquivo Dockerfile e salve as alterações:

```bash
# Use a imagem oficial do PostgreSQL como base
FROM postgres:latest

# Defina uma variável de ambiente para a senha do PostgreSQL (altere conforme necessário)
ENV POSTGRES_PASSWORD=sua_senha

# Exponha a porta padrão do PostgreSQL
EXPOSE 5432
```

Este Dockerfile utiliza a imagem oficial do PostgreSQL como base e define a senha do PostgreSQL através de uma variável de ambiente. A porta 5432 é exposta para a comunicação com o banco de dados.

### Passo 4: Construa a Imagem

No mesmo diretório do Dockerfile, construa a imagem personalizada com o seguinte comando:
    
```bash
docker build -t minha_imagem_postgres .
```

Substitua **minha_imagem_postgres** pelo nome que você deseja para a sua imagem.

### Passo 5: Execute o PostgreSQL

Agora que a imagem personalizada foi criada, execute o PostgreSQL com o Docker:

```bash
docker run -d --name meu_postgres -p 5432:5432 minha_imagem_postgres
```

### Passo 6: Acesse o PostgreSQL

Você pode acessar o PostgreSQL usando um cliente PostgreSQL (por exemplo, psql) e se conectar à porta 5432 do servidor local.

### Passo 7: Persista os Dados

Os dados do PostgreSQL agora estão sendo persistidos no volume padrão do contêiner. Mesmo após parar e remover o contêiner, os dados ainda estarão disponíveis no volume.

### Passo 8: Interrompa e Remova o Contêiner (Opcional)

Se precisar interromper e remover o contêiner PostgreSQL, execute o seguinte comando:

```bash
docker stop meu_postgres
docker rm meu_postgres
```

### Passo 9: Remova a Imagem (Opcional)

Se desejar remover a imagem personalizada que você criou, execute o seguinte comando:

```bash
docker rmi meu_postgres
```
Agora você criou com sucesso uma imagem personalizada do PostgreSQL, executou-a e persistiu os dados do banco usando Docker.