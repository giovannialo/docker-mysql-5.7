# Docker MySQL 5.7

Cria um serviço de banco de dados MySQL na versão 5.7 utilizado o Docker Compose.

## Dependências

* Docker Compose;
* Rede mercury-network.

## Instalação

Siga as etapas abaixo para um correto funcionamento do serviço.

### Rede mercury-network

Crie a rede **mercury-network** e conecte os seus serviços a ela para utilizar o banco de dados.

```docker
docker network create --driver bridge mercury-network
```

### Variáveis de ambiente

Renomeei o arquivo .env.example para .env e configure-o a sua vontade.

```dotenv
MYSQL_USER=user
MYSQL_PASSWORD=user
MYSQL_ROOT_PASSWORD=root
```

### Permissões básicas do usuário simples (não root)

Abra o arquivo **set-grant-permission-to-user.sql** e, onde tem o texto **user**, altere para o mesmo valor de **MYSQL_USER** do arquivo **.env**.

```sql
TRIGGER ON *.* TO 'user'@'%';
```

### Serviço

```docker
docker-compose up -d
```

## Créditos

* [Giovanni Alves de Lima Oliveira](https://github.com/giovannialo) (Desenvolvedor)