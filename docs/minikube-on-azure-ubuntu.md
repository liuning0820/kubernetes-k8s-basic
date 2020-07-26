# Play With K8S using minikube Ubuntu Linux

## What is minikube

minikube implements a local Kubernetes cluster on macOS, Linux, and Windows.

## Install minikube

See guide at <https://minikube.sigs.k8s.io/docs/start/>

The sample script to [install minikube on ubuntu ](../scripts/install-minikube-linux.sh)


## Start minikube

Create and start the Kubernetes cluster, by running the minikube start command

```sh

sudo minikube start --vm-driver=none
# the 'none' driver must be run as the root user
# For non-root usage, try the newer 'docker' driver
minikube start --vm-driver=docker
sudo minikube status

minikube addons list
# enable dashboard

sudo minikube addons enable dashboard
# or 
minikube dashboard

# or 
minikube dashboard --url



```

### Verify

```sh

sudo kubectl version

# Cluster details
sudo kubectl cluster-info
sudo kubectl get nodes

```

### Enable Nginx Ingress controller

```sh
minikube addons enable ingress

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
