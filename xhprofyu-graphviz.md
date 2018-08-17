xhprof是php性能检测工具

graphviz是图形界面查看工具

```
下载并安装流程
wget -c http://graphviz.gitlab.io/pub/graphviz/stable/SOURCES/graphviz.tar.gz \ -O graphviz-2.40.1.tar.gz
tar zxvf graphviz.tar.gz
cd graphviz-2.40.1/
./configure
make
make install
```

注意：报错：failed to execute cmd " dot -Tpng" 请核对php.ini

```
在 php.ini 中 去掉 disable_functions 中的如下函数
system
shell_exec
proc_open
proc_get_status
```



