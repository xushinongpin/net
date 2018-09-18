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



