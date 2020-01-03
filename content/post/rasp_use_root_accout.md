+++
title= "树莓派使用root账户"
date= 2016-06-01T15:32:51+08:00
draft= false
categories = ["rasp"]
tags = ["raspberry"]
toc = true
author = "zls3201"
author_homepage =  "http://www.zls3201.com/"
+++

树莓派默认账户是pi 默认密码是raspberry

在默认账户下激活root账户

输入一下命令
sudo passwd root
在执行完该命令后 系统会提示 输入两次密码 那么就输入 你设定的密码
再执行解锁账户命令 
sudo passwd -unlock root

这样的话你的 root账户就激活了

接下来可以切换账户了
从普通账户切换到 root账户 直接输入 su root 就可以了 同样的道理 从root账户切换到普通账户 输入 su pi

虽然我们激活了root账户 但是远程登录root账户的时候还是会被拒绝 这个时候是因为 在/etc/ssh/sshd_config
里面的内容没有修改 
直接 cd /etc/ssh 后 数据 nano sshd_config 将里面的
将 PermitRootLogin without-password 修改为 PermitRootLogin yes
就可以了 
然后保存退出 
再重新登陆试试 就可以了
