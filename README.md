## Symfony and Laravel Dockerized Starter Kit
   ![](https://github.com/ronykader/docker-symfony-laravel-stack/workflows/CI/badge.svg)
   ![](https://img.shields.io/badge/license-AGPL--3.0-green)

Welcome to the Symfony and Laravel Dockerized Starter Kit! This kit allows for rapid setup of a local development environment, with each component meticulously chosen to support the optimal operation of Symfony version 7 and Laravel version 11.

### Getting Started

After cloning this repository, follow these steps to get started:

1. Copy the `.env.dist` file and customize it as required:
    ```
    cp .env.dist .env
    ```

2. Start Docker Compose to get your environment up and running:
    ```
    docker-compose up
    ```

### Symfony Project Setup

To enable Symfony CLI, simply uncomment the specified line in the Dockerfile:

      RUN curl -sS https://get.symfony.com/cli/installer | bash && mv /root/.symfony/bin/symfony /usr/local/bin/symfony


Check your active Docker container by running the following command:

```angular2html
docker ps
```

Access your Docker container with the following command:

```
docker exec -it your-container-name bash
```

Start your Symfony project either by using Composer with the command

```angular2html
 composer create-project symfony/skeleton:"7.0.*" ./
```
or by utilizing Symfony CLI with
```
 symfony new ./
```

Configure the database settings in Symfony's .env file to match those of Docker's .env file. For example:

```angular2html
DATABASE_URL=mysql://ronykader:db_password@db:3306/symfony_laravel?serverVersion=8.0
```

[Run your project.](http://127.0.0.1:8000)  

http://127.0.0.1:8000
    

### Laravel Project Setup
   To enable Laravel CLI, simply uncomment the specified line in the Dockerfile:

      RUN composer global require laravel/installer

    Coming Soon ........