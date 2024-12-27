# Docker Commands Cheat Sheet

Below is a comprehensive list of essential and advanced Docker commands with detailed explanations for each. Use these commands to manage Docker containers, images, volumes, and networks effectively.

```markdown
# Docker Basics

## Check Docker Version
```bash
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

# Docker Compose Commands

## Start Services
```bash
docker-compose up
```
Starts services defined in the `docker-compose.yml` file.

## Start Services in Detached Mode
```bash
docker-compose up -d
```
Runs the services in the background.

## Stop Services
```bash
docker-compose down
```
Stops and removes containers, networks, and volumes created by `docker-compose up`.

## View Logs
```bash
docker-compose logs
```
Displays logs for all services.

## Scale Services
```bash
docker-compose up --scale <service-name>=<count>
```
Scales a service to the specified number of instances.

---

# Example `docker-compose.yml`
```yaml
version: '3.8'
services:
  web:
    image: nginx
    ports:
      - "8080:80"
    volumes:
      - ./html:/usr/share/nginx/html
  app:
    build:
      context: ./app
      dockerfile: Dockerfile
    ports:
      - "5000:5000"
    environment:
      - APP_ENV=production
    depends_on:
      - db
  db:
    image: postgres
    restart: always
    environment:
      POSTGRES_USER: user
      POSTGRES_PASSWORD: password
      POSTGRES_DB: mydb
```

---

# Debugging and Troubleshooting

## View Build Context
```bash
docker build --no-cache -t <image-name>:<tag> <path>
```
Forces Docker to rebuild the image without using cache, useful for debugging build issues.

## Debug Compose Files
```bash
docker-compose config
```
Validates and displays the resolved configuration for a `docker-compose.yml` file.

---

# Security and Best Practices

## Scan Images for Vulnerabilities
```bash
docker scan <image-name>
```
Performs a security scan on the specified image (requires Docker Desktop).

## Limit Container Resources
```bash
docker run --memory="256m" --cpus="1.0" <image-name>
```
Limits the memory and CPU usage of a container to specified values.

---

# Managing Docker Swarm (Optional)

## Initialize a Swarm
```bash
docker swarm init
```
Sets up the current machine as a Docker Swarm manager.

## Deploy a Stack
```bash
docker stack deploy -c <compose-file> <stack-name>
```
Deploys a stack using a Docker Compose file in Swarm mode.

## List Services in a Stack
```bash
docker stack services <stack-name>
```
Displays all services in the specified stack.

## Remove a Stack
```bash
docker stack rm <stack-name>
```
Removes the specified stack from the swarm.
```
```


# Advanced Docker Commands and Configurations

## Docker Commands

### 1. **`docker network create`**
   - **Description**: Creates a new network for containers to communicate.
   - **Syntax**:
     ```bash
     docker network create <network-name>
     ```
   - **Example**:
     ```bash
     docker network create --driver bridge my_network
     ```

### 2. **`docker volume create`**
   - **Description**: Creates a named volume to persist data between container restarts.
   - **Syntax**:
     ```bash
     docker volume create <volume-name>
     ```
   - **Example**:
     ```bash
     docker volume create my_volume
     ```

### 3. **`docker run --network`**
   - **Description**: Runs a container in a specific network.
   - **Syntax**:
     ```bash
     docker run --network <network-name> <image-name>
     ```
   - **Example**:
     ```bash
     docker run --network my_network nginx
     ```

### 4. **`docker exec`**
   - **Description**: Executes a command inside a running container.
   - **Syntax**:
     ```bash
     docker exec -it <container-id> <command>
     ```
   - **Example**:
     ```bash
     docker exec -it my_container bash
     ```

### 5. **`docker logs`**
   - **Description**: Fetches logs from a running or stopped container.
   - **Syntax**:
     ```bash
     docker logs <container-id>
     ```
   - **Example**:
     ```bash
     docker logs my_container
     ```

### 6. **`docker build --no-cache`**
   - **Description**: Builds a Docker image without using cache, forcing a fresh build.
   - **Syntax**:
     ```bash
     docker build --no-cache -t <image-name> .
     ```
   - **Example**:
     ```bash
     docker build --no-cache -t my_image .
     ```

### 7. **`docker-compose logs`**
   - **Description**: Shows logs from all services in a Docker Compose setup.
   - **Syntax**:
     ```bash
     docker-compose logs
     ```
   - **Example**:
     ```bash
     docker-compose logs
     ```

