# Docker Commands with Explanations

## **Basic Commands**
- `docker version`  
  Displays the Docker version installed on your system.
  
- `docker info`  
  Shows detailed information about the Docker installation (e.g., containers, images, volumes).

- `docker help`  
  Displays help for Docker commands.

---

## **Container Lifecycle Management**
- `docker run [OPTIONS] IMAGE [COMMAND]`  
  Creates and starts a new container from a specified image.

- `docker start [OPTIONS] CONTAINER`  
  Starts an existing, stopped container.

- `docker stop CONTAINER`  
  Stops a running container.

- `docker restart CONTAINER`  
  Stops and starts a container.

- `docker kill CONTAINER`  
  Immediately stops a container by sending a `SIGKILL` signal.

- `docker rm [OPTIONS] CONTAINER`  
  Removes one or more stopped containers.

- `docker container prune`  
  Removes all stopped containers.

---

## **Image Management**
- `docker images`  
  Lists all Docker images on the host.

- `docker pull IMAGE[:TAG]`  
  Downloads an image from a Docker registry (default is Docker Hub).

- `docker push IMAGE[:TAG]`  
  Uploads an image to a Docker registry.

- `docker build [OPTIONS] PATH | URL`  
  Builds a Docker image from a Dockerfile.

- `docker rmi IMAGE`  
  Removes one or more Docker images.

- `docker image prune`  
  Removes unused images.

---

## **Container Inspection and Interaction**
- `docker ps [OPTIONS]`  
  Lists all running containers. Add `-a` to include stopped containers.

- `docker logs [OPTIONS] CONTAINER`  
  Fetches logs from a container.

- `docker exec [OPTIONS] CONTAINER COMMAND [ARGS...]`  
  Runs a command inside a running container.

- `docker attach CONTAINER`  
  Connects to a running container’s standard input, output, and error streams.

- `docker inspect [OPTIONS] CONTAINER | IMAGE`  
  Displays detailed information about a container or image.

- `docker top CONTAINER`  
  Shows running processes inside a container.

- `docker stats [OPTIONS]`  
  Displays real-time resource usage statistics of containers.

- `docker diff CONTAINER`  
  Shows changes made to a container’s filesystem.

---

## **Volumes and Storage**
- `docker volume create [OPTIONS] [VOLUME]`  
  Creates a new volume.

- `docker volume ls`  
  Lists all volumes.

- `docker volume inspect VOLUME`  
  Displays detailed information about a volume.

- `docker volume rm VOLUME`  
  Removes a volume.

- `docker volume prune`  
  Removes unused volumes.

---

## **Networking**
- `docker network create [OPTIONS] NETWORK`  
  Creates a new network.

- `docker network ls`  
  Lists all Docker networks.

- `docker network inspect NETWORK`  
  Displays detailed information about a network.

- `docker network connect NETWORK CONTAINER`  
  Connects a container to a network.

- `docker network disconnect NETWORK CONTAINER`  
  Disconnects a container from a network.

- `docker network rm NETWORK`  
  Removes a network.

- `docker network prune`  
  Removes unused networks.

---

## **Docker Compose Commands**
- `docker-compose up [OPTIONS]`  
  Starts and creates containers defined in a `docker-compose.yml` file.

- `docker-compose down`  
  Stops and removes containers, networks, and other resources created by `up`.

- `docker-compose ps`  
  Lists containers managed by Docker Compose.

- `docker-compose logs [OPTIONS]`  
  Displays logs for containers managed by Docker Compose.

- `docker-compose build [OPTIONS]`  
  Builds images defined in a `docker-compose.yml` file.

---

## **Advanced Commands**
- `docker save [OPTIONS] IMAGE`  
  Saves an image to a tar archive.

- `docker load [OPTIONS]`  
  Loads an image from a tar archive.

- `docker export CONTAINER`  
  Exports a container’s filesystem as a tar archive.

- `docker import [OPTIONS] FILE`  
  Creates an image from a tar archive.

- `docker system df`  
  Displays disk usage of Docker resources.

- `docker system prune`  
  Cleans up unused resources (containers, images, volumes, networks).

---

## **Swarm and Orchestration**
- `docker swarm init`  
  Initializes a new Swarm cluster.

- `docker swarm join`  
  Adds a node to an existing Swarm cluster.

- `docker service create [OPTIONS] IMAGE [COMMAND]`  
  Creates and starts a new service in a Swarm cluster.

- `docker service ls`  
  Lists all services in a Swarm.

- `docker service scale SERVICE=REPLICAS`  
  Scales a service to the specified number of replicas.

- `docker stack deploy -c COMPOSE-FILE STACK`  
  Deploys a stack in Swarm mode using a Compose file.

- `docker stack rm STACK`  
  Removes a stack.

---

## **Debugging and Monitoring**
- `docker events`  
  Displays real-time events from the Docker daemon.

- `docker checkpoint create CONTAINER CHECKPOINT`  
  Creates a checkpoint for a container.

- `docker checkpoint ls CONTAINER`  
  Lists checkpoints for a container.

- `docker checkpoint rm CONTAINER CHECKPOINT`  
  Removes a checkpoint.

---

## **Utility Commands**
- `docker tag SOURCE_IMAGE[:TAG] TARGET_IMAGE[:TAG]`  
  Tags an image with a new name.

- `docker rename CONTAINER NEW_NAME`  
  Renames a container.

- `docker update [OPTIONS] CONTAINER`  
  Updates container settings (e.g., resources).

---

This list covers most commonly used Docker commands. Let me know if you'd like detailed examples or additional commands!
