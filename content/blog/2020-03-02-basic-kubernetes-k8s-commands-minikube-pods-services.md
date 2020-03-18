---
title: Basic Kubernetes (K8s) Commands | Minikube | Pods | Services
date: 2020-03-02T21:47:16.593Z
description: 'Basic Kubernetes (K8s) Commands '
---
# Kubernetes Basics

Using minikube to create a single node cluster

## Check if minikube is installed

```bash
minikube version
```

## Start the cluster

```bash
minikube start
```

## Check if kubectl is installed

```bash
kubectl version
```

## Check cluster details

```bash
kubectl cluster-info
```

## View nodes in the cluster

```bash
kubectl get nodes
```

## Deploy an app 

```bash
kubectl create deployment kubernetes-bootcamp --image=gcr.io/google-samples/kubernetes-bootcamp:v1
```

## List your deployment

```bash
kubectl get deployments
```

## Check existing pods

```bash
kubectl get pods
```

```bash
kubectl get pods -o wide
```

## Describe pods

```bash
kubectl describe pods
```

## Check logs of a container running in pod

```bash
kubectl logs $POD_NAME
```

## Execute command directly inside container running in a pod

```bash
kubectl exec $POD_NAME env
```

## Start a bash session in a pod container

```bash
kubectl exec -ti $POD_NAME bash
```

To close your container connection type ```exit```.

## List current services from your cluster

```bash
kubectl get services
```

## Create a new service and expose it to external traffic with NodePort as paramter

```bash
kubectl expose deployment/kubernetes-bootcamp --type="NodePort" --port 8080
```

## Describe a service

```bash
kubectl describe services/kubernetes-bootcamp
```

## Test your app on the externally exposed port

```bash
curl $(minikube ip):$NODE_PORT
```

## Query list of pods using label

```bash
kubectl get pods -l run=kubernetes-bootcamp
```

## Query list of services using label

```bash
kubectl get services -l run=kubernetes-bootcamp
```

## Apply a new label to the object

```bash
kubectl label pod $POD_NAME app=v1
```

## Deleting a service

```bash
kubectl delete service -l run=kubernetes-bootcamp
```

## Scale up the service

```bash
kubectl scale deployments/kubernetes-bootcamp --replicas=4
```

## Scale down the service

```bash
kubectl scale deployments/kubernetes-bootcamp --replicas=2
```

## Rolling update, Update the image of your application

```bash
kubectl set image deployments/kubernetes-bootcamp kubernetes-bootcamp=jocatalin/kubernetes-bootcamp:v2
```

## Confirm an update

```bash
kubectl rollout status deployments/kubernetes-bootcamp
```

## Rollback an update

```bash
kubectl rollout undo deployments/kubernetes-bootcamp
```