# Raspberry Pi

## JBOD

### Creating JBOD
```bash
sudo apt install -y mergerfs 
```

```bash
sudo mkdir -p /mnt/disk1 /mnt/disk2 /mnt/disk3
```

```bash
sudo chown chait:chait /mnt/disk1 /mnt/disk2 /mnt/disk3
```

```bash
sudo mkdir -p /mnt/jbod
```

```bash
sudo chown chait:chait /mnt/jbod
```

```bash
sudo mergerfs /mnt/disk1:/mnt/disk2:/mnt/disk3 /mnt/jbod \
-o allow_other,use_ino,category.create=mfs
```



### Check Status
```bash
mount | grep "mergerfs"
```

### Service
```bash
sudo nano /etc/systemd/system/jbod-mergerfs.service
```

### Start Service
```bash
sudo systemctl daemon-reload
sudo systemctl start jbod-mergerfs.service
```

## Cluster

### Creation

**Master**

Install k3s server:

``` bash
curl -sfL https://get.k3s.io | sh -
```

Verify:

``` bash
sudo k3s kubectl get nodes
```

Join Token:

``` bash
sudo cat /var/lib/rancher/k3s/server/node-token
```

**Worker**

``` bash
curl -sfL https://get.k3s.io | \
K3S_URL=https:// "<MASTER IP>" :6443 \
K3S_TOKEN="<TOKEN>" \
sh -
```

*Replace `<TOKEN>` with the token from the master.


Verify from the master:

``` bash
sudo k3s kubectl get nodes -o wide
```

**WSL Worker**

``` bash
curl -sfL https://get.k3s.io | \
K3S_URL=https:// "<MASTER IP>" :6443 \
K3S_TOKEN="<TOKEN>" \
INSTALL_K3S_EXEC="agent --node-name= "<system name>" --node-ip= "<System Ip>" " \
sh -
```

### Useful commands

View nodes:

``` bash
sudo k3s kubectl get nodes
```

``` bash
sudo k3s kubectl get nodes -o wide
```


View pods:

``` bash
sudo k3s kubectl get pods
```

Watch pods: 

``` bash
sudo k3s kubectl get pods -w
```


### Test the Cluster

**On Master**
Create NGINX:

``` bash
sudo k3s kubectl create deployment nginx --image=nginx
```

Scale 4 Times:

``` bash
sudo k3s kubectl scale deployment nginx --replicas=4
```

Expose:

``` bash
sudo k3s kubectl expose deployment nginx --type=NodePort --port=80
```

Check:

``` bash
sudo k3s kubectl get pods -o wide
sudo k3s kubectl get svc
```

Delete Test Application

``` bash
sudo k3s kubectl delete deployment nginx
sudo k3s kubectl delete service nginx
```


### Un-Register

**Master**

``` bash
sudo /usr/local/bin/k3s-uninstall.sh
```

**Workers**

``` bash
sudo /usr/local/bin/k3s-agent-uninstall.sh
```

## NAS
### Setup
Installing Samba Server
```bash
sudo apt install samba
```

Open Samba Config File
```bash
sudo nano /etc/samba/smb.conf
```

```text
[PI-NAS]
path = <Path to your shared folder>
writeable = yes
browseable = yes
public=no
```

- PI-NAS : Name of the NAS folder
- path : Path to your shared folder
- writeable : Write access
- browseable : Visiable on explorer
- public : If Guest Users (Without Signin) Can access

```bash
sudo systemctl restart smbd
```

### Samba User
```bash
sudo smbpasswd -a <Username>
```


### Accessing

**On Windows:**

(File Manager)
```bash
\\raspberrypi.local
```

**On Linux:**

(Nautilus File Manager >  Other Locations > Enter server address)
```bash
smb://raspberrypi.local
```
