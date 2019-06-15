首先导入SublimeHQ GPG键，在终端输入以下命令。

```
sudo rpm -v --import https://download.sublimetext.com/sublimehq-rpm-pub.gpg
```

现在将Sublime Text存储库添加到运行以下命令的系统中的存储库列表中：

```
sudo yum-config-manager --add-repo https://download.sublimetext.com/rpm/stable/x86_64/sublime-text.repo
```

现在您可以按以下命令安装Sublime Text：

```
sudo yum install sublime-text
```

要从终端运行以下命令启动Sublime Text：

```
subl
```



