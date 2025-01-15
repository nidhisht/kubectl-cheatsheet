# kubectl-cheatsheet

| Command | Purpose|
|----------|----------|
| kubectl get|  Provides a summarized view of resources. Custom Output using -o  |
| kubectl describe| Provides detailed information about a specific resource. Event & status section helpful for debugging  |
| kubectl create  | Creates a new resource. Fails if the resource already exists.  |
| kubectl apply | Creates or updates a resource.   |


## Pods
```
kubectl get pods
kubectl get po
kubectl delete pod <pod-name>
kubectl describe pod <pod-name>
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
