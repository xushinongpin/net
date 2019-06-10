centos7

添加8888端口的访问权限，这里添加后永久生效

\#firewall-cmd --zone=public --add-port=8888/tcp --permanent

\#firewall-cmd --reload

查看8888端口访问权限情况

\#firewall-cmd --zone= public --query-port=8888/tcp

关闭8888访问权限

\#firewall-cmd --zone= public --remove-port=8888/tcp --permanent

关闭防火墙

```
 systemctl stop firewalld.service
```

禁止启动

```
systemctl disable firewalld.service
```

查看防火墙状态

```
firewall-cmd --state
```



