---
layout: post
title: Windows之wmi和cim
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

# wmi/cim

windows management instrumentation.

common information model.

命名空间:
root\cimv2
root\microsoftdns
root\securitycenter

windows自带wmi测试工具wbemtest.

# wmic

wmic是wmi的客户端。

windows的wmic：

    >wmic
    >-?
    >/?

linux的wmic：

Linux需要自己创建wmic命令，可以通过samba获取，也可以安装openvas的安装包。

    $man wmic
    $wmic -U [domain/]adminuser%password //host "select * from Win32_ComputerSystem"

<https://mikepalmer.net/debianubuntu-wmi-client-package-with-openvas-libwmiclient1-patches/>

# wql

like的操作符：
[]
^
%
_

    select * from meta_class where __class like '%win32%' # 查询wmi的类
    select * from meta_class where __class like '%cim%' # 查询cim的类

    select * from cim_datafile where drive="c:" and path=\\path\\" and filename like "%%" and extension='doc'
    select * from cim_directory where drive="c:" and path="\\path\\"
    select * from cim_logicaldisk
    select * from win32_operationsystem
    select * from win32_service
    select * from win32_process

# Python

## wmi

Windows安装[pywin32](https://sourceforge.net/projects/pywin32/?source=navbar)和[wmi](http://timgolden.me.uk/python/wmi/index.html)两个包,可以访问wmi。

    import wmi
    c = wmi.WMI()

## subprocess

Linux通过subprocess远程执行wmic命令。

    import subprocess
    wmi_output = subprocess.check_output(command)

# Java
