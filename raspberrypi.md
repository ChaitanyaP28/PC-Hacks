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
mount |grep "mergerfs"
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
