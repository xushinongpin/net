### 更新系统

```
sudo -- sh -c 'apt-get update; apt-get upgrade -y; apt-get dist-upgrade -y; apt-get autoremove -y; apt-get autoclean -y'
```

### putty 连接 ubuntu 提示：  network error connection refused

```
sudo apt-get install openssh-server openssh-client
```

### **配置静态ip**

Find your actual network configuration by typing

```
ifconfig

```

You should see something similar to

```
eth0 Link encap Ethernet HWaddr 00:00:00:00:00:00
inet addr:192.168.1.10 Bcast 192.168.1.255 Mask:255.255.255.0

```

Edit the networking config file by typing

```
sudo nano /etc/network/interfaces

```

Inside it find the line

```
auto eth0
iface eth0 inet dhcp

```

and change it to

```
auto eth0
iface eth0 inet static
address 192.168.1.115
netmask 255.255.255.0
gateway 192.168.1.1
dns-nameservers 8.8.8.8 192.168.1.1
```



