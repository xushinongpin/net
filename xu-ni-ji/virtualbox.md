安装的浏览器闪屏    ===    设置-显示-去掉启动3D加速



# Oracle VM VirtualBox安装增强功能和共享文件夹的方法



一、介绍下如何安装增强功能 

1\)选择安装增强功能的安装包有2种方法，分别如下： 

第一种：找到设备-&gt;安装增强功能 

 

第二种 

1\)找到设备-&gt;点击选择虚拟盘。 

 

2\)找到VirtualBox-&gt;VBoxGuestAdditions.iso文件。 



二、介绍如何共享文件夹 

1\)找到菜单栏上的设备-&gt;选择共享文件夹-&gt;创建共享文件夹\(共享文件夹就是本电脑共享文件夹，该文件夹设置自动挂载分配，这样每次启动虚拟机就可以进行共享文件。\) 



2\)重新进入虚拟Ubuntu，在命令行终端下输入： 

sudo mkdir /mnt/sharing 新创建一个挂载点； 

sudo mount -t vboxsf Share /mnt/sharing 进行挂载 

执行下ls 看下有没有挂载成功。 



3\)如果不想每次启动后都进行挂载的话，可以设置为自动挂载，如果有选中“Auto-mount”的选项的话,可在/media/目录下看到你共享的名字sf\_name;例如共享的文件夹名字为share，那就看到sf\_share。 

三、在本系统关联虚拟机上的系统，进行文件共享。 

点击桌面上的网络右击鼠标，选择映射网络驱动器，其中的文件夹的路径，为共享文件夹的路径，最后在电脑中的网络位置，出现共享文件的图标，双击该文件夹，显示了共享的内容。 

