## <a name="net">Networking
### Ingress

192.168.27.199	icp.ibm.com
192.168.27.199	red.icp.ibm.com
192.168.27.199	dash.icp.ibm.com
192.168.27.199	monitoring.icp.ibm.com
192.168.27.199	icp



```yaml
apiVersion: extensions/v1beta1
kind: Ingress
metadata:
  name: nodered-ingress
  annotations:
    ingress.kubernetes.io/rewrite-target: /
spec:
  rules:
  - host: red.icp.ibm.com
    http:
      paths:
      - backend:
          serviceName: nodered
          servicePort: 1880
                    
          
          
apiVersion: extensions/v1beta1
kind: Ingress
metadata:
  name: dashboard-ingress
  annotations:
    ingress.kubernetes.io/rewrite-target: /
spec:
  rules:
  - host: dash.icp.ibm.com
    http:
      paths:
      - backend:
          serviceName: kubernetes-dashboard-kubernetes-dashboard
          servicePort: 80
```