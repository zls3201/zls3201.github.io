+++
title = "Virtualbox安装配置alpine"
date = 2018-12-08T09:56:19+08:00
draft = false
+++

# 1.安装virtualbox

# 2.安装alpine linux
参考 https://wiki.alpinelinux.org/wiki/Install_Alpine_on_VirtualBox
```
    apk add nano vim curl wget git mercurial subversion
    curl https://j.mp/spf13-vim3 -L > spf13-vim.sh && sh spf13-vim.sh
    nano /etc/ssh/sshd_config
    rc-service sshd restart

```
服务管理 
https://wiki.alpinelinux.org/wiki/Alpine_Linux_Init_System

# 3.在alpine linux中安装共享文件夹支持
参考 https://wiki.alpinelinux.org/wiki/VirtualBox_shared_folders
```
echo "http://dl-cdn.alpinelinux.org/alpine/edge/community" >> /etc/apk/repositories
apk update
apk add virtualbox-guest-additions virtualbox-guest-modules-virt
```

# 4.在alpine linux中安装Docker
参考 https://wiki.alpinelinux.org/wiki/Docker

# 5.安装dotnet core sdk
下载 https://dotnet.microsoft.com/download/dotnet-core/2.2
参考 https://dotnet.microsoft.com/download/thank-you/dotnet-sdk-2.2.100-linux-x64-binaries
```
    apk add --no-cache libstdc++ gettext libunwind-dev icu openssl-dev
```
# 6.安装mariadb
参考 https://wiki.alpinelinux.org/wiki/MariaDB
```
    apk add mariadb mariadb-client
    chown -R mysql:root /var/lib/mysql
    /etc/init.d/mariadb setup
    rc-update add mariadb default
    mysql -u
    GRANT ALL PRIVILEGES ON *.* TO 'root'@'%'  IDENTIFIED BY 'root' WITH GRANT OPTION;
```