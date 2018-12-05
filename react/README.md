# React App

Pulls `stephengrider/multi-client` image for the container.

## Create Pod

```
kubectl apply -f client-pod.yaml
```

## Create Service

```
kubectl apply -f client-node-port.yaml
```

To view the status of pods and services configured, run below commands:
```
kubectl get pods
kubectl get services
```

Get Kubernetes master IP to access the web app
```
kubectl cluster-info
```

Access the app at http://<master_ip>:31515
