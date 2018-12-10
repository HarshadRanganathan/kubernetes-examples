# MULTICONTAINER APP

![multicontainer_overview](images/multicontainer_overview.png?raw=true)

## Pre-Requisites

Configure postgres password as a secret

```
kubectl create secret generic pgpassword --from-literal PG_PASSWORD=postgres_password
```

## Create Resources

To create the resources run below command
```
kubectl apply -f .
```

## Deploy Ingress Controller

```
kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/master/deploy/mandatory.yaml
```

If you are using minikube enable ingress
```
minikube addons enable ingress
```

[Check provider specific steps](https://kubernetes.github.io/ingress-nginx/deploy/)

## Access Webpage

Get the cluster ip and access the webpage at http://<cluster_ip>

```
kubectl cluster-info
```