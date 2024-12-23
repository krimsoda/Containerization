# Docker Guide

## Table of Contents
1. [Introduction to Docker](#introduction-to-docker)
2. [Installation](#installation)
3. [Key Docker Concepts](#key-docker-concepts)
4. [Basic Docker Commands](#basic-docker-commands)
5. [Creating and Using Dockerfiles](#creating-and-using-dockerfiles)
6. [Docker Compose](#docker-compose)
7. [Managing Docker Containers](#managing-docker-containers)
8. [Best Practices](#best-practices)
9. [Resources](#resources)

---

## Introduction to Docker
Docker is an open-source platform that allows developers to automate the deployment of applications inside lightweight, portable containers. Containers package the application and its dependencies, ensuring consistency across environments.

### Benefits of Docker:
- Consistent development, testing, and production environments.
- Lightweight and faster compared to traditional virtual machines.
- Simplified dependency management.

---

## Installation

### Prerequisites
- A supported operating system (Windows, macOS, Linux).
- Admin/root access to the system.

### Steps
1. **Windows/MacOS:**
   - Download Docker Desktop from the [official website](https://www.docker.com/products/docker-desktop/).
   - Install the application and follow the on-screen instructions.
   - Start Docker Desktop.

2. **Linux:**
   ```bash
   # Update your package index
   sudo apt update

   # Install prerequisites
   sudo apt install -y ca-certificates curl gnupg

   # Add Docker's official GPG key
   curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg

   # Set up the stable repository
   echo \"deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable\" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

   # Install Docker Engine
   sudo apt update
   sudo apt install -y docker-ce docker-ce-cli containerd.io

   # Verify installation
   docker --version
   ```

3. **Post-Installation Steps (Optional):**
   - Add your user to the Docker group to avoid using `sudo`:
     ```bash
     sudo usermod -aG docker $USER
     ```
   - Log out and log back in.

---

## Key Docker Concepts

### Images
- Read-only templates used to create containers.
- Built using Dockerfiles.

### Containers
- Lightweight, standalone executable packages of software.
- Created from Docker images.

### Dockerfile
- A script containing instructions to build a Docker image.

### Volumes
- Persistent storage for Docker containers.

### Networks
- Allow communication between containers.

---

## Basic Docker Commands

### Working with Images
```bash
# Pull an image from Docker Hub
docker pull <image-name>

# List downloaded images
docker images

# Remove an image
docker rmi <image-id>
```

### Working with Containers
```bash
# Run a container
docker run -d --name <container-name> <image-name>

# List running containers
docker ps

# List all containers (including stopped ones)
docker ps -a

# Stop a container
docker stop <container-id>

# Remove a container
docker rm <container-id>
```

### Other Useful Commands
```bash
# View Docker system info
docker info

# View Docker logs
docker logs <container-id>
```

---

## Creating and Using Dockerfiles

### Example Dockerfile
```dockerfile
# Use an official Python runtime as a base image
FROM python:3.9-slim

# Set the working directory
WORKDIR /app

# Copy requirements.txt and install dependencies
COPY requirements.txt ./
RUN pip install --no-cache-dir -r requirements.txt

# Copy the rest of the application code
COPY . .

# Command to run the application
CMD [ "python", "app.py" ]
```

### Build and Run an Image
```bash
# Build an image
docker build -t <image-name> .

# Run the image
docker run -d -p 5000:5000 <image-name>
```

---

## Docker Compose

Docker Compose is a tool to define and run multi-container applications using a YAML file.

### Example `docker-compose.yml`
```yaml
version: '3.8'
services:
  web:
    image: nginx
    ports:
      - "8080:80"
  app:
    build:
      context: ./app
    volumes:
      - .:/app
    ports:
      - "5000:5000"
```

### Commands
```bash
# Start services defined in docker-compose.yml
docker-compose up

# Stop services
docker-compose down

# List running services
docker-compose ps
```

---

## Managing Docker Containers

### Inspecting Containers
```bash
# View container details
docker inspect <container-id>

# Access a running container's shell
docker exec -it <container-id> /bin/bash
```

### Cleaning Up
```bash
# Remove unused images
docker image prune

# Remove unused containers
docker container prune

# Remove everything (use with caution)
docker system prune -a
```

---

## Best Practices

1. Use lightweight base images (e.g., `alpine`).
2. Minimize the number of layers in Dockerfiles.
3. Leverage multi-stage builds for optimized images.
4. Use `.dockerignore` to exclude unnecessary files.
5. Regularly update and scan images for vulnerabilities.
6. Use volumes for persistent data.

---

## Resources

- [Docker Documentation](https://docs.docker.com/)
- [Docker Hub](https://hub.docker.com/)
- [Play with Docker](https://labs.play-with-docker.com/)
- [Docker Cheat Sheet](https://github.com/wsargent/docker-cheat-sheet)

---

### Contributions
Feel free to submit issues or pull requests to improve this guide!

