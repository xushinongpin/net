# 能连接不能上网-待排查

# 如何在Centos 7上安装Softether VPN服务器

Setting up your own virtual private network server is a good way to evade blockage and be able to access sites that are blocked in your country. Choice of open source VPN packages is long but today we decided to try Softether coming from University of Tsukuba in Japan. Softether have long been proprietary product under name PacketX and it has been open sourced just several years ago. That may be the reason why it is so Windows oriented, the configuration GUI is windows only and connecting from Linux clients requires extra work. We are going to use only Linux and no GUIs here, so lets start. In the beginning, lets update the system, install dependencies and disable SElinux

设置您自己的虚拟专用网络服务器是避免阻塞并能够访问您所在国家/地区阻止的网站的好方法。

开源VPN包的选择很长，但今天我们决定尝试来自日本筑波大学的Softether。

Softether长期以来一直是名为PacketX的专有产品，几年前就开源了。

这可能是它面向Windows的原因，配置GUI仅限Windows，而Linux客户端的连接需要额外的工作。

我们这里只使用Linux而没有GUI，所以让我们开始吧。

首先，让我们更新系统，安装依赖项并禁用SElinux

> yum update  
> yum -y groupinstall "Development Tools"  
> yum -y install gcc zlib-devel openssl-devel readline-devel ncurses-devel wget tar dnsmasq net-tools iptables-services system-config-firewall-tui nano iptables-services
>
> sed -i 's/SELINUX=enforcing/SELINUX=disabled/g' /etc/selinux/config

After this reboot the computer so selinux stop and new kernel start if update had any new kernel. After the server boots up, disable both firewalls because they can interfere with testing. The firewall rules will be set after all is configured

重新启动计算机之后，如果更新有任何新内核，则selinux停止并启动新内核。

服务器启动后，禁用两个防火墙，因为它们可能会干扰测试。

配置完所有防火墙规则后，将设置防火墙规则

> systemctl disable firewalld  
> systemctl stop firewalld  
> systemctl status firewalld
>
> service iptables save  
> service iptables stop  
> chkconfig iptables off

Of those two batches of commands, one will error because you are not running two firewalls. Next we need to cd to /usr/src, download the Softether, unpack it and compile it. We will use 4.20 version of Softether which is in the time of writing newest rtm version. There is also 4.21 but that is beta.

在这两批命令中，一个会出错，因为您没有运行两个防火墙。

接下来我们需要cd到/ usr / src，下载Softether，解压缩并编译它。

我们将使用4.20版本的Softether，这是在编写最新的rtm版本时。

还有4.21，但那是测试版。

> wget www.softether-download.com/files/softether/v4.20-9608-rtm-2016.04.17-tree/Linux/SoftEther\_VPN\_Server/64bit\_-\_Intel\_x64\_or\_AMD64/softether-vpnserver-v4.20-9608-rtm-2016.04.17-linux-x64-64bit.tar.gz

tar xzvf softether-vpnserver-v4.20-9608-rtm-2016.04.17-linux-x64-64bit.tar.gz -C /usr/local

> cd /usr/local/vpnserver  
> make

Compile will ask you three questions at the end, you need to answer all with 1.

Next wee need to make init script for softether, as one is not included into the install. So run vi /etc/init.d/vpnserver and make paste this script.

编译最后会问你三个问题，你需要用1来回答所有问题。

接下来我们需要为softether创建init脚本，因为安装中不包含一个脚本。所以运行vi /etc/init.d/vpnserver并粘贴这个脚本。

> \#!/bin/sh  
> \#\#\# BEGIN INIT INFO  
> \# Provides: vpnserver  
> \# Required-Start: $remote\_fs $syslog  
> \# Required-Stop: $remote\_fs $syslog  
> \# Default-Start: 2 3 4 5  
> \# Default-Stop: 0 1 6  
> \# Short-Description: Start daemon at boot time  
> \# Description: Enable Softether by daemon.  
> \#\#\# END INIT INFO  
> DAEMON=/usr/local/vpnserver/vpnserver  
> LOCK=/var/lock/subsys/vpnserver  
> TAP\_ADDR=192.168.7.1
>
> test -x $DAEMON \|\| exit 0  
> case "$1" in  
> start\)  
> $DAEMON start  
> touch $LOCK  
> sleep 1  
> /sbin/ifconfig tap\_soft $TAP\_ADDR  
> ;;  
> stop\)  
> $DAEMON stop  
> rm $LOCK  
> ;;  
> restart\)  
> $DAEMON stop  
> sleep 3  
> $DAEMON start  
> sleep 1  
> /sbin/ifconfig tap\_soft $TAP\_ADDR  
> ;;  
> \*\)  
> echo "Usage: $0 {start\|stop\|restart}"  
> exit 1  
> esac  
> exit 0

Next need to add the executable bit to the init script and start it for the first time in the old fashion way and then enable it it with systemd to start at every boot.

接下来需要将可执行位添加到init脚本并以旧方式首次启动它，然后使用systemd启用它以在每次启动时启动。

> chmod +x /etc/init.d/vpnserver
>
> /etc/init.d/vpnserver start
>
> systemctl enable vpnserver

