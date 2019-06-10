挂载方法

```
mount -h
用法:  mount [-o options] [-u:username] [-p:<password | *>] <\\computername\sharename> <devicename | *>

-o rsize=size               设置读取缓冲区的大小(以 KB 为单位)。
-o wsize=size               设置写入缓冲区的大小(以 KB 为单位)。
-o timeout=time             设置 RPC 调用的超时值(以秒为单位)。
-o retry=number             设置软装载的重试次数。
-o mtype=soft|hard          设置装载类型。
-o lang=euc-jp|euc-tw|euc-kr|shift-jis|big5|ksc5601|gb2312-80|ansi
                            指定用于文件和目录名称的编码。
-o fileaccess=mode          指定文件的权限模式。
                            这些模式用于在 NFS 服务器上创建的
                            新文件。使用 UNIX 样式模式位指定。
-o anon                     作为匿名用户装载。
-o nolock                   禁用锁定。
-o casesensitive=yes|no     指定在服务器上执行区分大小写的文件查找。
-o sec=sys|krb5|krb5i|krb5p

eg: mount -o timeout=5 retry=2 \\192.168.0.10\www\wwwroot x:
```

删除挂载盘

```
net use x: /delete
```

温馨提示： 共享文件不能添加修改请核对是否给了权限，测试用的可以给777

