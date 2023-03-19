## Docker Notes
Contains a list of simple docker commands.

### Images and containers
- `docker images`
List all the docker images.

- `docker ps`
List all the running containers.

- `docker ps -a`
Lists all the containers runnning + stopped

- `docker pull <image_name>:<version>`
Pull the image from Docker hub of the specified version

- `docker pull <image_name>`
Same as before but teh version is "latest" which is the default version is pulled from the DockerHub.

### Run a container
- `docker run <image_name>:<tag>`
Runs the container for the docker image.
Please note: 
1. Docker will look for the image locally, and if not found then it will look for it in the docker hub. If found, it will pull it and then run it.
2. It creates a new container each time.

- `docker run -d <image_name>:<tag>`
Runs the container in detached mode. The process is not blocking the terminal. The container runs in the background.

- `docker run -d -p <local_machine_port>:<application/docker container_port> <image_name>:<tag>`
Port binding - Binds the container to a port on the local machine so it can be accessed.

- `docker run --name web-app -d -p <local_machine_port>:<application/docker container_port> <image_name>:<tag>`
flag --name <name>
It is used to give a custom name to the container.

- `docker start <container_id> or <container_name>`
Restarts the exited/stopped container.

- `docker stop <container_name> or <container_id>`
Stops the container with the given id or name.

### Logs
- docker logs <container_id> or <container_name>`
View logs of the container.

### Build
- `docker build -t <image_name>:<tag> . // or --tag = and "." refers to the current folder`
build a custom docker image.

### Clean up
- `docker container prune`
Delete all the stopped containers

- `docker image rm <image_name>:<tag>`
Delete the docker image