Don't mind that it complaints about tap interface, that is because we added it to init script and made it start with softether but didn't yet made the tap interface in softether config. We will come to that latter.

不介意它抱怨tap接口，这是因为我们将它添加到init脚本并使其从softether开始，但还没有在softether配置中创建tap接口。

我们将来到后者。

## Softether is installed, now we configure 已安装Softether，现在我们配置

Moving over to configuration part, we need to start vpncmd utility

转到配置部分，我们需要启动vpncmd实用程序

> /usr/local/vpnserver/vpncmd

Press 1 to select "Management of VPN Server or VPN Bridge", and then whe it asks you which server to configure, just press enter and it wll chose localhost where you just installed Softether. Press Enter one more time to get access to server as Administrator. Next type

按1选择“管理VPN服务器或VPN桥”，然后它会询问您配置哪个服务器，只需按Enter键，它将选择您刚安装Softether的localhost。

再次按Enter键以管理员身份访问服务器。

下一个类型

> ServerPasswordSet

to set admin password for the server. In order to use softether, virtual hub needs to be created. We will create one named MOB with following command

设置服务器的管理员密码。

为了使用softether，需要创建虚拟集线器。

我们将使用以下命令创建一个名为MOB的命令

> HubCreate MOB

It will ask you to set password, which you will use to administer a hub, without access to entire VPN server.

Now we need to create local bridge. That is more efficient of the ways, there is also SecureNAT which is easier to setup but it is resource intensive. We will go with local bridge and tap device, note that with local bridge also DHCP server needs to be configured and installed which will do at the end of tutorial. So local bridge is created with following command:

它将要求您设置密码，您将使用该密码来管理集线器，而无需访问整个VPN服务器。

现在我们需要创建本地桥。这种方式更有效，还有SecureNAT，它更容易设置但是资源密集。我们将使用本地网桥和点击设备，请注意，使用本地网桥也需要配置和安装DHCP服务器，这将在教程结束时完成。因此，使用以下命令创建本地桥：

> BridgeCreate /DEVICE:"soft" /TAP:yes MOB

If TAP device creation fails with message about insufficient privileges, you might want to check if your network controller is set in promiscuous mode. HyperV and VMware by default create VMs without promiscuous mode. Set promiscuous mode and then retry creation of the tap device.

Now we need to create user for the MOB virtual hub we created. Users are created with command UserCreate and you can view the list of users by command UserList. Users can be added to groups and each group can have different authentication mode, for example Password, Certificate, RADIUS, NTLM and others.

如果TAP设备创建失败并显示权限不足的消息，您可能需要检查网络控制器是否设置为混杂模式。默认情况下，HyperV和VMware会创建没有混杂模式的VM。设置混杂模式，然后重试创建点击设备。

现在我们需要为我们创建的MOB虚拟中心创建用户。用UserCreate命令创建用户，您可以通过命令UserList查看用户列表。用户可以添加到组中，每个组可以具有不同的身份验证模式，例如密码，证书，RADIUS，NTLM等。

## Configuring the virtual Hub 配置虚拟HUB

Now we switch to hub MOB 现在我们切换到集线器MOB

> Hub MOB

and create user 并创建用户

> UserCreate test

We will keep it simple and use password auth, so use the following command

我们将保持简单并使用密码身份验证，因此请使用以下命令

> UserPasswordSet test

Now we setup L2TP/IPSec, work the prompt as follows, bold is what you need to type:

现在我们设置L2TP / IPSec，按如下方式处理提示，粗体是您需要输入的内容：

> VPN Server/MOB&gt;**IPsecEnable**  
> IPsecEnable command - Enable or Disable IPsec VPN Server Function  
> Enable L2TP over IPsec Server Function \(yes / no\):**yes**
>
> Enable Raw L2TP Server Function \(yes / no\):**yes**
>
> Enable EtherIP / L2TPv3 over IPsec Server Function \(yes / no\):**yes**
>
> Pre Shared Key for IPsec \(Recommended: 9 letters at maximum\):**linoxide**
>
> Default Virtual HUB in a case of omitting the HUB on the Username: **MOB**
>
> The command completed successfully.

That is it for IPsec, but we also want to have other protocols. For example OpenVPN and Microsoft protocols. We use**ServerCertRegenerate**command to generate and register a SSL certificate for the server in order to be able to use it for OpenVPN and Microsoft clients. Argument passed to the command must be your server IP adress or FQDIN:

这是IPsec，但我们也希望有其他协议。

例如OpenVPN和Microsoft协议。

我们使用

**ServerCertRegenerate**

命令为服务器生成并注册SSL证书，以便能够将其用于OpenVPN和Microsoft客户端。

传递给命令的参数必须是您的服务器IP地址或FQDIN：

> **ServerCertRegenerate**&lt;YOUR SERVER IP or FQDN&gt;

A new server certificate has been created, we needs to save it to file:

已创建新的服务器证书，我们需要将其保存到文件：

> ServerCertGet ~/cert.cer

This certificate now can be transfered to your clients. We can now enable SSTP function with this command:

此证书现在可以转移给您的客户。

我们现在可以使用以下命令启用SSTP功能：

