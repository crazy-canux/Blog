---
layout: post
title: Monitoring之check_MK
comments: true
date: 2016-05-12 00:19:01
updated:
tags:
- check_mk
- livestatus
- Multisite
categories:
- DevOps
- Monitor
permalink:
---

# check_MK

check_Mk有两个版本：
1. Raw edition(开源版本)
2. Enterprise edition(商业版本)

check_Mk是基于agent的，需要在被监控机器上安装agent。

check_MK包括mk livestatus等组件。

<http://mathias-kettner.com/check_mk.html>

<http://git.mathias-kettner.de/git/?p=check_mk.git;a=tree>

<http://mathias-kettner.com/check_mk_exchange.php?HTML=yes>

![pic](/images/mkdis.PNG)

***

# OMD

The Open Monitoring Distribution

用于快速部署基于nagios的分布式监控，包括：
1. Icinga
2. Shinken
3. check_mk
4. 基于mod-gearman/MK Livestatus/thruk的分布式监控。
5. 其它组件。

<http://omdistro.org/>

<http://git.mathias-kettner.de/git/?p=omd.git;a=tree>

***

# check_MK macro core

是nagios core的升级版，用python写的。

![pic](/images/check_mk.PNG)

***

# MK livestatus

Event broker,是NDO的升级版,不需要数据库。

支持：
1. mk Multisite
2. thruk
3. nagvis
4. BPI
5. CoffeeSaint
6. RealOpInsight

***

# Multisite

check_MK的Dashboard。

***

# WATO

check_mk的配置工具。

***

# Notify

***

# Event Console

***

# install check_mk

安装工具gdebi：

    sudo apt-get install gdebi-core

安装正确的版本：

    sudo gdebi check-mk-raw-1.2.8p1_0.trusty_amd64.deb

检查是否安装成功：

    omd version

***

# Use check_mk

    sudo -i

创建一个instances：

    omd create mysite

启动instances：

    omd start mysite

登陆Multisite:

http://HOSTNAME/mysite/

username: omdadmin

password: omd

***

# Use WATO and Multisite

1. Install Monitoring Agents on monitoring server
2. Activating servers
3. Activating services

***

# Use notify and event console
