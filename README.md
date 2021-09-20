### Basic Docker commands 

docker pull nginx - pulls nginx image from docker hub
docker images - lists the images you have
docker run nginx:latest - running a container based on a tag
docker container ls - lists running containers
docker ps - lists running containers
docker stop <container id> - stops a running container but does not remove it
docker stop <container name> - stops a running container using its name without removing it
docker run -d nginx:latest - run a container in detach mode to avoid hunging
docker run -d -p 8080:80 nginx:latest - maps port 8080 on the host to port 80 inside the container
docker run -d -p 8080:80 -p 3000:80 nginx:latest - maps multiple ports from the host to port 80 inside the container
docker start <container_name> - runs an existing container
docker ps -a - list all containers even those that are running
docker rm <container id || container name> - deletes a container based on its id or name
docker ps -aq - select all container ids
docker rm $(docker ps -aq) - removes all containers using their ids but will not work if there is a running container.
docker rm -f <container name || container id> - removes a container whether its running or not.
docker run --name website -d -p 3000:80 -p 8080:80 nginx:latest - runs a container with a custom name
volumes - allow sharing data between host and containers and between containers
docker run --name website -v C:\Users\david\Desktop\website:/usr/share/nginx/html:ro -d -p 8080:80 nginx - 
		creates a read only volume that allows your files to be shared and then served by the container.
docker run --name website -v C:\Users\david\Desktop\website:/usr/share/nginx/html -d -p 8080:80 nginx - 
		creates a read and write volume that allows your files to be shared and then served by the container.
docker exec -it website bash - execute in interactive mode using bash
docker run --name website-copy --volumes-from website -d -p 8081:80 nginx - 
		runs a container called website-copy that shares files from website
Dockerfile - allows you to create custom images
docker build --tag website:latest . - 
		creates a custom image with your own project files from existing image using 
		Dockerfile eliminating the need for volumes and ensure you are inside the working directory
alpine - reduces the size of the images
docker pull node:lts-alpine - creates the latest node image of alpine
docker image rm <image id> - removes a docker image
Tags, versioning and tagging - allows you to control image version

docker tag amigoscode-website:latest amigoscode-website:1 - 
		creates a tag denoting the current version from the latest tag that always contains the latest changes
docker tag amigoscode-website:latest amigoscode-website:2 -
		creates version 2 after making changes using latest.
docker registry - a server where you can host your images with either public or private access
docker push springbootguru/website:1 - pushes an image version to docker hub
docker pull springbootguru/website - pulls your latest image if version not specified
docker inspect <container id || container name> - gives you full information of the container as json format
docker logs <container id || container name> - gives you the logs of the container
docker exec -it <container id> /bin/sh - getting inside a running node container





