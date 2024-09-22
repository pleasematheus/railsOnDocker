
# Projeto Docker com Ruby e PostgreSQL

Este projeto utiliza Docker Compose para configurar um ambiente com Ruby e PostgreSQL. O container Ruby é preparado com as dependências necessárias e o container PostgreSQL é configurado para persistir os dados.

## Estrutura do Projeto

```
.
├── docker-compose.yml
└── (outros arquivos do projeto)
```

## Tecnologias Usadas

- Ruby 3.1.6 (baseado em Alpine)
- PostgreSQL 16.4 (baseado em Alpine)
- Docker e Docker Compose

## Configuração

### Pré-requisitos

- Docker
- Docker Compose

### Instruções

1. **Clone o repositório:**

   ```bash
   git clone <url-do-repositorio>
   cd <nome-do-repositorio>
   ```

2. **Inicie os containers:**

   ```bash
   docker-compose up
   ```

   Isso iniciará os containers de Ruby e PostgreSQL. O container Ruby ficará em execução e disponível para acesso via terminal.

3. **Acesse o container Ruby:**

   Para acessar o terminal do container Ruby, use:

   ```bash
   docker exec -it <nome-do-container-ruby> sh
   ```

   Substitua `<nome-do-container-ruby>` pelo nome real do container, que pode ser obtido com `docker ps`.

### Mapeamento de Diretórios

- A pasta atual do host está mapeada para a raiz (`/`) do container Ruby, permitindo acesso aos arquivos do projeto diretamente no container.

## Persistência de Dados

O container PostgreSQL utiliza um volume nomeado para garantir que os dados sejam mantidos mesmo se o container for removido.

## Parar os Containers

Para parar e remover os containers, use:

```bash
docker-compose down
```

## Contribuição

Sinta-se à vontade para contribuir com este projeto. Abra um pull request ou um issue se encontrar algum problema.