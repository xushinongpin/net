```
vi /etc/sysconfig/network-scripts/ifcfg-enp0s3

    TYPE="Ethernet"
    BOOTPROTO="none"  //静态ip  使用 dhcp
    DEFROUTE="yes"
    PEERDNS="yes"
    PEERROUTES="yes"
    IPV4_FAILURE_FATAL="no"
    IPV6INIT="yes"
    IPV6_AUTOCONF="yes"
    IPV6_DEFROUTE="yes"
    IPV6_PEERDNS="yes"
    IPV6_PEERROUTES="yes"
    IPV6_FAILURE_FATAL="no"
    IPV6_ADDR_GEN_MODE="stable-privacy"
    NAME="enp0s3"
    UUID="e5ca8134-2961-4b14-8590-431679e78740"
    DEVICE="enp0s3"
    ONBOOT="yes"
    IPADDR=192.168.254.200//固定ip
    NETMASK=255.255.255.0//网关
    GATEWAY=192.168.254.254//看自己路由


systemctl restart network
或者
service network restart //这条好像比较有效
```

禁止ipv6

```
执行以下命令，没东西就不用操作了
$ ip a | grep inet6

一： 编辑GRUB配置文件： vi /etc/default/grub
二： GRUB_CMDLINE_LINUX="crashkernel=auto rd.lvm.lv=centos/root rd.lvm.lv=centos/swap rhgb quiet" 【添加了 GRUB_CMDLINE_LINUX="crashkernel=auto rd.lvm.lv=centos/root rd.lvm.lv=centos/swap rhgb quiet"】
    改为
    GRUB_CMDLINE_LINUX="crashkernel=auto rd.lvm.lv=centos/root rd.lvm.lv=centos/swap rhgb quiet"
三： 更新GRUB配置
    grub2-mkconfig -o /boot/grub2/grub.cfg
四： 重启电脑
 reboot
五： 执行 一 命令 看不到输出了
```



