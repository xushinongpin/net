#### 一、应用程序池



```
%windir%\system32\inetsrv\appcmd list apppool /config /xml > d:\apppools.xml  //批量导出
%windir%\system32\inetsrv\appcmd add apppool /in < c:\apppools.xml  //批量导入
%windir%\system32\inetsrv\appcmd list apppool "应用程序池名称" /config /xml > c:\myapppool.xml //单个导出
%windir%\system32\inetsrv\appcmd add apppool /in < c:\myapppool.xml //单个导入
```

#### 二、站点

```
%windir%\system32\inetsrv\appcmd list site /config /xml > c:\sites.xml //批量导出
%windir%\system32\inetsrv\appcmd add site /in < c:\sites.xml //批量导入
%windir%\system32\inetsrv\appcmd list site “站点名称” /config /xml > c:\mywebsite.xml //单个导出
%windir%\system32\inetsrv\appcmd add site /in < c:\mywebsite.xml //单个导入
```



