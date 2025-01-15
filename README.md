# kubectl-cheatsheet

| Command | Resource | Purpose|
|----------|----------|----------|
| kubectl get pods | pod  | Get All Pods in the Current Namespace  |
| kubectl get replicasets  | replicasets  | Get All Replicasets in the Current Namespace  |
| kubectl get replicaset replicaset-name -o yaml  | replicasets  | Get replicaset output format as YAML  |

```
kubectl get pods
kubectl delete pod <pod-name>


kubectl get replicasets
kubectl get replicaset <replicaset-name> -o yaml
kubectl create -f replicaset-definition.yaml
kubectl apply -f replicaset-definition.yaml
kubectl edit replicaset <replicaset-name>
kubectl scale replicaset <replicaset-name> --replicas=5
```
