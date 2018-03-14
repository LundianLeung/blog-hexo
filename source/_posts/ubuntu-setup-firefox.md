---
title: Ubuntu17.10手动安装Firefox
date: 2018-01-23 17:25:34
tag: Firefox
---

# Ubuntu 17.10 手动安装Firefox

首先是去[Firefox官网](https://www.mozilla.org/zh-CN/firefox/new/)下载Firefox的Linux平台包，找到最新的Linux版本，下载后得到Firefox-xx.tar.bz2，然后解压到本地。

> tar -xvf Firefox-xx.tar.bz2

得到一个Firefox文件夹。然后更改一下用户的执行权限，

> cd firefox
>
> sudo chmod 755 *

为了便于管理（当然根据个人的习惯），将此文件夹移到/opt文件夹下面，

> sudo mv firefox /opt

此时你若直接运行文件夹中的firefox的话， 弹出的仍然是旧版本的Firefox，所以为了方便使用，还需要更改一下/usr/bin/firefox的指向，先备份该文件，

> sudo mv /usr/bin/firefox /usr/bin/firefox-old

然后创建新文件：

> sudo ln -s /opt/firefox/firefox /usr/bin/firefox

执行成功后，注销一下，重新登录后，就尽情享用Firefox了。



