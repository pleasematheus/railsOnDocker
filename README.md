# Docker Project with Ruby and PostgreSQL

This project uses Docker Compose to set up an environment with Ruby and PostgreSQL. The Ruby container is prepared with the required dependencies, and the PostgreSQL container is configured to persist data.

## Project Structure

```
.
├── docker-compose.yml
└── (other project files)
```

## Technologies Used

- Ruby 3.1.6 (Alpine-based)
- PostgreSQL 16.4 (Alpine-based)
- Docker and Docker Compose

## Setup

### Prerequisites

- Docker
- Docker Compose

### Instructions

1. **Clone the repository:**

```bash
git clone https://github.com/pleasematheus/railsOnDocker.git
cd railsOnDocker
```

2. **Start the containers:**

```bash
docker-compose up
```

This will start the Ruby and PostgreSQL containers. The Ruby container will keep running and be available through the terminal.

3. **Access the Ruby container:**

To access the Ruby container terminal, run:

```bash
docker exec -it <ruby-container-name> sh
```

`sh` can be replaced with `/bin/sh`.
`ash` or `/bin/ash` can also be used.

Replace `<ruby-container-name>` with the actual container name, which you can get with `docker ps`.

### Directory Mapping

- The current host folder is mapped to the Ruby container home folder (`/home`), allowing direct access to project files from inside the container.

## Data Persistence

The PostgreSQL container uses a named volume to ensure data is kept even if the container is removed.

## Stop Containers

If you need to stop the containers without removing them, run:

```bash
docker compose stop
```

## Start Containers Again

If you need to start the containers again, run:

```bash
docker compose start
```

## Remove Containers

To remove the containers, run:

```bash
docker-compose down
```

## How to Connect to the Ruby Container for Development Using VS Code

1. Install the [Dev Containers](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers) extension in VS Code.
2. When VS Code opens, go to the lower-left corner and click `Open a Remote Window`.
3. Select `Attach to Running Container`.
4. Select the Ruby container.
5. A new VS Code window will open and the connection will be established.
6. Navigate to the `/home` folder.
7. You're all set :D

## How to Start a Ruby on Rails Project

1. Run one of the following commands:

   ```bash
   rails new <project-name>
   ```

   or

   ```bash
   rails new <project-name> -d postgresql
   ```

2. Move into the project folder:

   ```bash
   cd <project-name>
   ```

3. Install dependencies:

   ```bash
   bundle install
   ```

4. Configure the `database.yml` file inside the `config` folder:

   > Remember to replace `<container-postgres>` with the real PostgreSQL container name, which you can get with `docker ps`.
   > The database name, username, and password should be configured according to your needs and the PostgreSQL container setup.
   > The example below is a basic development configuration and can be adjusted as needed.

   ```bash
   nano config/database.yml
   ```

   `database.yml` file:

   ```yml
   default:
     adapter: postgresql
     encoding: unicode
     pool: 5 # Default value
     database:
     username:
     password: 1234
     host: <container-postgres>
     port: 5432
   ```

5. Create the database:

   ```bash
   rails db:create
   ```

6. Run migrations:

   ```bash
   rails db:migrate
   ```

7. Finally, start the Rails server:

   ```bash
   rails s -p
   ```

## Contribution

Feel free to contribute to this project. Open a pull request or an issue if you find any problems.
