```
centos

mkdir -p /www
fdisk /dev/sdb
mke2fs -t ext4 /dev/sdb1
mount /dev/sdb1 /www
echo "/dev/sdb1 /www ext4 defaults 0 0" >> /etc/fstab
df -h
```



