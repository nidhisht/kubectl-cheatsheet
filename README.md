# kubectl-cheatsheet
- [Introduction](#Introduction)
- [Namespace](#Namespace)
- [Pods](#Pods)
- [Replicasets](#Replicasets)
- [Deployment](#Deployment)
- [ConfigMaps](#ConfigMaps)
- [Secrets](#Secrets)
- [Imperative commands](#Imperative-commands)
- [SSH into container](#SSH-into-container)
- [Service Account](#ServiceAccount)
- [Nodes](#Nodes)
- [Label](#Label)
- [Selectors](#Selectors)
- [Taints and Tolerations](#Taints-Tolerations)
- [Logs](#Logs)
- [Monitoring](#Monitoring)
- [Rolling update and rollback](#Rolling-update-Rollback)
- [Dry run](#dry-run)
- [Alias](#Alias)


## Introduction
https://kubernetes.io/docs/reference/kubectl/quick-reference/

| Command | Purpose|
|----------|----------|
| kubectl get|  Get summarized view of resources. Use -o for custom formats like json, yaml  |
| kubectl describe| Get detailed information about a specific resource. Event & status section helpful for debugging  |
| kubectl create  | Creates a new resource. Fails if the resource already exists.  |
| kubectl apply | Creates or updates a resource.   |
| kubectl run | Creates & run single container pod on Kubernetes   |
| kubectl expose | Creates service to expose pod or deployment or replicaset on Kubernetes  |
| kubectl replace | Update an existing resource in a Kubernetes cluster  |

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
kubectl get cm
kubectl create configmap  webapp-config-map --from-literal=APP_COLOR=darkblue --from-literal=APP_OTHER=disregard
```


## Secrets
```
kubectl get secrets
kubectl create secret generic webapp-config-map --from-literal=password=nidhish --from-literal=host=example.com

# NOTE: Secrets are NOT encrypted, but encoded.
# NOTE: Run below command in Linux to encode/decode
echo -n 'nidhish' | base64
echo -n 'bmlkaGlzaA==' | base64 --decode
```


## Imperative-commands
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

## SSH-into-container
SSH into app container
```
# Get list of pods
kubectl get po

# SSH into a pod
kubectl exec -it <pod-name> -- /bin/sh

# check environment variable of the pod (Optional)
env

# Get user of running pod
kubectl exec ubuntu-sleeper -- whoami
```


## ServiceAccount
```
kubectl get serviceaccounts
kubectl get sa
kubectl create serviceaccount dashboard-sa
kubectl create token dashboard-sa
```

## Nodes
```
kubectl get nodes
kubectl get no
kubectl get no -o wide
```

## Label
```
kubectl label nodes node01 color=blue
```

## Selectors
```
kubectl get all --selector env=prod
kubectl get po --selector env=prod --selector=bu=finance --selector tier=frontend
```

## Taints-Tolerations
```
# Add taint to a node (Example: node01)
kubectl taint nodes node01 spray=mortein:NoSchedule

# Remove taint from node (Example: control-plane)
kubectl taint nodes control-plane node-role.kubernetes.io/control-plane:NoSchedule-
```

## Logs
```
kubectl get logs <pod-name>

# Get live streaming of logs
kubectl get logs <pod-name> -f
```

## Monitoring
```
kubectl apply -f https://github.com/kubernetes-sigs/metrics-server/releases/latest/download/components.yaml

kubectl top pods
kubectl top nodes
```

## Rolling-update-Rollback
Deployment Strategy
1) Recreate - Delete and recreate deployments, causing downtime..
2) Rolling Update - This is the default deployment strategy. It upgrades one instance at a time—bringing it down, completing the upgrade, and then proceeding to the next. This ensures zero downtime.
```
# Check the rollout status of a deployment
kubectl rollout status deployment/<deployment-name>

# Check the rollout history of a deployment
kubectl rollout history deployment/<deployment-name>

# Rollback the deployment
kubectl rollout undo deployment/<deployment-name>
```

## dry-run
```
kubectl run nginx --image=nginx --dry-run=client -o yaml
```

## Alias
```
# Set temporary alias on Windows Command Prompt
doskey k=kubectl
```


