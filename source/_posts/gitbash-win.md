---
title: Windows上Git Bash配置
data: 2018-04-10 23:10:38
tags: "git"
categories: "工具软件使用"
---

首先正确安装Git，完成安装后，可以根据自己的喜好自定义Gitbush的外观（左键单击Gitbush左上角选择Options...进行选择），然后下载配置Git所必须的文件，本文后面附带百度网盘链接下载，然后启动Git Bush进行配置：

第一步：将下载的文件移动到主目录中，命令行如下：

> cd ~
> mv xxxxx/git-completion.bash.txt git-completion.bash
> mv xxxxx/git-prompt.sh.txt git-prompt.sh
> mv xxxxx/bash_profile_course .bash_profile  
> // xxxxx代表下载的文件所在的目录

第二步：配置Git编辑器，命令行如下：

> git config --global core.editor "'xx/xxx/sublime_text.exe' -n -w"
> git config --global push.default upstream
> git config --global merge.conflictstyle diff3
> git config --global user.name "xxx"
> git config --global user.email "xxx@gmail.com"

至次你的Git就已配置完毕。

git bash文件下载连接：链接：https://pan.baidu.com/s/1XZsYCr_ovBVyCZ3tWhwD9g 密码：fphz