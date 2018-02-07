### CALICO Policy

```
docker run -v /root:/data --entrypoint=cp ibmcom/calico-ctl:v1.4.0 /calicoctl /data
sudo cp /root/calicoctl /usr/local/bin/ 
export ETCD_CERT_FILE=/etc/cfc/conf/etcd/client.pem
export ETCD_CA_CERT_FILE=/etc/cfc/conf/etcd/ca.pem
export ETCD_KEY_FILE=/etc/cfc/conf/etcd/client-key.pem
export ETCD_ENDPOINTS=https://mycluster.icp:4001


```

```yaml
kind: NetworkPolicy
apiVersion: extensions/v1beta1
metadata:
  name: default-deny
  namespace: policy-demo
spec:
  podSelector:
    matchLabels: {}




kind: NetworkPolicy
apiVersion: extensions/v1beta1
metadata:
  name: default-deny
  namespace: policy-demo
spec:
  egress:
  - action: allow
    destination: {}
    source: {}
  ingress:
  - action: deny
    destination: {}
    source: {}
    
    
        
 
 
kind: NetworkPolicy
apiVersion: extensions/v1beta1
metadata:
  name: default-deny
  namespace: policy-demo
spec:
  podSelector:
    matchLabels: {}
  policyTypes:
  - Egress
  - Ingress 
  
  

apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  name: allow-egress-to-advance-policy-ns
  namespace: advanced-policy-demo
spec:
  podSelector:
    matchLabels: {}
  policyTypes:
  - Egress
  egress:
  - to:
    - podSelector:
        matchLabels:
          run: nginx
          
          
            
  
    
kind: NetworkPolicy
apiVersion: extensions/v1beta1
metadata:
  name: access-nginx
  namespace: policy-demo
spec:
  podSelector:
    matchLabels:
      run: nginx
  ingress:
    - from:
      - podSelector:
          matchLabels:
            run: access
```