#### 一、应用程序池

```
%windir%\system32\inetsrv\appcmd list apppool /config /xml > d:\apppools.xml  //批量导出
%windir%\system32\inetsrv\appcmd add apppool /in < d:\apppools.xml  //批量导入
%windir%\system32\inetsrv\appcmd list apppool "应用程序池名称" /config /xml > d:\myapppool.xml //单个导出
%windir%\system32\inetsrv\appcmd add apppool /in < d:\myapppool.xml //单个导入
```

#### 二、站点

```
%windir%\system32\inetsrv\appcmd list site /config /xml > d:\sites.xml //批量导出
%windir%\system32\inetsrv\appcmd add site /in < d:\sites.xml //批量导入
%windir%\system32\inetsrv\appcmd list site “站点名称” /config /xml > d:\mywebsite.xml //单个导出
%windir%\system32\inetsrv\appcmd add site /in < d:\mywebsite.xml //单个导入
```

最简单的方法

```
复制系统IIS配置文件  C:\Windows\System32\inetsrv\config
需要修改 ip 信息的  直接修改 applicationHost.config
```



