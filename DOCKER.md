DOCKER



* Docker is a platform that helps us to build containers.
* 
* A container is a package of application and its dependencies in a single unit.
* 
* It is platform-independent.
* It works on any machine.





* It is portable.

\- The Docker image can be shared to any machines.



* It is lightweight.
* Very low overhead.

\- Creating, updating, and deleting the containers and images is very easy.





* A Docker image is an executable file that contains the instructions to build a container.





* A Docker container is an actually running instance while the Docker image is a static snapshot of the local development environment.







* docker run -it ubuntu   --> It will pull the image from Docker and will run it in interactive mode.



* Docker is similar to virtual machines but it is very lightweight as compared to virtual machines.







Docker commands:

* docker pull IMAGE\_NAME
* docker images
* docker run IMAGE\_NAME
* docker run -it IMAGE\_NAME
* docker stop CONT\_NAME or CONT\_ID
* docker start CONT\_NAME or CONT\_ID







To generate this message: Hello from Docker. Docker took the following steps:

1\. The Docker client contacted the Docker daemon.

2\. The Docker daemon pulled the `hello-world` image from the Docker Hub (arm 64v8).

3\. The Docker daemon created a new container from that image, which runs the executable that produces the output you are currently reading.

4\. The Docker daemon streamed that output to the Docker client, which sent it to your terminal.





The Docker image layers:

* container
* Layer 2
* layer 1
* base layer





Port binding:

When we map our host port with the container port, it is called port binding. For example: `docker run -p8080:3306 IMAGE\\\_NAME`





Docker virtualizes the application layer whereas the virtual machine virtualizes both the host OS kernel and the application layer of the system.



The virtual machine is compatible with any system as it virtualizes both the host OS kernel and application layer of the system.



And Docker has very low overhead as it only virtualizes the application layer. Due to its low overhead it is very lightweight



Docker Desktop adds a lightweight hypervisor layer in the system. which internally uses a light weight  linux distribution





Docker Desktop contains small Linux distributions virtual machines, which help us to run the containers on any machine.



Docker Compose :

Docker Compose is a tool for defining and running multi-container applications.





compose.yaml file

version: "3.8"

services:

mongo:

image: mongo

ports:

27017:27017

environment:

MONGO\_INITDB\_ROOT\_USERNAME:

admin

MONGO\_INITDB\_ROOT\_PASSWORD:

qwerty





Docker Compose

docker compose -f fileName.yaml up -d

docker compose -f fileName.yaml down





Dockerizing our App

Important Dockerfile instructions

FROM

WORKDIR

COPY

RUN

CMD

EXPOSE

ENV





FROM node

ENV MONGO\_DB\_USERNAME=admin \\

MONDO\_DB\_PWD=qwerty

RUN mkdir -p testapp

COPY./testapp

CMD \["node", "/testapp/server.js"]





Dockerizing our App

* docker build -t testapp:1.0 .









Docker Commands



IMAGES :

* List all Local images

docker images

* Delete an image

docker rmi <image\_name>

* Remove unused images

docker image prune

* Build an image from a Dockerfile

docker build -t <image\_name>:<version> . //version is optional

docker build -t <image\_name>:<version> . -no-cache //build without cache



CONTAINER :

* List all Local containers (running \& stopped)

docker ps -a

* List all running containers

docker ps

* Create \& run a new container

docker run <image\_name>

//if image not available locally, it’ll be downloaded from DockerHub

* Run container in background

docker run -d <image\_name>

* Run container with custom name

docker run - -name <container\_name> <image\_name>

* Port Binding in container

docker run -p<host\_port>:<container\_port> <image\_name>

* Set environment variables in a container

docker run -e <var\_name>=<var\_value> <container\_name> (or <container\_id)

* Start or Stop an existing container

docker start|stop <container\_name> (or <container\_id)

* Inspect a running container

docker inspect <container\_name> (or <container\_id)

* Delete a container

docker rm <container\_name> (or <container\_id)



TROUBLESHOOT :

* Fetch logs of a container

docker logs <container\_name> (or <container\_id)

* Open shell inside running container

docker exec -it <container\_name> /bin/bash

docker exec -it <container\_name> sh



DOCKER HUB :

* Pull an image from DockerHub

docker pull <image\_name>

* Publish an image to DockerHub

docker push <username>/<image\_name>

* Login into DockerHub

docker login -u <image\_name>

* Or

docker login

//also, docker logout to remove credentials

* Search for an image on DockerHub

docker search <image\_name>



VOLUMES :

* List all Volumes

docker volume ls

* Create new Named volume

docker volume create <volume\_name>

* Delete a Named volume

docker volume rm <volume\_name>

* Mount Named volume with running container

docker run - -volume <volume\_name>:<mount\_path>

* //or using - -mount

docker run - -mount type=volume,src=<volume\_name>,dest=<mount\_path>

* Mount Anonymous volume with running container

docker run - -volume <mount\_path>

* To create a Bind Mount

docker run - -volume <host\_path>:<container\_path>

//or using - -mount

docker run - -mount type=bind,src=<host\_path>,dest=<container\_path>



* Remove unused local volumes

docker volume prune //for anonymous volumes



NETWORK :

* List all networks

docker network ls

* Create a network

docker network create <network\_name>

* Remove a network

docker network rm <network\_name>

* Remove all unused networks

docker network prune

