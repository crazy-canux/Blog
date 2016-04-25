---
layout: post
title: Linux系统管理
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

# 安装jre或jdk

    sudo apt-get install openjdk-7-jre
    sudo apt-get install openjdk-7-jdk

# debian/ubuntu安装rpm包

安装工具alien：

    sudo apt-get install alien

直接安装：

    sudo alien -i -c XXX.rpm

转换成deb包：

    sudo alien -d -c XXX.rpm
    sudo dpkg/alien -i XXX.deb

