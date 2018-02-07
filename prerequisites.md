#Snippets

### Update / Upgrade
```bash
sudo apt-get update
sudo apt-get upgrade

sudo ufw disable
```

### INSTALL SOME STUFF
```bash
sudo apt install python

sudo apt-get install tree
sudo apt-get install htop
sudo apt install curl
sudo apt-get install unzip
sudo apt-get install iftop
docker run -d -p 9000:9000 --name "DOCKER_UI" --privileged -v /var/run/docker.sock:/var/run/docker.sock --restart always uifd/ui-for-docker

docker run -d -p 9010:9000 -v /var/run/docker.sock:/var/run/docker.sock --name PORTAINER --restart always portainer/portainer



```

```bash
docker run -d -p 9000:9000 --name "DOCKER_UI" --privileged -v /var/run/docker.sock:/var/run/docker.sock --restart always uifd/ui-for-docker

docker run -d -p 9010:9000 -v /var/run/docker.sock:/var/run/docker.sock --name PORTAINER --restart always portainer/portainer

```

### CREATE USER
```bash
sudo adduser demo

sudo nano /etc/sudoers 

demo    ALL=(ALL:ALL) ALL

sudo usermod -aG docker demo

```

### KEYBOARD
```bash
sudo dpkg-reconfigure keyboard-configuration
```

### NETWORK CONFIG
```bash
ifconfig
sudo nano /etc/network/interfaces
```

--> Modify with this:

```bash
# interfaces(5) file used by ifup(8) and ifdown(8)
# auto lo
# iface lo inet loopback
auto ens33
iface ens33 inet static
address 192.168.27.127
netmask 255.255.255.0
gateway 192.168.27.2
dns-nameservers 192.168.27.2
```

### Modify Host Name
```bash
sudo nano /etc/hosts

sudo hostname mycluster.icp
sudo hostname
sudo nano /etc/hostname
sudo hostname mycluster.icp
```



### Modify some performance stuff
```bash
sudo sysctl -w vm.max_map_count=262144
sudo nano /etc/sysctl.conf
```

Add the line

```bash
vm.max_map_count=262144
```

### Create SSH Key
```bash
ssh-keygen -b 4096 -t rsa -f ~/.ssh/master.id_rsa -N ""
cat ~/.ssh/master.id_rsa.pub | sudo tee -a ~/.ssh/authorized_keys
ssh-copy-id -i ~/.ssh/master.id_rsa.pub root@192.168.27.127
```

```bash
ssh root@192.168.27.127
cat ~/.ssh/master.id_rsa.pub | sudo tee -a ~/.ssh/authorized_keys
sudo systemctl restart sshd
```

```bash
sudo cp ~/.ssh/master.id_rsa ~/cluster/ssh_key
sudo chmod 400 ~/cluster/ssh_key

```

## Increase disk Space
```bash
sudo fdisk /dev/sda
d delete
n to create
a toggle bootable
w write

sudo reboot

sudo resize2fs /dev/sda1
```