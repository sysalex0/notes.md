# Minikube

## Start / Stop
```
minikube start
minikube stop
```

## Open Kubernetes dashboard
```
minikube dashboard
```

Get localhost url from a service
```
minikube service [service_name] --url
```

# kubectl

## Creates and updates resources in a cluster recursively by file with path
```
kubectl apply -R -f [path]
```

## List all pods / services
```
kubectl get pods
kubectl get svc OR kubectl get services
```

## Delete all resources
```
kubectl delete all --all
```

## Show details of a specific resource or group of resources 
```
kubectl describe [kind] [kind_name]
```

## Attach the bash of a pod
```
kubectl exec -it [pod_id] -- bash
```
## Debug by create new pod as database client
- -h is referring to the k8s service-metadata.name
- service spec.selector.xxx need to match pod-spec.template.metadata.labels.xxx
```
kubectl run -it --rm --image=mysql:8.0 --restart=Never mysql-client -- mysql -h login-db -ppassword
```

## Debug by install a light weight linux to interact with other pods in the cluster 
```
kubectl run -i --tty alpine --image=alpine --restart=Never -- sh
```

# kompose

## Convert the docker-compose.yml file to files that you can use with kubectl
```
kompose convert
```

# docker / docker-compose

# Encoding

## convert the string to base64
```
echo -n "[text_to_encode]" | base64
```