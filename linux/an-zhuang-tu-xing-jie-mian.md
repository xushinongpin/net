列出CentOS 7的可用软件包组

```
#yum group list
输出
Loaded plugins: fastestmirror
There is no installed groups file.
Maybe run: yum groups mark convert (see man yum)
Loading mirror speeds from cached hostfile
Available Environment Groups:
 Minimal Install
 Compute Node
 Infrastructure Server
 File and Print Server
 Basic Web Server
 Virtualization Host
 Server with GUI
 GNOME Desktop
 KDE Plasma Workspaces
 Development and Creative Workstation
Available Groups:
 Compatibility Libraries
 Console Internet Tools
 Development Tools
 Graphical Administration Tools
 Legacy UNIX Compatibility
 Scientific Support
 Security Tools
 Smart Card Support
 System Administration Tools
 System Management
Done
```

安装图形界面

```
# yum groupinstall "GNOME Desktop" "Graphical Administration Tools"
# yum groupinstall "Server with GUI"
# ln -sf /lib/systemd/system/runlevel5.target /etc/systemd/system/default.target
# reboot
# startx 启动图形界面
```



