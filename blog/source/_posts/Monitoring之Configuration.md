---
layout: post
title: Monitoring之Configuration
comments: true
date: 2016-09-25 23:15:38
updated:
tags:
- nagios
- configuration
categories:
- Operation
- Monitor
permalink:
---

# Nagios的配置

<http://nagios-cn.sourceforge.net/nagios-cn/index.html>

<http://nagios-cn.sourceforge.net/nagios-cn/configuration.html>

/usr/local/nagios/etc/或/etc/nagios

# nagios.cfg

<http://nagios-cn.sourceforge.net/nagios-cn/configuration.html#configmain>

/etc/nagios/nagios.cfg 是主配置文件。

    # 指定对象文件和路径，后者会覆盖前者的定义
    cfg_file=/etc/nagios/notification.cfg
    cfg_dir=/etc/nagios/repository

    # 指定资源文件
    resource_file=/etc/nagios/resources.res

    # 指定时间间隔长度，所有其它nagios的interval时间都是这个单位的倍数，默认是一分钟
    interval_length = 609(s)

# 资源配置文件

    $USERn$ # 在资源文件中定义变量，n的范围是[1,256]

# CGI配置文件

# 对象定义文件

    $ARGn$ # 位置参数变量，n范围是[1,32]
