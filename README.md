## Prerequisites

- [Docker](https://docs.docker.com/get-docker/) installed on your machine
- Docker Compose (if using docker-compose)

## Docker Commands

### Building Docker Images

Build the Docker image for the project:
```sh
docker build -t your_project_name .
```

### Running Docker Containers

Run a Docker container from the built image:
```sh
docker run -d -p 3000:3000 --name your_container_name your_project_name
```

Run a Docker container with environment variables:
```sh
docker run -d -p 3000:3000 --env-file .env --name your_container_name your_project_name
```

Run a Docker container in interactive mode:
```sh
docker run -it --name your_container_name your_project_name /bin/bash
```

### Docker Compose Commands

Build and start all services defined in the `docker-compose.yml` file:
```sh
docker-compose up --build
```

Start all services defined in the `docker-compose.yml` file:
```sh
docker-compose up
```

Start all services in the background (detached mode):
```sh
docker-compose up -d
```

Stop all running services:
```sh
docker-compose down
```

### Managing Docker Containers

List all running Docker containers:
```sh
docker ps
```

List all Docker containers (including stopped ones):
```sh
docker ps -a
```

Stop a running Docker container:
```sh
docker stop your_container_name
```

Start a stopped Docker container:
```sh
docker start your_container_name
```

Remove a stopped Docker container:
```sh
docker rm your_container_name
```

Remove a running Docker container (forcefully):
```sh
docker rm -f your_container_name
```

### Managing Docker Images

List all Docker images:
```sh
docker images
```

Remove a Docker image:
```sh
docker rmi your_image_id
```

### Inspecting Docker Containers

View logs of a running Docker container:
```sh
docker logs your_container_name
```

View real-time logs of a running Docker container:
```sh
docker logs -f your_container_name
```

### Cleaning Up

Remove all stopped containers, all unused networks, and all dangling images:
```sh
docker system prune
```

Remove all unused data (containers, networks, images, and optionally volumes):
```sh
docker system prune -a
```

---

