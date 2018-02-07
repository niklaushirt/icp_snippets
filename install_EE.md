## <a name="ee">Install EE
```bash
ssh-keygen -b 4096 -t rsa -f ~/.ssh/master.id_rsa -N ""
cat ~/.ssh/master.id_rsa.pub | sudo tee -a ~/.ssh/authorized_keys
ssh-copy-id -i ~/.ssh/master.id_rsa.pub root@192.168.27.199

sudo mkdir /opt/ibm-cp-app-mod-2.1.0.1
cd /opt/ibm-cp-app-mod-2.1.0.1

tar xf ibm-cp-app-mod-ppc64le-2.1.0.1.tar.gz -O | sudo docker load

sudo docker run -v $(pwd):/data -e LICENSE=accept ibmcom/icp-inception:2.1.0.1-ee cp -r cluster /data

sudo cp ~/.ssh/master.id_rsa ./cluster/ssh_key
sudo chmod 400 ./cluster//ssh_key

sudo mkdir -p ./cluster/images
sudo mv /home/demo/ibm-cp-app-mod-x86_64-2.1.0.1.tar.gz  ./cluster/images/

cd ./cluster

sudo docker run --net=host -t -e LICENSE=accept -v $(pwd):/installer/cluster ibmcom/icp-inception:2.1.0.1-ee install



```
