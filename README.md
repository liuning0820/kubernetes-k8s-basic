# Kubernetes K8S Basic

<!-- TOC -->

- [Kubernetes K8S Basic](#kubernetes-k8s-basic)
    - [What's Kubernetes](#whats-kubernetes)
        - [Kubernetes Cluster](#kubernetes-cluster)
    - [Create Cluster - minikube](#create-cluster---minikube)
    - [Manage Cluster - kubectl](#manage-cluster---kubectl)
        - [Kubernetes Deployment](#kubernetes-deployment)
        - [Kubernetes Pods](#kubernetes-pods)
        - [Play Azure Kubernetes Service (AKS)](#play-azure-kubernetes-service-aks)

<!-- /TOC -->

## What's Kubernetes

Kubernetes 用于自动部署，扩展和管理容器化应用程序的开源系统。

- 生产级别的容器编排系统
- 数据中心OS
- 新生代的云平台

### Kubernetes Cluster

A Kubernetes cluster consists of two types of resources:

- The **Master** coordinates the cluster
- **Nodes** are the workers that run applications

## Create Cluster - minikube

- [play with minikube](./docs/minikube-on-azure-ubuntu.md)

## Manage Cluster - kubectl

kubectl is the Kubernetes Command Line Interface (CLI) client to manage Kubernetes cluster resources and applications.

[install-kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/)

```sh

# Check the installation
kubectl version

# view the cluster details
kubectl cluster-info
# view the nodes in the cluster
kubectl get nodes

```

### Kubernetes Deployment

```sh

# using kubectl to create deployment
kubectl create -f azure-vote.yaml
kubectl apply -f azure-vote.yaml
kubectl run Name --image=image [--port=port]
kubectl get deployments
```

### Kubernetes Pods

When you created a Deployment, Kubernetes created a Pod to host your application instance. A Pod is a Kubernetes abstraction that represents a group of one or more application containers (such as Docker), and some shared resources for those containers.

```sh

# list resources
kubectl get pods
# show detailed information about a resource
kubectl describe pods
# print the logs from a container in a pod
kubectl logs $POD_NAME
# execute a command on a container in a pod
kubectl exec -ti $POD_NAME bash

```

### Play Azure Kubernetes Service (AKS)

[AKS Tutorial](https://docs.microsoft.com/en-us/azure/aks/tutorial-kubernetes-deploy-application)

```sh
# install kubectl
az aks install-cli
# check kubectl version
kubectl version
# connect to cluster using kubectl
az aks get-credentials --resource-group aks-basic --name aks-basic-cluster
# verify connection to cluster
kubectl get nodes
# get the external IP of the service, open browser to test the app.
kubectl get service azure-vote-front
# Access Kubernetes dashboard with aks
az aks browse --resource-group aks-basic --name aks-basic-cluster

```
