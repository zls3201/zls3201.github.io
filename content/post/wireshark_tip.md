+++
date = "2018-09-05T00:00:00+08:00"
title = "Wireshark查看网络通讯数据包"
categories = ["Tip"]
tags = ["Test", "Bar"]
toc = true
+++

过滤条件窗口输入 目标主机的IP和Port组合条件即可,如下
~~~js
(ip.dst == 127.0.0.1 and tcp.dstport == 9090) or (ip.src == 127.0.0.1 and tcp.srcport == 9090)
~~~
关于localhost通讯抓包 要求卸载winpcap 安装npcap
效果如图
![图片](/wireshark_tip/1.jpg)