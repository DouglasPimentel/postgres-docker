# Postgres e pgAdmin com Docker

Este repositório contém os arquivos de configuração necessários para criar um ambiente de desenvolvimento local com Postgres e pgAdmin utilizando Docker.

Images do Docker utilizadas:
- [Postgres](https://hub.docker.com/_/postgres)
- [pgAdmin](https://hub.docker.com/r/elestio/pgadmin)

## Requisitos

Docker Desktop instalado e em funcionamento. Se você ainda não tem o Docker instalado, você pode seguir as instruções oficiais de instalação para a sua plataforma: [Docker Desktop](https://www.docker.com/products/docker-desktop/).

## Preparando o ambiente

1. Verifique se o Docker está em execução. Você pode verificar isso procurando pelo ícone do Docker na barra de tarefas. Se não estiver rodando, inicie o Docker Desktop.
   
2. Abra seu terminal e execute o comando para criar uma rede chamada **local-network**:

```bash
  docker network create local-network
```

3. Clone o repositório.

```bash
   git clone https://github.com/DouglasPimentel/postgres-docker.git
```

4. Entre no diretório do projeto.

```bash
   cd postgres-docker
```

5. Crie um .env na raiz do diretório com as seguintes variáveis:

```bash
  DATABASE_URL=postgres://postgres:postgres@localhost:5432/postgres
  POSTGRES_USER=postgres
  POSTGRES_DB=postgres
  POSTGRES_PASSWORD=postgres
  PGADMIN_DEFAULT_EMAIL=user@localhost.com
  PGADMIN_DEFAULT_PASSWORD=admin
  PGADMIN_LISTEN_PORT=8080
```

6. Execute os containers com Compose:

```bash 
   docker compose --env-file=.env up -d
```

Após rodar o comando, o Docker vai fazer o download das imagens, e iniciar os containers. Para testar se o serviço do pgAdmin está funcionando, acesse http://localhost:8080 no seu navegador. Haverá uma tela de autenticação, você deverá informar o email e senha que você definiu no arquivo .env.
