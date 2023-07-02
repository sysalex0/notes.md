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
kubectl run -it --rm --image=mysql:8.0 --restart=Never mysql-client -- mysql -h [service_name] -p[password]
```

## Debug by install a light weight linux to interact with other pods in the cluster
```
kubectl run -i --tty alpine --image=alpine --restart=Never -- sh
```

## Port forward to localhost port from a service
```
kubectl port-forward svc/[service_name] [host_machine_port]:[service_port]
```