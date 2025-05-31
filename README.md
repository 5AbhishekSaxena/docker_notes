## Docker Notes

Contains a list of simple docker commands.

## <a name="table-of-contents"></a>Toable of Content

-   Docker

    -   [Images and Containers](#images-and-containers)
    -   [Run a container](#run-a-container)
    -   [Logs](#logs)
    -   [Build](#build)
    -   [Clean up](#clean-up)
    -   [Network](#network)

-   [Docker Compose](#docker-compose)
    -   [Basic commands](#docker-compose-basic-commands)

#### <a name="images-and-containers">Images and containers</a> <sup>[Back ⇈](#table-of-contents)</sup>

-   `docker images`
    List all the docker images.

-   `docker ps`
    List all the running containers.

-   `docker ps -a`
    Lists all the containers runnning + stopped

-   `docker ps -a | grep <container-name>`
    List the container with the container-name.

-   `docker pull <image_name>:<version>`
    Pull the image from Docker hub of the specified version

-   `docker pull <image_name>`
    Same as before but teh version is "latest" which is the default version is pulled from the DockerHub.

### <a name="run-a-container"></a>Run a container <sup>[Back ⇈](#table-of-contents)</sup>

-   `docker run <image_name>:<tag>`
    Runs the container for the docker image.
    Please note:

1. Docker will look for the image locally, and if not found then it will look for it in the docker hub. If found, it will pull it and then run it.
2. It creates a new container each time.

-   `docker run -d <image_name>:<tag>`
    Runs the container in detached mode. The process is not blocking the terminal. The container runs in the background.

-   `docker run -d -p <local_machine_port>:<application/docker container_port> <image_name>:<tag>`
    Port binding - Binds the container to a port on the local machine so it can be accessed.

-   `docker run --name web-app -d -p <local_machine_port>:<application/docker container_port> <image_name>:<tag>`
    flag --name <name>
    It is used to give a custom name to the container.

-   `docker run --name web-app -d -p <local_machine_port>:<application/docker container_port> --net <network-name> <image_name>:<tag>`
    flag --net <network-name>
    It is used to run the container on a docker network. All the containers running on the same network can communicate with each other.

-   `docker run --name web-app -d -p <local_machine_port>:<application/docker container_port> --net <network-name> -e <env-var-name>=<env-var-value> <image_name>:<tag>`
    flag -e <env-var-name>=<env-var-value>
    It is used to pass/set environment variables for the container.

-   `docker start <container_id> or <container_name>`
    Restarts the exited/stopped container.

-   `docker stop <container_name> or <container_id>`
    Stops the container with the given id or name.

-   `docker stop $(docker ps -q)`
    Stops all the running containers.

Example commands
Single line command

```bash
docker run -d -p 27017:27017 -e MONGO_INITDB_ROOT_USERNAME=admin -e MONGO_INITDB_ROOT_PASSWORD=password --name mongodb --net mongo-network mongo
```

Multiline command

```bash
    docker run -d \
    -p 27017:27017 \
    -e MONGO_INITDB_ROOT_USERNAME=admin \
    -e MONGO_INITDB_ROOT_PASSWORD=password \
    --name mongodb \
    --net mongo-network \
    mongo
```

### <a name="logs"></a>Logs <sup>[Back ⇈](#table-of-contents)</sup>

-   `docker logs <container_id> or <container_name>`
    View logs of the container.

-   `docker logs <container_id> or <container_name> | tail`
    View logs of the container and move the cursor to bottom.

-   `docker logs <container_id> or <container_name> -f`
    Stream the logs of the container.

### <a name="build"></a>Build <sup>[Back ⇈](#table-of-contents)</sup>

-   `docker build -t <image_name>:<tag> . // or --tag = and "." refers to the current folder`
    build a custom docker image.

### <a name="clean-up"></a>Clean up <sup>[Back ⇈](#table-of-contents)</sup>

-   `docker container prune`
    Delete all the stopped containers

-   `docker image rm <image_name>:<tag>` or `docker rmi <image_name>:<tag>`
    Delete the docker image

### <a name="network"></a>Network <sup>[Back ⇈](#table-of-contents)</sup>

-   `docker network ls`
    Lists all the available docker network.

## <a name="docker-compsoe"></a>Docker Compose <sup>[Back ⇈](#table-of-contents)</sup>

Note: The docker compose creates a network for the services described in the docker compose file.

When the docekr compsoe is start it creates the network and volumne for the services, and removes the network and the volume once the services are stopped using `docker-compose down`.

### <a name="docker-compose-basic-commands"></a>Docker Compose basic commands <sup>[Back ⇈](#table-of-contents)</sup>

You can either use `docker compose` or `docker-compose`(old) for the below commands.

-   `docker-compose up`
    Start/run the services in the docker compose file.

-   `docker-compose -f <docker-compose yml or yaml file> up`
    Start the services in the docker compose file.

-   `docker-compose up -d`
    Start/run the services in the docker compose file in detach mode.

-   `docker-compose -f <docker-compose yml or yaml file> up -d`
    Start the services in the docker compose file in detach mode.

-   `docker-compose down`
    Stop the services in the docker compose.

-   `docker-compsoe ps -a`
    Lists all the docker compose projects.
