添加秒为单位的定时任务

```
#crontab -e

添加
* * * * *  sleep 5;curl http://baidu.com/ //5秒
* * * * *  sleep 60;curl http://google.com/ //60秒

```

[更多参考 ](https://tecadmin.net/crontab-in-linux-with-20-examples-of-cron-schedule/)

