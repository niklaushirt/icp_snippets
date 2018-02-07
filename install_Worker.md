## Install New Worker
```bash
ssh-copy-id -i ~/.ssh/master.id_rsa root@192.168.27.198

sudo systemctl restart sshd

docker run -e LICENSE=accept --net=host -v "$(pwd)":/installer/cluster ibmcom/icp-inception:2.1.0.1 install -l 192.168.27.198 

```