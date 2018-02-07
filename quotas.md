## <a name="quotas"></a>Quotas

```yaml
apiVersion: v1
kind: ResourceQuota
metadata:
  name: compute-resources
  namespace: devops
spec:
  hard:
    pods: "4"
    requests.cpu: "1"
    requests.memory: 1Gi
    limits.cpu: "2"
    limits.memory: 2Gi



apiVersion: v1
kind: ResourceQuota
metadata:
  name: object-counts
  namespace: devops
spec:
  hard:
    configmaps: "10"
    persistentvolumeclaims: "4"
    replicationcontrollers: "20"
    secrets: "10"
    services: "10"
    services.loadbalancers: "2"
```

```bash
kubectl get quota --namespace=devops

kubectl delete quota compute-resources --namespace devops

kubectl delete quota object-counts --namespace devops
```


## <a name="roles"></a>Roles

```bash
kubectl get clusterroles operate
kubectl describe clusterroles operate
kubectl describe clusterroles view
kubectl get clusterrolebindings
```

