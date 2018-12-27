### 更新系统

```
sudo -- sh -c 'apt-get update; apt-get upgrade -y; apt-get dist-upgrade -y; apt-get autoremove -y; apt-get autoclean -y'
```

### putty 连接 ubuntu 提示：  network error connection refused

```
sudo apt-get install openssh-server openssh-client
```

### 重启网路

```
sudo /etc/init.d/networking restart
```

### **配置静态ip \[ 配置后不能上网，具体原因：未知 \]**

```
1- From the top of the screen select the network icon, next to the clock and volume, then click/从屏幕顶部选择时钟和音量旁边的网络图标，然后单击 Edit Connections.

2- From the window that opens, go to Wired tab, select your connection (there should be only one connection, if you didn't touch anything). Then click/从打开的窗口中，转到“有线”选项卡，选择您的连接（如果您没有触摸任何内容，则应该只有一个连接）。然后点击 Edit.

3- From the IPv4 Settings tab change Method from Automatic (DHCP) to Manual./从IPv4设置选项卡中，将方法从自动（DHCP）更改为手动

4- Under Addresses feild, click on/在地址栏下，单击 Add.

5- Enter your desired IP address and subnet mask and click/输入所需的IP地址和子网掩码，然后单击 Save, you can also enter an optional DNS server here/您也可以在此处输入可选的DNS服务器.
```



