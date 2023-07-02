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

## Get localhost url from a service
```
minikube service [service_name] --url
```

## Load the built image in host machine docker repository to kubernetes cluster
```shell
minikube image load login-app  
```

## [Windows] Allow Kubernetes read your local docker repository
Run this command to set ENV variable in your current shell
```
minikube docker-env
```
Execute the last line command from the result, to apply the changes according to the ENV variables
The command should like
```
@FOR /f "tokens=*" %i IN ('minikube -p minikube docker-env --shell cmd') DO @%i
```
Verify the effect by running `docker image ls` and `minikube image ls`, they should show the same images.

When you want to switch it back to local docker repository, simply restart the shell. As the ENV variables will drop after restart.

