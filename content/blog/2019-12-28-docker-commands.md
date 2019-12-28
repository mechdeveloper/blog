---
title: Basic Docker Commands | Images | Containers
date: 2019-12-28T17:51:27.725Z
description: List of common docker commands
---
# Docker Commands

### Check Docker Version
```bash
docker version
```
### Check the detailed information
```
docker info
```

## Docker commands - Images
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
### Check image history (layers in an image)
```
docker history <<imagename>>
docker history nginx
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

## Docker Commands - Containers
### List running containers
```
docker ps
```
### List all containers (This includes containers in all state)
```
docker ps -a
```
### Inspect container object
```
docker inspect <<containername/containerid>>
docker inspect cntnginx
```
### Print the stats for a running container 
```
docker stats <<containername/containerid>>
docker stats cntnginx
```
### Pause a running container
```
docker pause <<containername/containerid>>
docker pause cntnginx
```
### Unpause a paused container
```
docker unpause <<containername/containerid>>
docker unpause cntnginx
```
### Kill a running container
```
docker kill <<containername/containerid>>
docker kill cntnginx
```
### Start a killed container
```
docker start <<containername/containerid>>
docker start cntnginx
```
### Stop a running container
```
docker stop <<containername/containerid>>
docker stop cntnginx
```
### Delete a container
```
docker rm <<containername/containerid>>
docker rm cntnginx
```
### To remove all stopped containers
```
docker container prune
```
### Export a container as an image (.tar file)
```
docker export <<containername/contianerid>> > <<filename>>.tar
docker run --name newnginxcontainer -d nginx
docker export newnginxcontainer > test.tar
```
### Import an exported container image (.tar file)
```
docker import <<remoteurl/imagename.tar>>
docker import test.tar
```
