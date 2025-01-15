# kubectl-cheatsheet

| Command | Resource | Purpose|
|----------|----------|----------|
| kubectl get pods | pod  | Get All Pods in the Current Namespace  |
| kubectl get replicasets  | replicasets  | Get All Replicasets in the Current Namespace  |
| kubectl get replicaset replicaset-name -o yaml  | replicasets  | Get replicaset output format as YAML  |

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
