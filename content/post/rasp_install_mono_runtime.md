+++
title= "树莓派安装mono运行环境"
date= 2016-06-01T15:25:04+08:00
draft= false
categories = ["rasp"]
tags = ["rasp","mono","asp.net","dotnet"]
toc = true
author = "zls3201"
author_homepage =  "http://www.zls3201.com/"
+++

```bash

sudo apt-get install build-essential automake autoconf bison gettext libtool libglib2.0-dev libfreetype6-dev libfontconfig-dev
sudo apt-get install libgif-dev libtiff4-dev libpng12-dev libexif-dev libx11-dev libxft-dev libjpeg-dev

sudo apt-get install libcairo2-dev


wget http://download.mono-project.com/sources/libgdiplus/libgdiplus-4.2.tar.gz
tar zxf libgdiplus-4.2.tar.gz
cd libgdiplus-4.2 
./configure --prefix=/usr
make
sudo make install

wget http://download.mono-project.com/sources/mono/mono-4.4.0.148.tar.bz2
tar jvxf mono-4.4.0.122.tar.bz2
cd mono-4.4.0.122
./configure --prefix=/usr
make
sudo make install
```
