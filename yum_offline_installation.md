# Yum Offline Installation

If the server is offline then you cannot use yum command.

Use another online server, and download yum packages, transfer to the target server. 

***

### Online Server

Your server must linked with Internet, and with yum active.

* Open yum download cache：

  ```
  #vim /etc/yum.conf keepcache=1 //1: cache open, 0: default, cache not open
  #yum install <SOFTWARE_NAME> //cache location: /var/cache/yum/base/packages
  ```

  go to `/var/cache/yum/updates/packages`

  ```
  #yum install yum-downloadonly
  #yum -y install --downloadonly <SOFTWARE_NAME>  //only download, no intalltaion
  ```

### Target Server

* Switch to your target server, who is offline.

  ```
  #yum -C update //config for updating yum with cache ahead
  #yum -C install <SOFTWARE_NAME> 
  #yum clean headers 
  #yum clean package //delete all packages in cache
  #sudo yum install yum-utils 
  #sudo yumdownloader <package-name> //download a rpm package
  ```




