---
title: How to Clean Windows Server 2016 OS Docker Host ?
date: 2021-01-19T12:36:14.090Z
description: Many times we have requirement or we want to clean the docker
  windows server host to start docker services from a clean state. This article
  will help you in that process.
---
# Windows Server 2016 OS | Docker Host - Cleanup

![Docker](/img/docker-1583867936176-2300.jpg "Docker")

## Step 1: Make sure host is not in swarm mode

```PowerShell
docker swarm leave --force
```

## Step 2: Remove all container networks on the system

```PowerShell
docker network prune -f
```

## Step 3: Remove All containers on the system

```PowerShell
docker container prune -f
```

## Step 4: Stop docker service

```PowerShell
net stop docker  
```

## Step 5: Clean up networking components on the container host

```PowerShell
Get-NetNatStaticMapping | Remove-NetNatStaticMapping
Get-NetNat | Remove-NetNat
Get-ContainerNetwork | Remove-ContainerNetwork
Stop-Service hns 
del C:\ProgramData\Microsoft\Windows\HNS\HNS.data
Restart-Service hns
```

## Step 6: Change StartupType of docker service to manual

```PowerShell
Get-Service -Name docker | fl *
Set-Service -Name docker -StartupType Manual
Get-Service -Name docker | fl *
```

## Step 7: Restart host

```PowerShell
Restart-Computer
```

## Step 8: Change StartupType of docker service to automatic

```PowerShell
Get-Service -Name docker | fl *
Set-Service -Name docker -StartupType Automatic
Get-Service -Name docker | fl *
```

Note: You can also remove/uninstall unused/disabled network adapters of Windows Server 2016 OS host from Device Manager

Now your host machine is in clean state and you can start your docker windows service again 

```PowerShell
net start docker
```