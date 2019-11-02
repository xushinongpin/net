要先进到该项目目录下，不然会提示 fatal: not a git repository \(or any of the parent directories\): .git

克隆

git.exe clone --progress -v "[https://xxx.com/xxx/xxx.git](https://xxx.com/xxx/xxx.git)" "E:\git\xxx"

添加文件

```
git.exe add .
```

提交文件

```
git.exe commit -m "小测试" -a
```

切换分支

```
    缺少分支时候

    git.exe checkout -b xxxx remotes/origin/xxxx

    已有分支

           git.exe checkout xxxx
```

拉取

```
git.exe pull --progress -v --no-rebase "origin"
```

获取

```
git.exe fetch -v --progress "origin"
```

合并

```
develop 合并的分支

    git.exe merge remotes/origin/master

   release 合并的分支

           git.exe merge remotes/origin/xxxx
```

推送

```
git.exe push --progress "origin" xxxx:xxxx
```

#### 代码回退

默认参数 `-soft`,所有commit的修改都会退回到git缓冲区  
 参数`--hard`，所有commit的修改直接丢弃

```
$ git log   查看日志
$ git reset --hard HEAD^        回退到上个版本
$ git reset --hard commit_id    退到/进到 指定commit_id
```

推送到远程

```
$ git push origin HEAD --force
```

#### 可以吃的后悔药-&gt;版本穿梭

当你回滚之后，又后悔了，想恢复到新的版本怎么办？

用`git reflog`打印你记录你的每一次操作记录

```
$ git reflog

输出：
5f217a06 (HEAD -> master, origin/master) HEAD@{0}: reset: moving to 5f217a0616404770d23c0bb37ca07bd18da8d39c
db9f7532 HEAD@{1}: commit: 谷歌验证码-添加小测试
10c22bd1 HEAD@{2}: commit: 添加 composer require bacon/bacon-qr-code
9a1c0203 HEAD@{3}: commit: 安装谷歌验证码 composer require pragmarx/google2fa
450f741c HEAD@{4}: commit: 删除谷歌验证码-2
bc95d8f2 HEAD@{5}: commit: 卸载谷歌验证码-jwt
8bf9755b HEAD@{6}: commit: 下载谷歌验证码-authenticator
abfd1a45 HEAD@{7}: commit: 上传前端脚手架
5f217a06 (HEAD -> master, origin/master) HEAD@{8}: commit: 上传扩展
c078c641 HEAD@{9}: commit: 小测试
7dbda75d HEAD@{10}: commit: 添加laravel-admin的扩展
524b7906 HEAD@{11}: commit: 添加laravel-admin扩展【https://github.com/z-song/laravel-admin】，删除之前无用路由
4ab98ed8 HEAD@{12}: commit: 添加爬取页面的扩展
1268d909 HEAD@{13}: commit: 添加翻译测试
9cb0ad4f HEAD@{14}: commit: 添加谷歌翻译模板
555187ed HEAD@{15}: commit: 初始化laravel
4b836d3e HEAD@{16}: commit (initial): first commit
```

找到你操作的id如：abfd1a45 ，就可以回退到这个版本

```
$ git reset --hard abfd1a45
```

拉取与获取等待半天都失败的解决方案

![](/assets/20190801043420.png)创建分支提交

```
git push origin new_master:new_master
git push --set-upstream origin new_master
```



