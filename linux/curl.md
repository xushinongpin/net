```
curl -v -s -o /dev/null https://a.com   查此域名跳转链接
高级：
time curl -L -s -v -o /dev/null http://sck.app  查看跳转所有层以及跳转所用时间
```

如果服务器curl出错，提示 curl: \(6\) Couldn't resolve host 'isc.app'

```
修改 /etc/resolv.conf
nameserver 127.0.0.1
nameserver 8.8.8.8
nameserver 8.8.4.4

```



