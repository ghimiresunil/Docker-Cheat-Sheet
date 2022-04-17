# Docker Cheatsheet By [Sunil Ghimire](https://sunilghimire.com.np)

Are you finding difficulty remembering all the commands that you need in order to work with Docker?

Guys, don’t worry! This Docker cheat sheet will give you a quick reference to the basics of Docker that you must know to get started with it.

It is designed for those who have already started learning Docker but need a handy reference to recall the concepts that they have learned

![docker_container_architecture](https://user-images.githubusercontent.com/40186859/163715318-258c12df-9361-4e63-afb6-80986b3f60f9.png)

## Introduction

The Docker tool was introduced to make it easier for developers to create, deploy, and run applications using containers. Containers allow the packaging of your application (and everything that you need to run it) in a “container image”. Inside a container you can include a base operating system, libraries,
files and folders, environment variables, volume mount-points, and your application binaries.

A “container image” is a template for the execution of a container — It means that you can have multiple containers running from the same image, all sharing the same behavior, which promotes the scaling and distribution of the application. These images can be stored in a remote registry to ease the distribution.

Once a container is created, the execution is managed by the container runtime. You can interact with the container runtime through the `“docker”` command. 

### General Usage
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




