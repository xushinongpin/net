提取到/tmp

```
tar xvzf ~/Downloads/PhpStorm*.tar.gz -C /tmp/
```

设置权限

```
sudo chown -R root:root /tmp/PhpStorm*
```

搬迁位置

```
sudo mv /tmp/PhpStorm* /opt/PhpStorm
```

添加快捷键

```
sudo ln -s /opt/PhpStorm/bin/phpstorm.sh /usr/local/bin/phpstorm
```

命令行启动

```
phpstorm
```



