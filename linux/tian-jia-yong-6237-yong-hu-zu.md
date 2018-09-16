```
查看用了哪些用户组id
tail /etc/passwd
分配未使用用户id，比如 1010，组名叫elasticsearch
groupadd -g 1010 elasticsearch
添加用户到用户组
useradd -u 1010 -g 1010 -d /home/elasticsearch elasticsearch
设置密码
passwd elasticsearch
分配用户组权限
chown -R elasticsearch:elasticsearch ./elasticsearch-6.4.0
```



