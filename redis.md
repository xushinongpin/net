redis - linux 官网【包含下载安装教程】

```
https://redis.io/download
```

连接redis

```
$ redis-cli -h host -p port -a password
```

redis - window自动启动【 [https://www.zhihu.com/question/22771030](https://www.zhihu.com/question/22771030) 】

```
进入到redis目录 
①
redis-server.exe --service-install redis.windows.conf --loglevel verbose
②
redis-server --service-start

扩展地址：https://pecl.php.net/package/redis【看好是单线程还是多线程】
```

# **redis笔记**

默认端口  6379 【mogodb 27017 28017】

Windows

redis安装： [http://www.runoob.com/redis/redis-install.html](http://www.runoob.com/redis/redis-install.html)

cmd

进入目录：D:\wamp64\www\redis

运行：redis-server.exe redis.windows.conf

新cmd

redis-cli.exe -h 127.0.0.1 -p 6379

linux

安装包地址        wget [http://download.redis.io/releases/redis-4.0.1.tar.gz](http://download.redis.io/releases/redis-4.0.1.tar.gz)

解压              tar zxvf redis-xxx.tar.gz

进入目录          cd redis-xxx

编译              make

安装              cd src && make install

为了便于管理，把相关安装好的移到源代码安装目录下

创建【-p 递归创建】

```
mkdir -p /usr/local/redis/bin

mkdir -p /usr/local/redis/etc
```

移动

```
mv /lamp/redis-xxx/redis.conf /usr/local/redis/etc

cd /lamp/redis-xxx/src

mv mkreleasehdr.sh redis-benchmark redis-check-aof redis-check-dump redis-cli redis-server /usr/local/redis/bin
```

启动redis服务

```
/usr/local/redis/bin/redis-server /usr/local/redis/etc/redis.conf

后台运行需要修改 daemonize no  为 daemonize yes
```

停止

```
/usr/local/redis/bin/redis-cli【pkill redis-server】
```

客户端连接

```
/usr/local/redis/bin/redis-cli
```

查看是否运行

```
ps -ef \| grep redis
```

查看是否占用端口

```
netstat -tunpl \| grep 6379
```

查看被关闭的端口

```
!net
```

命令

string操作

赋值                      set key value【赋值前判断是否存在，存在返回0表示没修改，不存在返回1表示更改成功（nx表示 not exist）  setnx key value】

有效期赋值                setex key second value【多少秒内有效】

替换某段字符              setrange key offect value【offect 是从0开始算第几个开始替换原字符某段，原字符长度大于新字符长度，剩下的原字符直接拼接到新字符后面】

获取某段字符串            getrange key start end

批量设置                  mset key1 value1 key2 value2

批量获取                  mget key1 key2 key3 ....

不覆盖批量设置            msetnx key1 value1 key2 value2 key3 value3

获取旧值并设置新值        getset key value

读取                      get key

自增                      incr key

自增指定值                incrby key increment【increment 可以正数可以负数】

自减                      decr key【incr的相反操作】

自增指定值                decrby key increment【incrby的相反操作】

追加字符串                append key value

获取字符串长度            strlen

hash操作【可以当做表】

设置值                    hset key field value【eg:hset user:01 name shabi】

不存在设置                hsetnx key field value【存在返回1不存在返回0】

批量设置                  hmset key field value field1 value1

获取值                    hget key field【eg:hget user:01 name】

批量获取                  hmget key field field1

增加指定值                hincrby key field increment

判断是否存在某个键        hexists key field

返回键数                  hlen key

删除指定键                hdel key field field1 field2

返回所有字段              hkeys key

返回所有值                hvals key

获取所有的键值            hgetall key

lists【链表结构】

从头部压入元素            lpush key value value1

从尾部压入一个元素        rpush key value value1

从头开始取出一个元素      lrange key start stop

从某个位置前/后开始压入   linsert key BEFORE\|AFTER pivot value

替换某个值                lset key index value【eg:lset key 1 value】

删除几个不相同的元素      lrem key count value

删除某段值之外的元素      ltrim key start stop

从头弹出一个元素          lpop key

从尾弹出一个元素          rpop key

从key1尾部弹出压入key2    rpoplpush source destination【eg：rpoplpush list1 list2】

返回链表多少个元素        llen key

sets【集合】

添加元素                  sadd key member \[member ...\]

读取元素                  smembers key

删除元素                  srem key member \[member ...\]

随机删除                  spop key \[count\]

返回第一個key的差集       sdiff key key1

返回給定key跟第一個key的差集 sdiffstore destination key key1【eg：sdiffstore key2 key key1】

返回key跟key1的交集       sinter key key1

返回給定key跟第一個key的交集 sinterstore destination key key1【eg：sinterstore key2 key key1】

返回key与key1的并集       sunion key key1

返回所有给定key的并集     sunionstore destination key key1

将key1里面的a元素移到key2 smove source destination member【eg：smove key1 key2 a】

返回元素个数              scard key1

检查是否存在某个值        sismember key member

随机返回几个【默认一个】  srandmember key \[count\]



删除所有数据

```
> flushdb
或者
> flushall
```



