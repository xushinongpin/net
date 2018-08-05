查找某个文件     find / -name httpd.conf



查找rpm安装源    rpm -qa \| grep sql



退出vi编辑       :q退出  :wq保存退出



mv  修改前文件（夹）名   修改后文件（夹）名  eg: mv /home/www /home/lvtianshop

cp -rf 复制当前目录 复制后目录

pwd  查看当前路径





新建目录   mkdir 文件夹名称

删除目录   rm -r lvtian

递归删除目录  rm -rf /home/lvtianshop/





解压  unzip XXX.zip -d 解压目录



复制一个目录到另一个目录  cp -a \* /home/lvtianshop/www/ /home/shop



递归修改目录权限  chmod \[755\] shop -R

修改文件权限      chmod \[755\] index.php



----------------------------------

apache







配置路由 /opt/lampstack/apache2/conf/extra/httpd-vhosts.conf





重启apache   /opt/lampstack/apache2/bin/apachectl restart

重启mysql    /opt/lampstack/mysql/bin/mysqld restart







-----------------------------------------------

Bitnami

安装镜像服务商：https://market.aliyun.com/products/53398003/cmjj012827.html?spm=5176.2020520101.image.selectFromMarketplace.fqfqVq

启动所有服务

sudo /opt/lampstack/ctlscript.sh start





重启特定服务

sudo /opt/lampstack/ctlscript.sh restart apache

sudo /opt/lampstack/ctlscript.sh restart mysql



获取所有服务的当前状态

sudo /opt/lampstack/ctlscript.sh status



WordPress下载  -c断点续传

wget -c https://downloads.bitnami.com/files/stacks/wordpress/4.7.5-1/bitnami-wordpress-4.7.5-1-module-linux-x64-installer.run





-------------------------------------------------

安装的linux系统

https://market.aliyun.com/products/53398003/cmjj018355.html?spm=5176.2020520101.image.selectFromMarketplace.0jkEVc



目录说明：

软件包目录：/usr/local/src

软件安装目录：/usr/local

网站目录：/usr/local/apache/htdocs

数据库目录：/data/mysql

安装包保留情况：全部保留



修改说明：

网站子目录修改：/usr/local/apache/conf/httpd.conf（修改server下面的root后面）

数据库存放修改：/etc/rc.d/init.d/mysql



操作说明：

Apache：service httpd start\|stop\|restart（启动\|停止\|重启）

Mysql：service mysqld start\|stop\|restart（启动\|停止\|重启）

php： service php-fpm start\|stop\|restart（启动\|停止\|重启）



修改mysql密码：  SET PASSWORD FOR 'root'@'localhost' = PASSWORD\('HAOhaizi666!'\);



查看进程

sudo systemctl status mysql



关机重启

shutdown -r now





-------------------------------------------------------

自配

http://blog.noark9.com/2016/07/23/LAMP-on-CentOS7/

虚拟主机配置  vim /etc/httpd/conf/httpd.conf

ssl证书       https://www.phpini.com/linux/rhel-centos-7-install-apache-mod\_ssl





-------------------------------------

目前linux环境配置地址

https://market.aliyun.com/products/53398003/cmjj018301.html?spm=5176.730005.0.0.tINKYQ



 

目录说明：

软件包目录：/usr/local/src

软件安装目录：/usr/local

网站目录：/data/wwwroot

数据库目录：/data/mysql

安装包保留情况：全部保留

 

账号说明：

Mysql账号：root

Mysql密码：HAOhaizi666!

 

访问说明：

PhpMyAdmin访问：http://您的IP/phpmyadmin

网站访问：http://您的IP

 

修改说明：

网站子目录修改：/usr/local/nginx/conf/nginx.conf（修改server下面的root后面）

数据库存放修改：/etc/rc.d/init.d/mysql

 

操作说明：

Nginx：service nginx start\|stop\|restart（启动\|停止\|重启）

Mysql：service mysqld start\|stop\|restart（启动\|停止\|重启）



修改memcache大小   vi /etc/init.d/memcached

		   kill -9 pid    \(pid从ps aux查找\)终结

		   service memcached start    重启

		   





nginx启动          sudo systemctl start nginx

nginx重启          sudo systemctl reload nginx

nginx开机自动启动  sudo systemctl enable nginx

查看状态	   systemctl status nginx.service



php重启            sudo systemctl reload php-fpm

php 自动启动       sudo systemctl enable php-fpm

查看状态	   systemctl status php-fpm



mysql重启          sudo systemctl reload mysql

mysql 自动启动     sudo systemctl enable mysql

查看状态	   systemctl status mysql



重置表  truncate table zlc\_core\_cache



修改权限           chmod -R 777 shop/





http://6ee18d3831c7f8e35fd3df7ab1b6b8f3.ilvtian.cn/index.php  数据库

用户密码

用户：root

密码：HAOhaizi666!

