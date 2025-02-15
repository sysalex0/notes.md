# kubectl

## Generic command
### Show details of a specific resource or group of resources
```shell
kubectl describe [kind] [resource_name]
```
### List all resource of a kind
```shell
kubectl get [kind]s
kubectl get [kind_short_form]
```
### Check yaml fields
explain the kubernetes kind object fields
```shell
kubectl explain [kind_field_path]
kubectl explain service.spec.type
```
check apiVersion for the resources
```sh
kubectl explain [kind]
```
### create resource by yaml
```shell
kubectl create -f <yaml_filename>
```
### Creates and updates resources in a cluster recursively by file with path
```shell
kubectl apply -R -f [path]
```
### Update resources command
This command replaces an existing resource with a new definition maintains the resource's history
```sh
kubectl replace -f [resouce.yaml]
```
### Switch namespace
```sh
kubectl config set-context --current --namespace=my-namespace
```

## Delete command
### Delete resource by kind  
```shell
kubectl delete [kind] --all 
```
Delete all resources
```shell
kubectl delete all --all
```

## Pod related command
### create pod yaml template
```shell
kubectl run [name] --image [image_name] --dry-run client -o yaml > [filename].yaml
```
### Start pod using a different command and custom arguments
```sh
kubectl run nginx --image=nginx --command -- <cmd> <arg1> ... <argN>
```
### modify pod properties
Some properties can be edited by command
- spec.containers[*].image
- spec.initContainers[*].image
- spec.activeDeadlineSeconds
- spec.tolerations
- spec.terminationGracePeriodSeconds 
```sh
kubectl edit pod [name]
```

## ReplicaSet related command
### Scale related command
```sh
kubectl replace -f [resouce.yaml]
kubectl scale --replicas=6 <replicaSet_name>
kubectl scale --replicas=6 -f <replicaSet_yml>
```

## Service related command
### create service to expose pod with type: ClusterIp
```sh
kubectl expose pod [pod_name] --port=[port_number] --name [service_name]
```
### expose the pod as type ClusterIp when creating pod 
```sh
kubectl expose pod [pod_name] --port=[port_number] --name [service_name] --expose=true
```

## ConfigMap related command
create config map with literal value
```sh
kubectl create configmap [name] --from-literal=key1=config1 --from-literal=key2=config2
```

## Secret related command
create secret with literal value
```sh
kubectl create secret [name] generic --from-literal=key1=val1

## Execute command directly
### Attach the bash of a pod
```shell
kubectl exec -it [pod_id] -- bash
```

## Taints and Tolerations
Taints a node
```sh
kubectl taint nodes node-name key=value:[taint-effect]
```
Untaints a node, add a minus side at the taints command
```sh
kubectl taint nodes node-name key=value:[taint-effect]-
```

## Networking command
### Port forward to localhost port from a service
```shell
kubectl port-forward svc/[service_name] [host_machine_port]:[service_exposing_port]
```

## Troubleshooting command
### Debug by create new pod as database client
- -h is referring to the k8s service-metadata.name
- service spec.selector.xxx need to match pod-spec.template.metadata.labels.xxx
```shell
kubectl run -it --rm --image=mysql:8.0 --restart=Never mysql-client -- mysql -h [service_name] -p[password]
```
### Debug by install a light weight linux to interact with other pods in the cluster
```shell
kubectl run -i --tty alpine --image=alpine --restart=Never -- sh
```
