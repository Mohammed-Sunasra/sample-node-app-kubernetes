## Overview

This sample repo contains the source code for a bunch of dummy apps communicating with each other. The repo also contains the source code for the kubernetes objects required to deploy these apps/services on a kubernetes cluster.

## Usage

Make sure minikube is installed and up and running before executing the below commands using

```
minikube status
minikube start(run only if minikube is not up and running)
```

Create deployments:

```
kubectl apply -f users-deployment.yaml -f tasks-deployment.yaml -f auth-deployment.yaml -f frontend-deployment.yaml
```

Create services:

```
kubectl apply -f users-service.yaml -f tasks-service.yaml -f auth-service.yaml -f frontend-service.yaml
```

Check all pods and running and healthy using

```
kubectl get pods
```

Run front-end service

```
minikube service frontend-service
```

## Images

Below images are already pushed and publicly available on DockerHub

- mohammedsunasra13/k8-3tier-demo-auth-app:v1 - Contains source code for the auth app located in the auth-api folder
- mohammedsunasra13/k8-3tier-demo-users-app:v1 - Contains source code for the users app located in the users-api folder
- mohammedsunasra13/k8-3tier-demo-tasks-app:v2 - Contains source code for the tasks app located in the tasks-api folder

## Architecture

![App architecture](images/architecture.png)

1. The Users API/Service will be accessible from outside the cluster
2. The Auth API/Service will not be accessible from outside the cluster as it's an internal only service only used by the applications for authentication
3. The tasks API/Services will be accessible from outside the cluster
