# Play With K8S using minikube on Azure Ubuntu VM

## What is minikube

minikube implements a local Kubernetes cluster on macOS, Linux, and Windows.

## Install minikube

[install minikube](https://minikube.sigs.k8s.io/docs/start/)

```sh

curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64 \
   && sudo install minikube-linux-amd64 /usr/local/bin/minikube

minikube version

```

## Start minikube

Create and start the Kubernetes cluster, by running the minikube start command

```sh

sudo minikube start --vm-driver=none
sudo minikube status
sudo minikube addons enable dashboard
sudo minikube dashboard --url


sudo kubectl version

# Cluster details
sudo kubectl cluster-info
# This command shows all nodes that can be used to host our applications.
kubectl get nodes

```

## Create a Deployment

```sh
docker build -t liuning0820/minikube-node-app .
docker login
sudo docker push liuning0820/minikube-node-app

sudo kubectl create deployment minikube-node-app --image=docker.io/liuning0820/minikube-node-app

```

## Access the app

```sh
kubectl expose deployment minikube-node-app --type=LoadBalancer --port=8080
sudo kubectl get services
```

## Clean up

Now you can clean up the resources you created in your cluster:

```sh
kubectl delete service minikube-node-app
kubectl delete deployment minikube-node-app
```

Optionally, stop the Minikube virtual machine (VM):

```sh
minikube stop
```

Optionally, delete the Minikube VM:

```sh

minikube delete

```

## Reference

- [hello-minikube](https://kubernetes.io/docs/tutorials/hello-minikube/)
- [minikube src](https://github.com/kubernetes/minikube)
- [kubernetes-basic](https://kubernetes.io/docs/tutorials/kubernetes-basics/)
