---
layout: post
title: Nagios搭建大型分布式监控
comments: true
date: 2016-03-25 11:15:48
updated:
tags:
- nagios
- monitoring
- DevOps
categories:
- DevOps
- Nagios
permalink:
---

# Nagios

## 什么是nagios

> Nagios is the industry standard in IT infrastructure monitoring

> Nagios offers complete monitoring and alerting for servers, switches, applications, and services.

Nagios官方宣称nagios是IT基础监控的工业标准。

Nagios提供对服务器，交换机，应用和服务的完整的监控和警报。

## 类似项目

开源项目：

Naemon, Icinga 和 Shinken 都是基于Nagios core开发的监控套件。

zabbix: 一个企业级的，开源的分布式监控套件。

zenoss: 新的开源监控套件。

***

# Nagios安装配置

## Nagios发展

Nagios core 1.0

Nagios core 2.0

Nagios core 3.0

Nagios XI

Nagios core 4.0

目前nagios有两大阵营：

开源解决方案： Nagios core

商业解决方案： Nagios XI

## Nagios安装配置

安装和配置nagios core,plugins,addons参考

官方文档:

<https://assets.nagios.com/downloads/nagioscore/docs/nagioscore/4/en/toc.html>

中文文档：

<http://nagios-cn.sourceforge.net/nagios-cn/index.html>

***

# Nagios开源解决方案

## Nagios core:

>Nagios Core is the monitoring and alerting engine that serves as the primary application around which hundreds of Nagios projects are built.

Nagios core是监控和警报的主引擎，围绕它建立了成千上万的项目。
技术栈是c，只能安装在linux/unix系统。
Nagios core只是一个监控套件，本身没有监控功能，需要插件来完成监控。

<https://www.nagios.org/projects/nagios-core/>

## Nagios plugins:

>Efficient, standalone extensions that provide low-level intelligence for monitoring anything and everything with Nagios Core.

Nagios core的监控插件,也就是官方插件,主要是c、shell和perl。

<https://www.nagios.org/projects/nagios-plugins/>

## Nagios frontends:

>Web interfaces, themes, Windows and Linux interfaces, and mobile apps for Nagios. Change the look and style of Nagios to suite your needs.

Nagios frontends包括了 主题,web接口,移动设备接口。

<https://www.nagios.org/downloads/nagios-core-frontends/>

## Nagios config tools(Nagios addons projects):

>Tools and GUIs for simplifying Nagios Core configuration.

nagios core的组件。

包括Lilac,NagiosQL,NConf,OneCMDB,ignoramus

<https://www.nagios.org/projects/nagios-config-tools/>

<https://www.nagios.org/downloads/nagios-core-addons/>

## Nagios exchange:

>Nagios® Exchange is the central place where you'll find all types of Nagios projects - plugins, addons, documentation, extensions, and more. This site is designed for the Nagios Community to share its Nagios creations.

Nagios exchange是nagios的开源宝库。

包括第三方plugins、addons和docs。

<https://exchange.nagios.org/https://exchange.nagios.org/>

***

# Nagios商业解决方案

## Nagios XI:

>Our most powerful IT infrastructure monitoring and IT monitoring software alerting solution for today’s demanding organizational requirements.

Nagios XI 是现代化的商业监控解决套件。

Nagios XI 使用nagios core 4.0。

Nagios XI 架构：

![pic](/images/nagiosxi.png)

## Nagios network analyzer

## Nagios log server

## Nagios fusion

做分布式监控。

## Nagios incident manager

***

# Nagios 集中监控

## 本地监控

使用nagios core + plugins只能监控本地的linux/unix机器。

## 远程监控

使用nagios core + plugins + addons可以监控远程的linux/unix/windows/mac机器。

NRPE/NRPE_NT和check_nrpe, 运行远程机器上的插件, 支持windows/unix/linux:

    nagios core + check_nrpe <=> NRPE/NRPE_NT + plugins

NSCP和check_nt, 只能使用固定的几个命令查基本属性, 支持windows和linux：

    nagios core + check_nt -v variable <=> NSCP(NSClient++)

NSCP和check_nrpe，可以传自己的命令或插件, 支持windows和linux：

    nagios core + check_nrpe -c command <=> NSCP

NSCP和NSCA/NRDP, NSCA提供被动检测, 支持windows和linux：

    nagios core + NSCA/NSCA-ng/NRDP <=> NSCP

NCPA是python写的跨平台代理, 支持linux/windows/mac：

    nagios core + check_ncpa.py <=> NCPA

check_MK_agent是一款先进的代理, 支持linux/windows：

    nagios core + Check_MK <=> check_mk_agent

***

# Nagios 分布式监控

Nagios的分布式监控方案有很多,性能最优的就是mod gearman，分布式监控基于集中监控。

## merlin

## check_MK

## NRDP/NSCA/NSCA-ng

官方推荐，NRDP是NSCA的升级版,提供被动检测,这种方式效率低，稳定性差。

    nagios core <- plugins <- NSCA <= send_nsca <- ocsp <- Nagios core <=> Hosts
                                  ^
                                 ||
                                 send_nsca <- ocsp <- Nagios core <=> Hosts

## Mod Gearman

![pic](/images/nagios.png)

这种架构监控几千台服务器和几万个服务没有压力。

***

# 其它组建介绍

## Mathias kethner

<http://mathias-kettner.com/index.html>

1. check_MK

    类似于mod gearman的分布式监控。

    <http://mathias-kettner.de/check_mk.html>

2. MK Livestatus

    其它的livestatus都是fork这个组件。

    <http://mathias-kettner.de/checkmk_livestatus.html>

3. MK MultiSite

    类似于thruk，基于check_mk的dashbord。

    <http://mathias-kettner.de/checkmk_multisite.html>

## op5

<https://www.op5.com/>

<http://git.op5.org/#/admin/projects/>

1. merlin

    类似与mod gearman的分布式监控。

    <https://kb.op5.com/display/MERLIN/Distributed+%28Merlin%29+Home>

2. Ninja

    类似于thruk, 基于merlin的dashbord。

3. check_vmware_api.pl

## consol labs

<https://labs.consol.de/>

<https://github.com/lausser?tab=repositories>

1. check_mssql_health.pl

## centreon

nagios的分布式监控管理平台

<https://www.centreon.com/en/>

## mod gearman

分布式监控。

<http://www.mod-gearman.org/>

## Thruk

基于perl的web框架catalyst的dashbord。

<http://www.thruk.org/>

## Nagvis

画nagios的地图,支持mk livestatus, NDOUtils, op5 merlin。

<http://www.nagvis.org/>

## Pnp4nagios

画nagios的性能图

<http://docs.pnp4nagios.org/>

## NDOUtils(NDO)

从nagios导出当前和历史数据到mysql数据库。

    N * (Nagios core + NDO module) -> TCP/Socket -> NDO2DB daemon -> DB

## Nagiosgraph

类似于Pnp4nagios

## NSTI

Nagios SNMP Trap Interface

***

