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


# What is a Dockerfile?

A Dockerfile is a text document that contains all the commands a user could call on the command line to create an image. If you want to create an image from your own code that you can push to Docker Hub, you need to create a Dockerfile for your application.

## How to Write a Dockerfile

A Dockerfile consists of two main parts:

1. **Base Image:** The starting point for your Docker image, usually an official image from Docker Hub.
2. **Commands:** A series of instructions to configure the image, such as installing dependencies.



Below is an example of a Dockerfile to containerize the backend app:

```Dockerfile
# Use the official Node.js image as the base image
FROM node:14

# Set the working directory inside the container
WORKDIR /app

# Copy package.json and package-lock.json to the working directory
COPY package*.json ./

# Install the dependencies
RUN npm install

# Copy the rest of the application code to the working directory
COPY . .

# Expose the port the app runs on
EXPOSE 3000

# Define the command to run the app
CMD ["npm", "start"]
```

### Common Dockerfile Commands

- **WORKDIR:** Sets the working directory for any `RUN`, `CMD`, `ENTRYPOINT`, or `COPY` instructions that follow it.
- **RUN:** Executes any commands in a new layer on top of the current image and commits the results.
- **CMD:** Provides defaults for executing a container. There can only be one `CMD` instruction in a Dockerfile.
- **EXPOSE:** Informs Docker that the container listens on the specified network ports at runtime.
- **ENV:** Sets an environment variable.
- **COPY:** Copies files from the Docker host to the Docker image.

### Create Docker image
```sh
docker build -t <image_name> .
```

### Docker Layers:
- **Layer 1:** The base image, which is the starting point for the Docker image.
- **Layer 2:** The `WORKDIR` instruction, which sets the working directory for the
Docker image.
- **Layer 3:** The `COPY` instruction, which copies the application code to the working
directory.
- **Layer 4:** The `RUN` instruction, which installs the dependencies.
- **Layer 5:** The `EXPOSE` instruction, which informs Docker that the container listens
on the specified network ports at runtime.
- **Layer 6:** The `CMD` instruction, which provides defaults for executing a container.


### Docker Compose::
- **docker-compose.yml:** The configuration file for the Docker Compose application.
- **docker-compose up:** Starts the application and runs the containers defined in the configuration file.
- **docker-compose down:** Stops the application and removes the containers defined in the configuration file.
- **docker-compose ps:** Lists the containers defined in the configuration file.
- **docker-compose logs:** Displays the logs for the containers defined in the configuration file.
---