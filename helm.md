## <a name="helm">HELM
https://raw.githubusercontent.com/niklaushirt/chartslocal/master/repo/stable/


## Image preload
```bash
sudo docker pull ibmcom/ucds:6.2.6.1.940532
sudo docker pull ibmcom/ucda:6.2.6.1.940532
sudo docker pull ibmcom/ucdr:6.2.6.1.940532
sudo docker pull bitnami/mariadb:10.1.26-r0
sudo docker pull bitnami/wordpress:4.8.1-r0
sudo docker pull bitnami/ghost:0.11.10-r2
sudo docker pull ibmcom/mq:9
sudo docker pull nginx
sudo docker pull nodered/node-red-docker:0.17.5
sudo docker pull ibmcom/cfc-jenkins-master:2.19.4-1.1
sudo docker pull tomcat:9.0
sudo docker pull ibmcom/datapower:7.6.0
sudo docker pull websphere-liberty:8.5.5.9
sudo docker pull ibmcom/transformation-advisor-db:1.1.0
sudo docker pull ibmcom/transformation-advisor-server
sudo docker pull ibmcom/transformation-advisor-ui
sudo docker pull gcr.io/google_containers/kubernetes-dashboard-amd64:v1.7.1
sudo docker pull rocket.chat:0.56
sudo docker pull sonarqube:6.5
sudo docker pull ibmcom/postgres:9.6.2
sudo docker pull sumologic/fluentd-kubernetes-sumologic:v1.4
sudo docker pull traefik:1.4.3
sudo docker pull bitnami/mariadb:10.1.29-r1
sudo docker pull bitnami/mongodb:3.4.10-r0
sudo docker pull ibmcom/websphere-traditional:latest
sudo docker pull ibmcom/websphere-liberty
sudo docker pull ibmcom/datapower:7.6.0
sudo docker pull ibmcom/ibmnode:8

sudo docker pull hybridcloudibm/dsx-dev-icp-dsx-core:v1.015
sudo docker pull hybridcloudibm/dsx-dev-icp-zeppelin:v1.015
sudo docker pull hybridcloudibm/dsx-dev-icp-jupyter:v1.015
sudo docker pull hybridcloudibm/dsx-dev-icp-rstudio:v1.015
sudo docker pull na.cumulusrepo.com/hcicp_dev/dsm-sidecar:0.3.0
sudo docker pull na.cumulusrepo.com/hcicp_dev/db2server_dec:11.1.2.2

sudo docker pull ibmcom/mb-tools:2.1.0
sudo docker pull ibmcom/mb-jenkins:2.1.0
sudo docker pull ibmcom/mb-jenkins-slave:2.5.2

sudo docker pull openliberty/open-liberty:latest

sudo docker pull ibmcom/icp-nodejs-sample:latest


sudo docker pull ibmcom/skydive:0.15.0
sudo docker pull elasticsearch:2


docker login mycluster.icp:8500

docker tag nginx mycluster.icp:8500/default/nginx
docker push mycluster.icp:8500/default/nginx



sudo docker pull istio/examples-helloworld-v1
sudo docker pull citizenstig/httpbin   

sudo docker pull istio/istio-ca:0.4.0
sudo docker pull istio/sidecar_initializer:0.4.0
sudo docker pull istio/pilot:0.4.0
sudo docker pull istio/proxy_debug:0.4.0
sudo docker pull istio/proxy_init:0.4.0
sudo docker pull istio/mixer:0.4.0

```