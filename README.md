# Microservices com gRPC - Parte 1

Este projeto demonstra a implementação de um microsserviço de pedidos (orders) utilizando gRPC em Go, com persistência em MySQL.

## Pré-requisitos

- Go 1.19 ou superior
- Docker e Docker Compose
- Git

## Instalação e Configuração

### 1. Clone o repositório

```bash
git clone <url-do-repositorio>
cd pratica-microservicos-com-grpc-parte-1
```

### 2. Instale as dependências do Go

```bash
cd microservices/order
go mod tidy
```

### 3. Gere o código protobuf (opcional, se já não estiver gerado)

Execute o script `run.sh` na raiz do projeto:

```bash
./run.sh
```

Este script irá:
- Instalar o protoc-gen-go e protoc-gen-go-grpc
- Gerar o código Go a partir do arquivo `order.proto`

## Como Executar

### 1. Inicie o banco de dados MySQL

```bash
cd microservices/order
docker-compose up -d
```


### 2. Execute o servidor gRPC

```bash
cd microservices/order
./run_server.bat
```


O servidor irá iniciar na porta 3000.

### 3. Execute o cliente de teste (em outro terminal)

```bash
cd microservices/order
go run client/main.go
```

O cliente irá:
- Conectar ao servidor gRPC na porta 3000
- Criar um pedido de exemplo
- Exibir o ID do pedido criado

## Variáveis de Ambiente

O projeto utiliza as seguintes variáveis de ambiente:

- `DATA_SOURCE_URL`: URL de conexão com o banco MySQL
  - Formato: `user:password@tcp(host:port)/database?charset=utf8mb4&parseTime=True&loc=Local`
- `APPLICATION_PORT`: Porta onde o servidor gRPC irá escutar (padrão: 3000)
- `ENV`: Ambiente de execução (development/production)

