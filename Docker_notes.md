# Docker Commands Cheat Sheet

Below is a comprehensive list of essential Docker commands with detailed explanations for each. Use these commands to manage Docker containers, images, volumes, and networks effectively.

```markdown
# Docker Basics

## Check Docker Version
docker --version
```
Displays the installed Docker version.

## Get Help
```bash
docker --help
```
Provides a list of available Docker commands and options.

---

# Working with Docker Images

## List Docker Images
```bash
docker images
```
Shows all locally available Docker images.

## Search for an Image
```bash
docker search <image-name>
```
Searches the Docker Hub for images matching the given name.

## Pull an Image
```bash
docker pull <image-name>:<tag>
```
Downloads the specified image and tag from Docker Hub. The `:tag` is optional; the latest tag is pulled by default.

## Remove an Image
```bash
docker rmi <image-id>
```
Deletes the specified image from the local system. Replace `<image-id>` with the actual image ID or name.

---

# Managing Docker Containers

## List Running Containers
```bash
docker ps
```
Displays all currently running containers.

## List All Containers
```bash
docker ps -a
```
Shows all containers, including stopped ones.

## Run a Container
```bash
docker run -d --name <container-name> <image-name>
```
Starts a container in detached mode (`-d`) with the specified name and image.

## Attach to a Running Container
```bash
docker attach <container-name>
```
Attaches to the standard input/output of a running container.

## Stop a Running Container
```bash
docker stop <container-name>
```
Gracefully stops the specified container.

## Remove a Container
```bash
docker rm <container-name>
```
Deletes a stopped container.

## Restart a Container
```bash
docker restart <container-name>
```
Restarts the specified container.

---

# Inspecting Containers and Images

## Inspect a Container
```bash
docker inspect <container-name>
```
Provides detailed information about a container in JSON format.

## Inspect an Image
```bash
docker inspect <image-name>
```
Provides detailed information about an image in JSON format.

---

# Docker Volumes

## List Volumes
```bash
docker volume ls
```
Shows all available Docker volumes.

## Create a Volume
```bash
docker volume create <volume-name>
```
Creates a new volume with the specified name.

## Remove a Volume
```bash
docker volume rm <volume-name>
```
Deletes the specified volume.

## Inspect a Volume
```bash
docker volume inspect <volume-name>
```
Displays detailed information about a specific volume.

---

# Docker Networks

## List Networks
```bash
docker network ls
```
Displays all Docker networks.

## Create a Network
```bash
docker network create <network-name>
```
Creates a new network with the specified name.

## Remove a Network
```bash
docker network rm <network-name>
```
Deletes the specified network.

## Connect a Container to a Network
```bash
docker network connect <network-name> <container-name>
```
Attaches a container to the specified network.

## Disconnect a Container from a Network
```bash
docker network disconnect <network-name> <container-name>
```
Detaches a container from the specified network.

---

# Managing Logs

## View Container Logs
```bash
docker logs <container-name>
```
Displays the logs of the specified container.

## Follow Container Logs
```bash
docker logs -f <container-name>
```
Streams the logs of a running container in real-time.

---

# Docker Compose

## Start Services
```bash
docker-compose up
```
Starts the services defined in the `docker-compose.yml` file.

## Start Services in Detached Mode
```bash
docker-compose up -d
```
Starts the services in detached mode.

## Stop Services
```bash
docker-compose down
```
Stops all running services defined in the `docker-compose.yml` file.

---

# Advanced Commands

## Build an Image
```bash
docker build -t <image-name>:<tag> <path>
```
Builds a Docker image from a `Dockerfile` in the specified path. Replace `<tag>` with the desired tag name.

## Tag an Image
```bash
docker tag <image-id> <repository-name>:<tag>
```
Tags an image with a new name and tag for pushing to a registry.

## Push an Image
```bash
docker push <repository-name>:<tag>
```
Uploads the tagged image to a Docker registry.

## Prune Unused Resources
```bash
docker system prune
```
Removes unused containers, images, networks, and volumes to free up space.

---

# Debugging and Troubleshooting

## Check Resource Usage
```bash
docker stats
```
Displays real-time resource usage (CPU, memory, etc.) for running containers.

## Show Container Events
```bash
docker events
```
Streams real-time events from the Docker daemon.

---

# Security

## Scan an Image for Vulnerabilities
```bash
docker scan <image-name>
```
Performs a security scan on the specified image (requires Docker Desktop).
