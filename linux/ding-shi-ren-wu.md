秒为单位

```
crontab -e
* * * * *  sleep 5;curl http://baidu.com/  //5秒
* * * * *  sleep 60;curl http://google.com/  //60秒
```



