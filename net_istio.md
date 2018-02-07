### ISTIO

#### Get Install

```bash
curl -L https://git.io/getLatestIstio | sh -
export PATH="$PATH:/home/demo/istio-0.4.0/bin"
sudo cp bin/istioctl /usr/local/bin/
istioctl 

cd istio-0.4.0/
```

#### Create Namespace
```
istio-system
```

#### Install

```bash
cd istio-0.4.0/
kubectl apply -f install/kubernetes/istio.yaml
kubectl apply -f install/kubernetes/istio-initializer.yaml

kubectl apply -f install/kubernetes/addons/prometheus.yaml 
kubectl apply -f install/kubernetes/addons/grafana.yaml

kubectl get svc -n istio-system
kubectl get pods -n istio-system

kubectl -n istio-system get svc istio-ingress


```

Remove

```bash

kubectl delete -f install/kubernetes/addons/grafana.yaml
kubectl delete -f install/kubernetes/addons/prometheus.yaml

kubectl delete -f install/kubernetes/istio-initializer.yaml
kubectl delete -f install/kubernetes/istio.yaml
```



#### EXAMPLES
**HELLOWORLD**

```bash

kubectl apply -f istio-0.4.0/samples/helloworld/helloworld.yaml 

echo $(kubectl get deployment helloworld-v1 -o jsonpath='{.metadata.annotations.sidecar\.istio\.io\/status}')

echo $(kubectl get deployment helloworld-v2 -o jsonpath='{.metadata.annotations.sidecar\.istio\.io\/status}')

curl http://192.168.27.199:31461/hello

for i in `seq 1 2000`; do curl http://192.168.27.199:31461/hello; done

kubectl delete -f istio-0.4.0/samples/helloworld/helloworld.yaml 

```

**ROUTING RULES**

```yaml
nano routingrule.yaml
```

```yaml

apiVersion: config.istio.io/v1alpha2
kind: RouteRule
metadata:
  name: helloworld-default
  namespace: default
spec:
  destination:
    name: helloworld
  precedence: 1
  route:
  - labels:
      version: v1
    weight: 90
  - labels:
      version: v2
    weight: 10
```


```bash

istioctl create -f routingrule.yaml

istioctl replace -f routingrule.yaml

for i in `seq 1 200000`; do curl http://192.168.27.199:31461/hello; done

istioctl delete routerules helloworld-default --namespace default
```






HTTPBIN

```bash
kubectl apply -f samples/httpbin/httpbin.yaml 

echo $(kubectl get deployment httpbin -o jsonpath='{.metadata.annotations.sidecar\.istio\.io\/status}')



kubectl apply -f samples/sleep/sleep.yaml

echo $(kubectl get deployment sleep -o jsonpath='{.metadata.annotations.sidecar\.istio\.io\/status}')

export SOURCE_POD=$(kubectl get pod -l app=sleep -o jsonpath={.items..metadata.name})
kubectl exec -it $SOURCE_POD bash
```


```bash

kubectl -n istio-system get po -l istio=ingress -o jsonpath='{.items[0].status.hostIP}'

kubectl -n istio-system get svc istio-ingress
```


EGRESS

```bash
nano egress.yaml

apiVersion: config.istio.io/v1alpha2
kind: EgressRule
metadata:
  name: google-egress-rule
spec:
  destination:
    service: www.google.com
  ports:
    - port: 443
      protocol: https


istioctl create -f egress.yaml 




apiVersion: extensions/v1beta1
kind: Deployment
metadata:
  name: sleep
spec:
  replicas: 1
  template:
    metadata:
      labels:
        app: sleep
    spec:
      containers:
      - name: sleep
        image: tutum/curl
        command: ["/bin/sleep","infinity"]
        imagePullPolicy: IfNotPresent

export SOURCE_POD=$(kubectl get pod -l app=sleep -o jsonpath={.items..metadata.name})
kubectl exec -it $SOURCE_POD bash

curl http://www.google.com:443

for i in `seq 1 200000`; do curl http://www.google.com:443; done


istioctl delete -f test.yaml --namespace default


```


```yaml
apiVersion: extensions/v1beta1
kind: Ingress
metadata:
  name: simple-ingress
  annotations:
    kubernetes.io/ingress.class: istio
spec:
  rules:
  - http:
      paths:
      - path: /status/.*
        backend:
          serviceName: httpbin
          servicePort: 8000
      - path: /delay/.*
        backend:
          serviceName: httpbin
          servicePort: 8000
```



```yaml
apiVersion: extensions/v1beta1
kind: Ingress
metadata:
  name: istio-test-ingress
  annotations:
    ingress.kubernetes.io/rewrite-target: /
spec:
  rules:
  - host: test
    http:
      paths:
      - backend:
          serviceName: istio-ingress
          servicePort: 30536
```