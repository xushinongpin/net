命令导出数据库

```
nohup mysqldump -u账号 -p密码 --all-databases >/存放路径.sql &
```

window

```
mysqldump -u 账号 -p 数据库 数据表 > E:\XXX\数据表.sql  导出某个表
mysqldump -u 账号 -p 库 > E:\XXX\苦命.sql  导出整个库
```



