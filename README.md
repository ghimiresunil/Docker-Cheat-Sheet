# Docker Cheatsheet By [Sunil Ghimire](https://sunilghimire.com.np)

Are you finding difficulty remembering all the commands that you need in order to work with Docker?

Guys, don’t worry! This Docker cheat sheet will give you a quick reference to the basics of Docker that you must know to get started with it.

It is designed for those who have already started learning Docker but need a handy reference to recall the concepts that they have learned

![docker_container_architecture](https://user-images.githubusercontent.com/40186859/163715318-258c12df-9361-4e63-afb6-80986b3f60f9.png)

## 1. Introduction

The Docker tool was introduced to make it easier for developers to create, deploy, and run applications using containers. Containers allow the packaging of your application (and everything that you need to run it) in a “container image”. Inside a container you can include a base operating system, libraries,
files and folders, environment variables, volume mount-points, and your application binaries.

A “container image” is a template for the execution of a container — It means that you can have multiple containers running from the same image, all sharing the same behavior, which promotes the scaling and distribution of the application. These images can be stored in a remote registry to ease the distribution.

Once a container is created, the execution is managed by the container runtime. You can interact with the container runtime through the `“docker”` command. 

### A. General Usage
* Start a container in background 
```
$> docker run -d jenkins
```
* Start an interactive container 
```
$> docker run -it ubuntu bash
```
* Start a container automatically removed on stop 
```
$> docker run --rm ubuntu bash
```
* Export port from a container
```
$> docker run -p 80:80 -d nginx 
```
* Start a named container
```
$> docker run --name mydb redis 
```
* Restart a stopped container
```
$> docker start mydb 
```
* Stop a container
```
$> docker stop mydb 
```
* Add metadata to container
```
$> docker run -d \
label=traefik.backend=jenkins jenkins
```

### B. Build Images

* Build an image from Dockerfile in current directory
```
$> docker build --tag myimage . 
```
* Force rebuild of Docker image
```
$> docker build --no-cache . 
```
* Remove all unused images 
```
$> docker rmi $(docker images \
-q -f "dangling=true"
```

### C. Debug

* Run another process in running container
```
$> docker exec -it c7337 bash 
```
* Show live logs of running daemon container 
```
$> docker logs -f c7337 
```
* Show exposed ports of a container
```
$> docker port c7337 
```

### D. Volumes

* Create a local volume
```
$> docker volume create --name myvol
```
* Mounting a volume on container start
```
$> docker run -v myvol:/data redis
```
* Destroy a volume
```
$> docker volume rm myvol
```
* List volumes
```
$> docker volume ls
```
* Create a local network
```
$> docker network create mynet
```
* Attach a container to a network on start
```
$> docker run -d --net mynet redis
```
* Connect a running container from a network
```
$> docker network connect mynet c7337
```
* Disconnect container to a network
```
$> docker network disconnect mynet c7337
```

### E. Manage Containers

* List running containers
```
$> docker ps 
```
* List all containers ( running & stopped )
```
$> docker ps -a 
```
* Inspect containers metadatas
```
$> docker inspect c7337
```
* List local available images
```
$> docker images
```
* To delete all images:
```
$> docker rmi $(docker images -q)
```
* Delete all stopped containers
```
$> docker rm $(docker ps --ﬁlter status=exited -q)
```
* To clean an unused/dangling image:
```
$> docker image prune
```
* To remove an image that is not used in a container:
```
$> docker image prune -a
```
* To prune the entire system:
```
$> docker system prune
```
* List all containers with a specific label
```
$> docker ps --ﬁlter label=traeﬁk.backend
```
* Query a specific metadata of a running container
```
$> docker inspect -f '{{ .NetworkSettings.IPAddress }}' c7337
```

## 2. Lengend
* Image Name
```
redis, jenkins, nginx
```
* Container name or commit ID
```
mydb  #name
c7337 #commit id
```

## 3. Important

Some of the important terms to know about while using Docker containers are listed below:

* **Layer**: Read-only files to provision the system
* **Image**: Read-only layer that is the base of an image
* **Container**: A runnable instance of the image
* **Registry/hub**: A central place where images reside
* **Docker machine**: A VM to run Docker containers
* **Docker Compose**: A VM to run multiple containers as a system

# 4. Contribution
Contributions are very welcome! Please submit a pull request on GitHub.
