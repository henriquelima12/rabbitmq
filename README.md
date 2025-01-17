# Projeto RabbitMQ com Spring Boot

Este projeto demonstra como usar o RabbitMQ para enviar mensagens com uma aplicação **Spring Boot**. A aplicação expõe duas rotas HTTP para enviar mensagens para uma fila RabbitMQ.

## Requisitos

- Docker
- Docker Compose
- JDK 17 ou superior
- Maven (ou Gradle, dependendo de sua configuração)
- RabbitMQ (será executado via Docker)

## Rodando o Projeto

### 1. Subindo o RabbitMQ com Docker Compose

O arquivo `docker-compose.yml` para configurar o RabbitMQ está localizado no diretório `docker/`. Para rodar o RabbitMQ facilmente, use o Docker Compose. 

No diretório raiz do projeto, execute o seguinte comando para subir o RabbitMQ:

```bash
cd docker
docker-compose up
````

### 2. Rodando o Backend (Spring Boot)

Clone este repositório e rode o projeto Spring Boot com o seguinte comando:

```bash
git clone https://github.com/henriquelima12/rabbitmq.git
cd springboot-rabbitmq
./mvnw spring-boot:run
```

Ou se você estiver usando o Maven globalmente:

```bash
mvn spring-boot:run
```

A aplicação Spring Boot será iniciada e estará disponível em http://localhost:8080.

### 3. Verificando o RabbitMQ

Após subir o RabbitMQ com o Docker Compose, você pode acessar a interface de gerenciamento do RabbitMQ em http://localhost:15672. Nessa interface, você pode visualizar as filas e as mensagens enviadas, além de verificar o status do RabbitMQ.

Credenciais padrão:

Usuário: guest
Senha: guest

## Endpoints

### 1. **GET** /api/v1/publish?message={mensagem}

Envia uma mensagem simples para uma fila do RabbitMQ.

**Exemplo de requisição:**

```bash
GET http://localhost:8080/api/v1/publish?message=helloworld
```

### 2. POST /api/v1/publish
Envia um objeto JSON para a fila do RabbitMQ.

**Exemplo de requisição (JSON no corpo da requisição):**

```bash
{
  "id": 1,
  "firstName": "henrique",
  "lastName": "araujo"
}
```
