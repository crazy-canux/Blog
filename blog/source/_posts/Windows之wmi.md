---
layout: post
title: Windows之wmi
comments: true
date: 2016-04-03 14:15:47
updated:
tags:
- Windows
- wmi
categories:
- Windows
permalink:
---

# wmic

wmic是wmi的客户端。

windows的wmic：

    cmd->wmic
    /?

linux的wmic：

Linux需要自己创建wmic命令，可以通过samba获取，也可以安装openvas的安装包。

    man wmic
    wmic -U [domain/]adminuser%password //host "select * from Win32_ComputerSystem"

<https://mikepalmer.net/debianubuntu-wmi-client-package-with-openvas-libwmiclient1-patches/>

# Python

## wmi

Windows安装[pywin32](https://sourceforge.net/projects/pywin32/?source=navbar)和[wmi](http://timgolden.me.uk/python/wmi/index.html)两个包,可以访问wmi。

    import wmi
    c = wmi.WMI()

## subprocess

Linux通过subprocess远程执行wmic命令。

    import subprocess
    wmi_output = subprocess.check_output(command)
