+++
title = "萤石摄像头视频网页播放"
date = 2019-03-27T02:00:00+08:00
draft = false
categories = ["直播"]
tags = ["视频"]
toc = true
author = "zls3201"
author_homepage =  "http://www.zls3201.com/"
+++

### 1.获取摄像头的局域网rtsp地址

### 2.将rtsp视频流转换为Hls视频

#### a.采用FFMpeg转换，较为耗费资源
#### b.使用srs服务，基于linux
#### c.使用[Live555](http://www.live555.com/)相关代码自定义开发

### 3.网页采用Hls.js播放