## <a name="ce">Install CE
```bash
sudo docker pull ibmcom/icp-inception:2.1.0.1

sudo docker run -e LICENSE=accept \
  -v "$(pwd)":/data ibmcom/icp-inception:2.1.0.1 cp -r cluster /data
  
sudo docker run -e LICENSE=accept --net=host \
 -t -v "$(pwd)":/installer/cluster \
 ibmcom/icp-inception:2.1.0.1 install | sudo tee install.log  
```