### 8. **`docker ps -a`**
   - **Description**: Lists all containers, including stopped ones.
   - **Syntax**:
     ```bash
     docker ps -a
     ```
   - **Example**:
     ```bash
     docker ps -a
     ```

### 9. **`docker stats`**
   - **Description**: Displays real-time statistics for all running containers.
   - **Syntax**:
     ```bash
     docker stats
     ```
   - **Example**:
     ```bash
     docker stats
     ```

### 10. **`docker-compose up --build`**
   - **Description**: Builds images before starting containers in a Docker Compose setup.
   - **Syntax**:
     ```bash
     docker-compose up --build
     ```
   - **Example**:
     ```bash
     docker-compose up --build
     ```

## Dockerfile Instructions

### 1. **`FROM`**
   - **Description**: Specifies the base image to use for the container.
   - **Example**:
     ```dockerfile
     FROM ubuntu:20.04
     ```

### 2. **`RUN`**
   - **Description**: Executes a command during the image build process.
   - **Example**:
     ```dockerfile
     RUN apt-get update && apt-get install -y curl
     ```

### 3. **`COPY`**
   - **Description**: Copies files from the host machine into the container.
   - **Example**:
     ```dockerfile
     COPY ./local-file /path/in/container/
     ```

### 4. **`ADD`**
   - **Description**: Similar to `COPY` but with additional features (e.g., extracting tar files).
   - **Example**:
     ```dockerfile
     ADD ./local-file.tar.gz /path/in/container/
     ```

### 5. **`EXPOSE`**
   - **Description**: Informs Docker that the container will listen on the specified network ports at runtime.
   - **Example**:
     ```dockerfile
     EXPOSE 8080
     ```

### 6. **`CMD`**
   - **Description**: Specifies the default command to run when the container starts.
   - **Example**:
     ```dockerfile
     CMD ["python", "app.py"]
     ```

### 7. **`ENTRYPOINT`**
   - **Description**: Sets the main command to run, and prevents overriding it.
   - **Example**:
     ```dockerfile
     ENTRYPOINT ["python", "app.py"]
     ```

### 8. **`WORKDIR`**
   - **Description**: Sets the working directory for any `RUN`, `CMD`, `ENTRYPOINT`, `COPY`, and `ADD` instructions.
   - **Example**:
     ```dockerfile
     WORKDIR /app
     ```

### 9. **`ENV`**
   - **Description**: Sets an environment variable.
   - **Example**:
     ```dockerfile
     ENV MY_ENV_VAR=value
     ```

### 10. **`VOLUME`**
   - **Description**: Creates a mount point with the specified path and marks it as holding persistent data.
   - **Example**:
     ```dockerfile
     VOLUME ["/data"]
     ```

## Docker Compose Configuration

### 1. **Basic `docker-compose.yml` Example**
   - **Description**: A simple Docker Compose file that sets up a web server and database.
   - **Example**:
     ```yaml
     version: '3.8'

     services:
       web:
         image: nginx
         ports:
           - "8080:80"
       db:
         image: postgres
         environment:
           POSTGRES_PASSWORD: example
     ```

### 2. **Using Volumes with Docker Compose**
   - **Description**: Demonstrates how to persist data with volumes.
   - **Example**:
     ```yaml
     version: '3.8'

     services:
       web:
         image: nginx
         volumes:
           - ./nginx.conf:/etc/nginx/nginx.conf
       db:
         image: postgres
         volumes:
           - postgres_data:/var/lib/postgresql/data

     volumes:
       postgres_data:
     ```

### 3. **Using Networks with Docker Compose**
   - **Description**: Example of creating and using a custom network.
   - **Example**:
     ```yaml
     version: '3.8'

     services:
       web:
         image: nginx
         networks:
           - frontend
       db:
         image: postgres
         networks:
           - backend

     networks:
       frontend:
       backend:
     ```

### 4. **Build Images with Docker Compose**
   - **Description**: Builds a custom image for a service defined in `docker-compose.yml`.
   - **Example**:
     ```yaml
     version: '3.8'

     services:
       web:
         build: ./web
         ports:
           - "8080:80"
       db:
         image: postgres
     ```

### 5. **Using Environment Variables with Docker Compose**
   - **Description**: Passes environment variables to containers.
   - **Example**:
     ```yaml
     version: '3.8'

     services:
       web:
         image: nginx
         environment:
           - MY_VAR=value
       db:
         image: postgres
         environment:
           POSTGRES_PASSWORD: example
     ```

---

Feel free to modify and expand this as needed for your GitHub repository!
