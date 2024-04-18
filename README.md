# Docker with Symfony and Laravel

This Docker Symfony and Laravel Stack enables rapid setup of a local development environment, with each component meticulously chosen to support the optimal operation of Symfony ^7 and Laravel ^11

## Getting started - After clone this repository
Copy the .env.dist file and edit the entries to your needs:
```
cp .env.dist .env
```

Just start docker-compose to get your environment up and running!
```
docker-compose up
```

Once the container is up, you can utilize Composer and the Symfony CLI inside your container.
```
docker exec -it your-container-name bash

```

## Coming Soon More..............
