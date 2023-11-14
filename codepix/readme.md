# Code Pix - Imersão Full Cycle

## Comandos

### Subir docker

`docker-compose up -d`

### Acessar bash do container Docker

`docker exec -it nome-do-container bash`

### Gerar arquivos de conexão do gRPC

`protoc --go_out=application/grpc/pb/ --go_opt=paths=source_relative --go-grpc_out=application/grpc/pb/ --go-grpc_opt=paths=source_relative --proto_path=application/grpc/protofiles/ application/grpc/protofiles/*.proto`

## Estrutura e camadas

### application

- factory: Instancia objetos com muitas dependências;
- grpc: Servidor e serviços disponibilizados via gRPC;
- kafka: Consumo e processamento de transações com o Apache Kafka;
- model: Estrutura dos objetos que receberão as requisições externas (via Kafka ou gRPC);
- usecase: Executa o fluxo de operações de acordo com as regras de negócio.

### cmd

Comandos registrados para iniciarmos a aplicação e seus serviços (CLI).

### domain

- model: Coração da aplicação e suas regras de negócio.

### infrastructure

- db: Realiza a configuração do ORM e a interface com o banco de dados;
- repository: Realiza a persistência dos dados. Normalmente são chamados pelos "usecases".
