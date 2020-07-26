# Manage K8S Cluster with kubectl

## Create Namespace

```sh
kubectl create -f ../scripts/namespace-devops-dev.yaml

kubectl get namespaces

```

## Manage Context


```sh

CURRENT_CONTEXT=$(kubectl config view -o jsonpath='{.current-context}')
USER_NAME=$(kubectl config view -o jsonpath='{.contexts[?(@.name == "'"${CURRENT_CONTEXT}"'")].context.user}')
CLUSTER_NAME=$(kubectl config view -o jsonpath='{.contexts[?(@.name == "'"${CURRENT_CONTEXT}"'")].context.cluster}')
kubectl config set-context devops-dev --namespace=devops-dev --cluster=${CLUSTER_NAME} --user=${USER_NAME}
kubectl config use-context devops-dev

```