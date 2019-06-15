下载地址

```
https://www.libreoffice.org/download/download/ //失效去谷歌
```

进入目录

```
cd/tmp
```

下载软件

```
wget -c wget  https://download.nus.edu.sg/mirror/tdf/libreoffice/stable/6.2.4/rpm/x86_64/LibreOffice_6.2.4_Linux_x86-64_rpm.tar.gz
```

删除已安装的office

```
yum remove openoffice* libreoffice*
```

解压软件

```
tar -xvf LibreOffice_6.2.4_Linux_x86-64_rpm.tar.gz 
```

进入本软件rpm目录

```
cd LibreOffice_6.2.4.2_Linux_x86-64_rpm/RPMS/
```

安装rpm

```
yum localinstall *.rpm
```

打开软件

```
libreoffice6.2  //输入开头几个字符  table补全
```



