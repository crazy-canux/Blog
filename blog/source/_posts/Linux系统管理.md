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

# 安装中文输入法

安装一个中文输入法框架fcitx：

    sudo apt-get install fcitx

安装适用于这种框架的输入法：

    sudo apt-get install fcitx-sogoupinyin
    sudo apt-get install fcitx-googlepinyin

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

