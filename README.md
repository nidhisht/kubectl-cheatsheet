# kubectl-cheatsheet
https://kubernetes.io/docs/reference/kubectl/quick-reference/

| Command | Purpose|
|----------|----------|
| kubectl get|  Provides a summarized view of resources. Use -o for custom formats like json, yaml  |
| kubectl describe| Provides detailed information about a specific resource. Event & status section helpful for debugging  |
| kubectl create  | Creates a new resource. Fails if the resource already exists.  |
| kubectl apply | Creates or updates a resource.   |
| kubectl run | Creates & run single container pod on Kubernetes   |
| kubectl expose | Creates service to expose pod or deployment or replicaset on Kubernetes  |

## Namespace
```
kubectl get namespace
kubectl get ns
kubectl create namespace dev-ns
```


## Pods
```
kubectl get pods
kubectl get pods -o wide
kubectl get po
kubectl delete pod <pod-name>
kubectl describe pod <pod-name>
kubectl get pods --all-namespaces
kubectl run redis --image=redis
```

## Replicasets
```
kubectl get replicasets
kubectl get rs
kubectl get replicaset <replicaset-name> -o yaml
kubectl describe replicaset <replicaset-name>
kubectl create -f replicaset-definition.yaml
kubectl apply -f replicaset-definition.yaml
kubectl edit replicaset <replicaset-name>
kubectl scale replicaset <replicaset-name> --replicas=5
kubectl scale rs <replicaset-name> --replicas=5
```


## Deployment
```
kubectl get deployment
kubectl get deploy
kubectl create deployment <deployment-name> --image=<image-name> --replicas=3
```

## ConfigMaps
```
kubectl get configmaps
kubectl create configmap  webapp-config-map --from-literal=APP_COLOR=darkblue --from-literal=APP_OTHER=disregard
```



## Imperative commands
```
# create a pod with redis image
kubectl run redis --image=redis

# Create a pod with name as redis, image as redis:alpine and label labelname=labelvalue
kubectl run redis -l labelkey=labelvalue --image=redis:alpine

# Create a service redis-service to expose the redis application within the cluster on port 6379
kubectl expose pod redis --port=6379 --name redis-service

# Create a deployment named webapp using the image kodekloud/webapp-color with 3 replicas
kubectl create deployment webapp --image=kodekloud/webapp-color --replicas=3

# Create a new namespace called dev-ns
kubectl create namespace dev-ns

# Create a pod called httpd using the image httpd:alpine in the default namespace. Next, create a service of type ClusterIP by the same name (httpd). The target port for the service should be 80
kubectl run httpd --image=httpd:alpine --port=80 --expose
```

## SSH into running container
```
# Get list of pods
kubectl get po

# SSH into a pod
kubectl exec -it <pod-name> -- /bin/sh

# check environment variable of the pod (Optional)
env
```
