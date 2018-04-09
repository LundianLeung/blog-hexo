---
title: 开机出现grub rescue解决办法
data: 2018-04-09 12:02:34
tag: grub
---

​	最近发现了一个Android-X86的RemixOS的系统，于是就想下载下来装着玩玩，结果装完开机就出现

> grub rescue>

出现这种情况一般是由于磁盘分区导致grub引导文件找不到了，因此只要我们让它找到引导文件即可。

首先我们先输入

> grub rescue> set

查看现在的grub引导指向那个盘，

```photo-1
prefix=(hd0,msdos5)/boot/grub
root=hd0,msdos5
```

表明现在grub指向的是第一块磁盘的第7块分区，引导文件不再此分区。然后使用`ls`命令查看磁盘的分区情况，

> grub rescue> ls

```photo-2
(hd0) (hd0,msdos5) (hd0,msdos4) (hd0,msdos3) (hd0,msdos2) (hd0,msdos1) (hd0,msdos0) (hd0,msdos6) (hd1)
```

接下来我们就要找到引导文件所在的分区，使用

> ls (hd0,msdos5)/

一个一个尝试，如果出现了grub字样，则说明引导文件就在此分区。我的引导文件恰巧就在（hd0，msdos5）分区。

找到分区之后使用

> set root =hd0,msdos5
>
> prefix=(hd0,msdos5)/boot/grub

将引导程序指向此分区，使用`set` 查看是否设置成功，然后在依次输入

> insmod normal
>
> normal

电脑重启进入启动界面，然而并没有完，如果你再关机，下次启动是还会出现`grub rescue`。

所以还需要进入你的Linux系统，在终端下输入

> sudo update-grub
>
> sudo grub-install /dev/sda

`sda`表示你的第一块磁盘

如果使用`/dev/sda`报错的话，那么请使用

> ls /dev/sd*

查看你的硬盘使用情况，选择一个正确的磁盘和分区。