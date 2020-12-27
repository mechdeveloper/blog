---
title: Basic Docker Commands | Images | Containers
date: 2020-12-27T19:36:33.451Z
description: List of common docker commands for getting started with docker on
  windows. Perfect for beginners learning or getting started with docker
---
![Docker Image](/img/docker-1583867936176-2300.jpg)

# Docker Commands

1. Check Docker Version

```bash
docker version
```

2. Check the detailed information of Docker installed

```
docker info
```

## Docker commands - Images

3. Search an image in Docker hub

```
docker search ubuntu
```

```bash
docker search <<imagename>> | head -20
docker search ubuntu | head -20
#  will search ubuntu images in the dockerhub and limit the search result to only 20
```

Note: head command works on bash terminal, for PowerShell terminal in windows use `select -first 10`
```PowerShell 
docker search ubuntu | select -first 10
```

4. Pull and Image from Docker hub

```
docker pull <<imagename>>
docker pull nginx
```

5. Check image history (layers in an image)

```
docker history <<imagename>>
docker history nginx
```

6. Pull a specific version of an image

```
docker pull <<imagename>>:<<versiontag>>
docker pull busybox:1.24
```

7. Verify Downloaded docker images

```
docker images
```

8. Remove Docker images

```
docker rmi <<imagename>>
docker rmi nginx
```

9. Download and run an image in docker container using run command

```
docker run <<imagename>>
docker run --name cntnginx -d nginx
# --name to specify a name for the running container. In this example, it is cntnginx
# -d to run the container in background (detached mode)
```

## Docker Commands - Containers

10. List running containers

```
docker ps
```

11. List all containers (This includes containers in all state)

```
docker ps -a
```

12. Inspect container object

```
docker inspect <<containername/containerid>>
docker inspect cntnginx
```

13. Print the stats for a running container 

```
docker stats <<containername/containerid>>
docker stats cntnginx
```

14. Pause a running container

```
docker pause <<containername/containerid>>
docker pause cntnginx
```

15. Unpause a paused container

```
docker unpause <<containername/containerid>>
docker unpause cntnginx
```

16. Kill a running container

```
docker kill <<containername/containerid>>
docker kill cntnginx
```

17. Start a killed container

```
docker start <<containername/containerid>>
docker start cntnginx
```

18. Stop a running container

```
docker stop <<containername/containerid>>
docker stop cntnginx
```

19. Delete a container

```
docker rm <<containername/containerid>>
docker rm cntnginx
```

20. To remove all stopped containers

```
docker container prune
```

21. Export a container as an image (.tar file)

```
docker export <<containername/contianerid>> -o <<filename>>.tar
docker run --name newnginxcontainer -d nginx
docker export newnginxcontainer -o test.tar

# Note: You must have permissions on the folder where you are saving the test.tar
# use `chmod 777 ./` for permissions in case if you are facing an permission denied error.
```

22. Import an exported container image (.tar file)

```
docker import <<remoteurl/imagename.tar>>
docker import test.tar
```
