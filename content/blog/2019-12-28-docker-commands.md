---
title: Docker Commands
date: 2019-12-28T17:51:27.725Z
description: List of common docker commands
---
# Docker Commands

## Check Docker Version  and Info
```bash
docker version
```
```
docker info
```
## Docker command - Images
### Search an image in Docker hub
```
docker search <<imagename>> | head -20
docker search ubuntu | head -20
#  will search ubuntu images in the dockerhub and limit the search result to only 20 
```
### Pull and Image from Docker hub
```
docker pull <<imagename>>
docker pull nginx
```
### Pull a specific version of an image
```
docker pull <<imagename>>:<<versiontag>>
docker pull busybox:1.24
```
### Verify Downloaded docker images
```
docker images
```
### Remove Docker images
```
docker rmi <<imagename>>
docker rmi nginx
```
### Dowload and run an image in docker container using run command
```
docker run <<imagename>>
docker run --name cntnginx -d nginx
# --name to specify a name for the running container. In this example, it is cntnginx
# -d to run the container in background (detached mode)
```


```
docker version
```
```
docker version
```
