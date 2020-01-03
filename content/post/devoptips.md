+++
title= "分布式运维Tips"
date= 2018-05-23T09:36:35+08:00
draft= false
categories = ["dev"]
tags = ["study","calcute"]
toc = true
author = "zls3201"
author_homepage =  "http://www.zls3201.com/"
+++

### 系统管理与自动化
+ [ansible](https://github.com/ansible/ansible)<br>
+ [salt](https://github.com/saltstack/salt)<br>
+ [puppet](https://github.com/puppetlabs/puppet)<br>
+ [chef](https://github.com/chef/chef)<br>


阅读资料<br>
[ansible和puppet的安装和比较](https://blog.csdn.net/wn_hello/article/details/52130573)<br>
[翻译-Salt与Ansible全方位比较](http://www.cnblogs.com/huang0925/p/4664608.html)<br>
[Puppet、Chef、Ansible和SaltStack四大运维管理工具]( http://blog.51cto.com/liqilong2010/1850617)<br>
[Ansible中文权威指南](http://ansible-tran.readthedocs.io/en/latest/index.html)


### 容器与容器管理
* [Docker](https://github.com/docker/docker-ce)
* [Rocket（已改名rkt）](https://github.com/rkt/rkt)
* [hyper](https://hyper.sh/)
* [runC](https://github.com/opencontainers/runc)
* [gvisor](https://github.com/google/gvisor)

阅读资料<br>
[容器，你还只用Docker吗？（上）](http://www.yunweipai.com/archives/10328.html)<br>
[容器，你还只用Docker吗？（下）](http://www.yunweipai.com/archives/10358.html)<br>
[安装并运行RunC](http://dockone.io/article/680)<br>
[riddler](https://github.com/genuinetools/riddler) docker image to runc转换工具<br>
[30个不可不知的容器技术工具和资源](http://dockone.io/article/2097)<br>


### 微服务相关
[Consul](https://www.consul.io/) 服务发现注册 健康监测 kv存储 leader选举 多数据中心<br>
[fabio](https://github.com/fabiolb/fabio) Consul Load-Balancing<br>
[Ocelot](https://github.com/ThreeMammals/Ocelot) .NET core API Gateway<br>
[butterfly](https://github.com/ButterflyAPM/butterfly) A distributed tracing system and application performance monitoring.<br>
[Appmetrics](https://www.app-metrics.io/) an open-source and cross-platform .NET library used to record metrics within an application<br>

Consul 阅读资料<br>
https://www.jianshu.com/p/f8746b81d65d
https://cecilphillip.com/using-consul-for-service-discovery-with-asp-net-core/
https://www.cnblogs.com/lori/p/8391351.html
https://github.com/PlayFab/consuldotnet
http://www.cnblogs.com/shanyou/p/4714838.html
http://www.csharpkit.com/2017-10-07_55898.html
http://www.cnblogs.com/xishuai/p/ubuntu-docker-consul-fabio-aspnet-core.html

Ocelot<br>
https://www.cnblogs.com/axzxs2001/p/8478340.html
https://www.cnblogs.com/axzxs2001/p/8005041.html
http://www.cnblogs.com/shanyou/p/7787183.html
https://www.cnblogs.com/axzxs2001/p/8487521.html
http://www.cnblogs.com/axzxs2001/p/8005101.html

[Ocelot中使用Butterfly实践](http://www.cnblogs.com/axzxs2001/p/8478340.html)

### 时序数据库TSDB
[InfluxDB](https://portal.influxdata.com/downloads)