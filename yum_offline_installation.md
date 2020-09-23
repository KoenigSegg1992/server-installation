# Yum Offline Installation

由于安全原因，很多机器只有内网策略，yum install命令无法获取资源，导致有很多安装复杂的软件无法使用这个便捷方式安装。
利用一台连接外网机器，把缓存复制到内网机器上，则可以实现内网机器使用yum install，比较方便简单。

***

###### 外网机器

先开启YUM下载缓存：
#vim /etc/yum.conf keepcache=1 //1表示启用缓存，默认为0，表示不启用
#yum install 软件名 //安装的软件包将被缓寸的/var/cache/yum/base/packages下，更新的软件包将被缓存到/var/cache/yum/updates/packages下
#yum install yum-downloadonly
#yum -y install --downloadonly 软件名  //只下载软件包、不安装

###### 内网机器（需要被部署的机器）

执行# yum -C update //只从缓存更新
#yum -C install <软件包名> //只从缓存安装注：清空 yum缓存
#yum clean headers要删除缓存中所有软件包，使用命令：
#yum clean package


$ sudo yum install yum-utils 下载一个RPM包：$ sudo yumdownloader <package-name> 