---
layout: post
title: Linux之系统管理
comments: true
date: 2016-04-03 14:04:05
updated:
tags:
- Linux
categories:
- Linux
permalink:
---

# 中文输入法

安装一个中文输入法框架fcitx(IBus, SCIM, UIM)：

    sudo add-apt-repository ppa:fcitx-team/nightly
    sudo apt-get update
    sudo apt-get install fcitx

安装适用于这种框架的输入法：

    sudo apt-get install fcitx-sunpinyin
    sudo apt-get install fcitx-libpinyin
    sudo apt-get install fcitx-googlepinyin

安装云拼音：

    sudo apt-get install fcitx-module-cloudpinyin

输入法模块(包括gtk2/3，qt4/5)：

    fcitx-im

配置程序：

    kcm-fcitx(qt)
    fcitx-configtool(gtk)

# gedit打开txt文件乱码

    sudo apt-get install dconf-editor

org->gnome->gedit->preferences->encodings->auto-detected
添加'GB2312','GBK',...

# virtualbox 开机自动挂载共享文件夹

    sudo vim /etc/rc.local
    mount.vboxsf -w ShareFolderNameOnWindows MountPointOnLinux

# 挂载U盘失败

移动硬盘或者u盘不能挂载，删掉/etc/fstab的关于sdb的行，保存后重新插拔。

# Linux修改hostname

    sudo vim /etc/hostname
    sudo vim /etc/hosts
    sudo reboot

# Linux创建桌面图标（比如eclipse）

    cd /usr/share/applications
    sudo vi XXX.desktop

添加必要属性后拖到桌面或启动栏即可。

# Linux安装QQ

    sudo apt-get install libgtk2.0-0:i386
    sudo apt-get install lib32ncurses5
    sudo apt-get install -f
    sudo dpkg -i fonts-wqy-microhei_0.2.0-beta-2_all.deb
    sudo dpkg -i ttf-wqy-microhei_0.2.0-beta-2_all.deb
    sudo dpkg -i wine-qqintl_0.1.3-2_i386.deb

# 安装文档的包

    sudo apt-get install glibc-doc manpages-dev manpages-posix-dev manpages-zh

手册位于/usr/share/man

# ufw & iptables

# upstart & systemd
