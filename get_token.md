## Get permanent Token

```bash
#!/bin/sh
kubectl config set-cluster mycluster.icp --server=https://192.168.27.199:8001 --insecure-skip-tls-verify=true
kubectl config set-context mycluster.icp-context --cluster=mycluster.icp
kubectl config set-credentials admin --token=$(kubectl get secret default-token-cwq97 -o jsonpath={.data.token} | base64 -d)
kubectl config set-context mycluster.icp-context --user=admin --namespace=default
kubectl config use-context mycluster.icp-context



```


## Kubectl without credentials
```
kubectl -s 127.0.0.1:8888 -n kube-system get pods

kubectl -s 127.0.0.1:8888 get pods

```