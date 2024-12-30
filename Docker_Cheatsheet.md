# Docker Commands Cheat Sheet

## 1. Docker Registry and Repository

| Command                      | Meaning                        | Syntax                                      |
|------------------------------|--------------------------------|--------------------------------------------|
| **Login to a Registry**      | Log in to your Registry        | `docker login` <br> `docker login localhost:8080` |
| **Logout from a Registry**   | Log out from your Registry     | `docker logout` <br> `docker logout localhost:8080` |
| **Search for an Image**      | Search for any image           | `docker search nginx` <br> `docker search --filter stars=3 --no-trunc nginx` |
| **Pulling an Image**         | Download a specific image      | `docker image pull nginx` <br> `docker image pull eon01/nginx localhost:5000/myadmin/nginx` |
| **Pushing an Image**         | Push a specific image          | `docker image push eon01/nginx` <br> `docker image push eon01/nginx localhost:5000/myadmin/nginx` |

---

## 2. Running Containers

| Command                            | Meaning                              | Syntax                                      |
|------------------------------------|--------------------------------------|--------------------------------------------|
| **Create a Container**             | Create a container without running   | `docker container create -t -i eon01/infinite --name XYZ` |
| **Run a Container**                | Run a container                      | `docker container run -it --name XYZ -d eon01/infinite` |
| **Rename a Container**             | Rename a container                   | `docker container rename XYZ infinity` |
| **Remove a Container**             | Remove a container                   | `docker container rm infinite` |
| **Update a Container**             | Update container resources           | `docker container update --cpu-shares 512 -m 300M infinite` |

---

## 3. Starting or Stopping Containers

| Command                            | Meaning                              | Syntax                                      |
|------------------------------------|--------------------------------------|--------------------------------------------|
| **Start a Container**              | Start a container                    | `docker container start nginx` |
| **Stop a Container**               | Stop a container                     | `docker container stop nginx` |
| **Restart a Container**            | Restart a container                  | `docker container restart nginx` |
| **Pause a Container**              | Pause a container                    | `docker container pause nginx` |
| **Unpause a Container**            | Unpause a container                  | `docker container unpause nginx` |
| **Block a Container**              | Block a container                    | `docker container wait nginx` |
| **Send SIGKILL**                   | Send SIGKILL to a container          | `docker container kill nginx` |
| **Send Another Signal**            | Send another signal to a container   | `docker container kill -s HUP nginx` |
| **Attach to a Container**          | Connect to an existing container     | `docker container attach nginx` |

---

## 4. Obtaining Container Information

| Command                            | Meaning                              | Syntax                                      |
|------------------------------------|--------------------------------------|--------------------------------------------|
| **Fetch Running Container Info**   | Fetch information from running containers | `docker ps` <br> `docker container ls` |
| **Fetch All Container Info**       | Fetch information from all containers | `docker container ls -a` <br> `docker ps -a` |
| **View Container Logs**            | View logs of a container             | `docker logs infinite` |
| **Follow Logs**                    | Follow container logs                | `docker container logs infinite -f` |
| **Inspect a Container**            | Inspect container details            | `docker container inspect infinite` <br> `docker container inspect --format '' $(docker ps -q)` |
| **View Container Events**          | View real-time container events      | `docker system events infinite` |
| **Find Public Ports**              | Find a container's public ports      | `docker container port infinite` |
| **View Running Processes**         | View running processes in a container | `docker container top infinite` |
| **Monitor Resource Usage**         | View live resource usage statistics  | `docker container stats infinite` |
| **Inspect File/Directory Changes** | Inspect file or directory changes    | `docker container diff infinite` |

---

## 5. Managing Images

| Command                            | Meaning                              | Syntax                                      |
|------------------------------------|--------------------------------------|--------------------------------------------|
| **List Images**                    | List all images                      | `docker image ls` |
| **Build Image (Current Directory)**| Build image from current directory   | `docker build` |
| **Build Image (GIT Repo)**         | Build image from GIT repository      | `docker build github.com/creack/docker-firefox` |
| **Tag and Build Image**            | Tag and build an image               | `docker build -t eon/infinite` |
| **Specify Build Context**          | Build from a specific Dockerfile     | `docker build -f myDockerfile` |
| **Remove an Image**                | Remove an image                      | `docker image rm nginx` |
| **Load Image from Tar Archive**    | Load an image from a tar archive     | `docker image load < ubuntu.tar.gz` |
| **Save Image to Tar Archive**      | Save an image to a tar archive       | `docker image save busybox > ubuntu.tar` |
| **View Image History**             | View history of an image             | `docker image history` |
| **Commit Container to Image**      | Create an image from a container     | `docker container commit nginx` |
| **Tag an Image**                   | Tag an image                         | `docker image tag nginx eon01/nginx` |
| **Push an Image**                  | Push an image to a registry          | `docker image push eon01/nginx` |

---

## 6. Networking

| Command                            | Meaning                              | Syntax                                      |
|------------------------------------|--------------------------------------|--------------------------------------------|
| **Create Overlay Network**         | Create a distributed network         | `docker network create -d overlay MyOverlayNetwork` |
| **Create Bridge Network**          | Create a bridge network              | `docker network create -d bridge MyBridgeNetwork` |
| **Remove a Network**               | Remove a network                     | `docker network rm MyOverlayNetwork` |
| **List Networks**                  | List all networks                    | `docker network ls` |
| **Inspect Network**                | Inspect network details              | `docker network inspect MyOverlayNetwork` |
| **Connect Container to Network**   | Connect container to a network       | `docker network connect MyOverlayNetwork nginx` |
| **Connect at Start**               | Connect container to a network at start | `docker container run -it -d --network=MyOverlayNetwork nginx` |
| **Disconnect from Network**        | Disconnect container from network    | `docker network disconnect MyOverlayNetwork nginx` |
| **Expose Ports**                   | Expose ports                         | `EXPOSE <port_number>` |

---

## 7. Cleaning Docker

| Command                            | Meaning                              | Syntax                                      |
|------------------------------------|--------------------------------------|--------------------------------------------|
| **Remove Running Container**       | Remove a running container           | `docker container rm nginx` |
| **Remove Container and Volume**    | Remove container and its volume      | `docker container rm -v nginx` |
| **Remove Exited Containers**       | Remove all exited containers         | `docker container rm $(docker container ls -a -f status=exited -q)` |
| **Remove Stopped Containers**      | Remove all stopped containers        | `docker container rm $(docker container ls -a -q)` |
| **Remove Image**                   | Remove a Docker image                | `docker image rm nginx` |
| **Remove Dangling Images**         | Remove dangling images               | `docker image rm $(docker image ls -f dangling=true -q)` |
| **Remove All Images**              | Remove all Docker images             | `docker image rm $(docker image ls -a -q)` |
| **Delete Untagged Images**         | Delete untagged images               | `docker image rm -f $(docker image ls | grep "^<none>" | awk "{print $3}")` |
| **Stop and Remove All Containers** | Stop and remove all containers       | `docker container stop $(docker container ls -a -q) && docker container rm $(docker container ls -a -q)` |
| **Remove Dangling Volumes**        | Remove all dangling volumes          | `docker volume rm $(docker volume ls -f dangling=true -q)` |
| **Remove Unneeded Resources**      | Remove unnecessary containers, images, networks, and volumes | `docker system prune -f` |
| **Clean Everything**               | Clean all Docker resources           | `docker system prune -a` |
