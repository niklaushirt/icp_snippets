## <a name="cam"></a>Install CAM

```bash
wget https://clis.ng.bluemix.net/download/bluemix-cli/0.6.4/linux64

tar xvfz linux64

cd Bluemix_CLI/
sudo ./install_bluemix_cli

wget https://192.168.27.199:8443/api/cli/icp-linux-amd64 --no-check-certificate

bx plugin install install_bluemix_cli

wget https://192.168.27.199:8443/api/cli/icp-linux-amd64 --no-check-certificate

bx plugin install icp-linux-amd64

wget http://niklauss-mbp.geneva-marziano.ch.ibm.com:8000/INSTALL/2_CLOUD/ICP/ibm-cloud-auto-mgr-x86_64-2.1.0.tar.gz

bx pr login -a https://mycluster.icp:8443 --skip-ssl-validation
```

```bash
bx pr login -a https://mycluster.icp:8443 --skip-ssl-validation
docker login mycluster.icp:8500
bx pr load-ppa-archive --namespace services --archive icp-cam-x86_64-2.1.0.1_12-17.tar.gz
```

```bash
User name			
niklaushirt				

Access key ID
AKIAI3ECCHD2UXDDDPQQ

Secret access key
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

Console login link
https://582147391765.signin.aws.amazon.com/console




https://github.com/niklaushirt/starterlibrary

d3e2557f9d60fa06efee0c89d94c76f860576f2e

AWS/terraform/hcl/lamp

v1.0.0

```

```bash
sudo mkdir -p /storage/CAM_db
sudo mkdir -p /storage/CAM_logs
sudo mkdir -p /storage/CAM_terraform

sudo chmod -R 777 /storage
sudo chown -R nobody:nogroup /storage
```







```yaml
kind: PersistentVolume
apiVersion: v1
metadata:
  name: cam-mongo-pv
  labels:
    type: cam-mongo
spec:
  capacity:
    storage: 15Gi
  accessModes:
    - ReadWriteMany
  nfs:
    server: 192.168.27.199
    path: /storage/CAM_db
```

```yaml
kind: PersistentVolume
apiVersion: v1
metadata:
  name: cam-logs-pv
  labels:
    type: cam-logs
spec:
  capacity:
    storage: 10Gi
  accessModes:
    - ReadWriteMany
  nfs:
    server: 192.168.27.199
    path: /storage/CAM_logs
```


```yaml
kind: PersistentVolume
apiVersion: v1
metadata:
  name: cam-terraform-pv
  labels:
    type: cam-terraform
spec:
  capacity:
    storage: 15Gi
  accessModes:
    - ReadWriteMany
  nfs:
    server: 192.168.27.199
    path: /storage/CAM_terraform
```