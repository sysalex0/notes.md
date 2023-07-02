# kubectl

## Creates and updates resources in a cluster recursively by file with path
```shell
kubectl apply -R -f [path]
```

## List all resource of a kind
```shell
kubectl get [kind]s
kubectl get [kind_short_form]
```

## Delete resources
Delete resource by kind  
```shell
kubectl delete [kind] --all 
```
Delete all resources
```shell
kubectl delete all --all
```

## Show details of a specific resource or group of resources
```shell
kubectl describe [kind] [resource_name]
```

## Attach the bash of a pod
```shell
kubectl exec -it [pod_id] -- bash
```

## Debug by create new pod as database client
- -h is referring to the k8s service-metadata.name
- service spec.selector.xxx need to match pod-spec.template.metadata.labels.xxx
```shell
kubectl run -it --rm --image=mysql:8.0 --restart=Never mysql-client -- mysql -h [service_name] -p[password]
```

## Debug by install a light weight linux to interact with other pods in the cluster
```shell
kubectl run -i --tty alpine --image=alpine --restart=Never -- sh
```

## Port forward to localhost port from a service
```shell
kubectl port-forward svc/[service_name] [host_machine_port]:[service_exposing_port]
```