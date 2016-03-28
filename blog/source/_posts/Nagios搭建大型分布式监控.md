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

# Nagios发展

Nagios core 1.0

Nagios core 2.0

Nagios core 3.0

Nagios XI

Nagios core 4.0

目前nagios有两大阵营：

开源解决方案： Nagios core

商业解决方案： Nagios XI

***

# Nagios开源解决方案

## Nagios core:

>Nagios Core is the monitoring and alerting engine that serves as the primary application around which hundreds of Nagios projects are built.

Nagios core是监控和警报的主引擎，围绕它建立了成千上万的项目。
技术栈是c，只能安装在linux/unix系统。
Nagios core只是一个监控套件，本身没有监控功能，需要插件来完成监控。

## Nagios plugins:

>Efficient, standalone extensions that provide low-level intelligence for monitoring anything and everything with Nagios Core.

Nagios core的监控插件。
也就是官方插件,主要是c、shell和perl。

## Nagios frontends:

>Web interfaces, themes, Windows and Linux interfaces, and mobile apps for Nagios. Change the look and style of Nagios to suite your needs.

Nagios frontends包括了 主题,web接口,移动设备接口。

## Nagios configuration tools:

>Tools and GUIs for simplifying Nagios Core configuration.

nagios core的的组件。

包括NConf,Thruk,NagiosQL,Mod_gearman,mk-livestatus,NDOUtils,BPI,NSTI,NRDP(NSCA),NCPA(NRPE/NSCP)等addons。

## Nagios exchange:

>Nagios® Exchange is the central place where you'll find all types of Nagios projects - plugins, addons, documentation, extensions, and more. This site is designed for the Nagios Community to share its Nagios creations.

Nagios exchange是nagios的开源宝库。
包括第三方plugins、addons和docs。

[nagios-excnahge](https://exchange.nagios.org/https://exchange.nagios.org/)

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

## Nagios incident manager

***

# Nagios 集中监控

使用nagios core + plugins可以监控本地的linux/unix机器。

使用nagios core + plugins + addons（NCPA/NRPE）可以监控远程的linux/unix机器。

使用nagios core + plugins + addons（NCPA/NSCP）可以监控远程的windows机器。

***

# Nagios 分布式监控

Nagios的分布式监控方案有很多。

## NRDP/NSCA

## DNX

## Mod_gearman

![pic](/images/nagios.png)

这种架构监控几千台服务器和几万个服务没有压力。

***

# 安装配置

安装和配置nagios core,plugins,addons参考官方文档：

<https://assets.nagios.com/downloads/nagioscore/docs/nagioscore/4/en/toc.html>

***

# Nagios的插件开发

开发nagios plugins参考官方文档：

<https://nagios-plugins.org/doc/guidelines.html>

***

*Nagios配置和插件开发请看下回分解*
