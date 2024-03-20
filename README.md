# Repositório Docker Compose para Treinamento

Este repositório contém dois arquivos Docker Compose para facilitar o ambiente de treinamento com bancos de dados e plataformas de administração em um ambiente Docker Swarm.

## Objetivo

O principal objetivo deste repositório é fornecer um ambiente de treinamento para entender como funciona a rede Docker em um Swarm. Utilizamos Docker Compose para criar e orquestrar serviços, facilitando a demonstração prática das capacidades do Docker Swarm para gerenciar contêineres em um ambiente distribuído.

## Arquivos Docker Compose

### 1. docker-compose-db.yml

Este arquivo Docker Compose inclui a configuração para os bancos de dados usados no treinamento. Atualmente, oferecemos suporte aos seguintes bancos:

- PostgreSQL
- MySQL
- MongoDB

Para iniciar os bancos de dados, utilize o seguinte comando:

```bash
docker stack deploy -c docker-compose-db.yml db
```

### 2. docker-compose-admin.yml

Este arquivo Docker Compose inclui a configuração para plataformas de administração dos bancos de dados. Atualmente, oferecemos suporte às seguintes plataformas:

- Adminer
- phpMyAdmin
- MongoDB Express

Para iniciar as plataformas de administração, utilize o seguinte comando:

```bash
docker stack deploy -c docker-compose-admin.yml admin
```

## Redes Docker

O repositório também inclui a criação de três redes Docker necessárias:

- mongo
- mysql
- postgres

Essas redes são utilizadas para isolar os contêineres dos respectivos bancos de dados. Certifique-se de que essas redes estão criadas antes de iniciar os contêineres.

Para criar as redes, utilize o seguinte comando:

```bash
docker network create -d overlay mongo
docker network create -d overlay mysql
docker network create -d overlay postgres
```

## Como usar

1. Clone este repositório:

```bash
git clone https://github.com/ViniB-A/stack-de-treinamento.git
cd stack-de-treinamento
```

2. Crie as redes Docker necessárias:

```bash
docker network create -d overlay mongo
docker network create -d overlay mysql
docker network create -d overlay postgres
```

3. Inicie os bancos de dados:

```bash
docker stack deploy -c docker-compose-db.yml db
```

4. Inicie as plataformas de administração:

```bash
docker stack deploy -c docker-compose-admin.yml admin
```

Agora, você terá os bancos de dados e as plataformas de administração em execução. Acesse as plataformas de administração pelos seguintes URLs:

- Adminer: [http://localhost:8087](http://localhost:8087)
- phpMyAdmin: [http://localhost:8080](http://localhost:8080)
- MongoDB Express: [http://localhost:8081](http://localhost:8081)

Lembre-se de ajustar as portas conforme necessário e consulte a documentação de cada plataforma para obter informações de login e configuração específicas.

**Nota:** Certifique-se de ter o Docker e o Docker Compose instalados em seu sistema antes de utilizar este repositório.