> SstpEnable yes

And to enable OpenVPN:

并启用OpenVPN：

> OpenVpnEnable yes /PORTS:1194

Port for OpenVPN can be changed to your liking. Then we need to create config for OpenVPN client like this

OpenVPN的端口可以根据自己的喜好进行更改。

然后我们需要像这样为OpenVPN客户端创建配置

> OpenVpnMakeConfig ~/openvpn\_config.zip

## VPN over DNS and VPN over ICMP

## 基于ICMP的DNS和VPN上的VPN

Type Hub to return to administering entire vpn server and not just MOB hub.

键入Hub以返回管理整个vpn服务器而不仅仅是MOB中心。

> VPN Server/MOB&gt;Hub  
> Hub command - Select Virtual Hub to Manage  
> The Virtual Hub selection has been unselected.  
> The command completed successfully.

For maximal evasion of all blockages, we also need to enable VPN over ICMP and DNS:

为了最大限度地避免所有阻塞，我们还需要在ICMP和DNS上启用VPN：

> **VpnOverIcmpDnsEnable /ICMP:yes /DNS:yes**  
> VpnOverIcmpDnsEnable command - Enable / Disable the VPN over ICMP / VPN over DNS Server Function  
> The command completed successfully.

Now exit the vpncmd because we need to stop the vpnserver and setup dnsmasq

现在退出vpncmd，因为我们需要停止vpnserver并设置dnsmasq

> service vpnserver stop

## DHCP server, forwarding and postrouting

## DHCP服务器，转发和postrouting

Softether is now configured, but since we are not using SecureNAT and going with local bridge instead, will need a DHCP server. The dnsmasq is already installed in first stage of tutorial when we installed dependancies, so now we need to configure it. We need to edit /etc/dnsmasq.conf or use echo command to append needed lines to it. We will use latter opton and while we are at it, we will also echo the ipv4\_forwarding.conf

Softether现在已配置，但由于我们不使用SecureNAT而是使用本地网桥，因此需要DHCP服务器。

当我们安装依赖项时，dnsmasq已经安装在教程的第一阶段，所以现在我们需要对其进行配置。

我们需要编辑/etc/dnsmasq.conf或使用echo命令向其追加所需的行。

我们将使用后一个opton，当我们在它时，我们也将回应ipv4\_forwarding.conf

> echo interface=tap\_soft &gt;&gt; /etc/dnsmasq.conf  
> echo dhcp-range=tap\_soft,192.168.7.50,192.168.7.90,12h &gt;&gt; /etc/dnsmasq.conf  
> echo dhcp-option=tap\_soft,3,192.168.7.1 &gt;&gt; /etc/dnsmasq.conf  
> echo port=0 &gt;&gt; /etc/dnsmasq.conf  
> echo dhcp-option=option:dns-server,8.8.8.8 &gt;&gt; /etc/dnsmasq.conf
>
> echo net.ipv4.ip\_forward = 1 &gt;&gt; /etc/sysctl.d/ipv4\_forwarding.conf

Apply this setting by runing 通过运行应用此设置

> sysctl -n -e --system

Check if it is applied: 检查是否已应用：

> cat /proc/sys/net/ipv4/ip\_forward

It should show 1. If it shows 0, do this 它应显示1.如果显示0，请执行此操作

> echo 1 &gt; /proc/sys/net/ipv4/ip\_forward

Enable nat and postrouting: 启用nat和postrouting：

> iptables -t nat -A POSTROUTING -s 192.168.7.0/24 -j SNAT --to-source \[YOUR SERVER IP ADDRESS\]
>
> iptables-save &gt; /etc/sysconfig/iptables

Restart vpn and dhcp servers with folowing commands and enable them to start at every boot:

使用以下命令重新启动vpn和dhcp服务器，并使它们在每次启动时启动：

> service vpnserver start
>
> systemctl start dnsmasq
>
> systemctl enable dnsmasq
>
> chkconfig vpnserver on

## Conclusion 结论

That concludes the install and configuration of Softether VPN server. It is configured with Local Bridge for maximum performance, we only now need to connect clients. The Windows and android ones are easy, for Windows you just head to the Softether site and download GUI client and connect. For android, you dont need even that, you have VPN client built in. But for Linux, to be able to connect, you need Virtual Layer-3 switch on Server, and you need to run dhclient on the virtual interface on client GNU/Linux machine. In future article we will concentrate on this Desktop GNU/Linux client which guys from Tsukuba University for some reason don't like and require all this additional steps.

以上是Softether VPN服务器的安装和配置。

它配置了Local Bridge以获得最佳性能，我们现在只需要连接客户端。

Windows和Android很容易，对于Windows，您只需前往Softether站点并下载GUI客户端并连接即可。

对于Android，你甚至不需要，你已经内置了VPN客户端。但是对于Linux，要能够连接，你需要在服务器上进行虚拟第3层交换，你需要在客户端GNU上的虚拟接口上运行dhclient / Linux机器。

在以后的文章中，我们将专注于这个桌面GNU / Linux客户端，来自筑波大学的人出于某种原因不喜欢并需要所有这些额外的步骤。

