## <a name="nfs">Create NFS VOLUMES
```yaml
apiVersion: v1
kind: PersistentVolume
metadata:
  name: nfsvol01rwo
spec:
  capacity:
    storage: 30Gi
  accessModes:
    - ReadWriteOnce
  persistentVolumeReclaimPolicy: Recycle
  nfs:
    path: /storage/nfsvol01rwo
    server: 192.168.27.199

apiVersion: v1
kind: PersistentVolume
metadata:
  name: nfsvol02rwm
spec:
  capacity:
    storage: 30Gi
  accessModes:
    - ReadWriteMany
  persistentVolumeReclaimPolicy: Recycle
  nfs:
    path: /storage/nfsvol02rwm
    server: 192.168.27.199
```

```bash
sudo apt-get install nfs-kernel-server

sudo mkdir -p /storage/
sudo mkdir -p /storage/nfsvol01rwo
sudo mkdir -p /storage/nfsvol02rwm

sudo chmod -R 777 /storage
sudo chown -R nobody:nogroup /storage

sudo nano /etc/exports

/storage           *(rw,sync,no_subtree_check,async,insecure,no_root_squash)

sudo systemctl restart nfs-kernel-server


```