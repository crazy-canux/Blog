---
layout: post
title: ITM
comments: true
date: 2016-04-20 13:57:31
updated:
tags:
- ITM
- IBM
- Tivoli
- Monitoring
categories:
- DevOps
- Tivoli
permalink:
---

# ITM

ITM: IBM Tivoli Monitoring

是IBM的Cloud & Smart Infrastructure监控解决方案。

Architecture Overview:

![pic](/images/tivoli.png)

ITM主要由管理组件和可选组件组成。

Tivoli Management Services:

1. TEP
2. TEPS
3. TEMS
4. TEMA

Optional components:

1. History data collection
2. Dashboard Application Services Hub

# TEMS

TEMS:  Tivoli Enterprise Monitoing Server

TEMS分为remote和hub，remote最后都汇总到hub。

HTEMS: Hub Tivoli Enterprise Monitoring Server

RTEMS: Remote Tivoli Enterprise Monitoring Server

一个TEMS建议管理700个agent

# TEMA

TEMA: Tivoli Enterprise Monitoring Agent

## Agentless

TEMS -> Agentless server -> servers

就是用一个中间服务器通过snmp等协议来监控不需要安装agent的被监控服务器。

一个agentless可以设置10个实例(操作系统)，一个实例可以监控100个节点(被监控服务器)。

Agentless Monitoring for AIX OS - SNMP

Agentless Monitoring for HP-UX OS - SNMP

Agentless Monitoring for Linux OS - SNMP

Agentless Monitoring for Solaris OS - SNMP,CIM-XML

Agentless Monitoring for Windows OS - SNMP,WMI

## Agent

TEMS -> servers(agent)

一个agent连2个TEMS,一个primary，一个backup。

agent分为：

1. Operating System agent
2. Application agent
3. specialized agent

specialized agent有：
1. warehouse proxy agent
2. summarization and pruning agent
3. tivoli log file agent
4. agent builder agents

# TEPS+DB

TEPS: Tivoli Enterprise Portal Server

# TEP(client)

TEP -> TEPS

TEP: Tivoli Enterprise Portal

TEP是GUI界面，分为：
1. Desktop
2. Browser
3. JavaWS: java web start

# DASH

DASH: Dashboard Application Services Hub

## Tivoli Monitoring dashboards

## Tivoli Common Reporting

## Tivoli Enterprise Monitoring Automation Server

# History data collection

## TDW+DB

TDW: Tivoli Data Warehouse

存储历史数据。支持DB2，Oracle， MSSQL。

## Warehouse Proxy agent

TDW使用该agent从agents收集和加载数据。

## Summarization and Pruning agent

TDW使用该agent控制数据库大小。

# Management

管理所有组件一般使用GUI叫MTEMS，windows/linux/unix都可以用。

其次是命令行模式。

## tacmd

支持windows/linux/unix。

/opt/IBM/ITM/bin/tacmd
C:\IBM\ITM\bin\tacmd

查看tacmd手册：

    ./tacmd help
    ./tacmd ?

登陆和登出HTEMS:

    ./tacmd login -s [PROTOCOL://]HOST[:PORT] -u [USERNAME] -p [PASSWORD] -t [TIMEOUT]
    ./tacmd logout

登陆和登出TEPS：

    ./tacmd tepsLogin -s [TEPS_HOSTNAME] -u [USERNAME] -p [TEPS_PASSWORD] -t [TIMEOUT] -i [IGNORE]
    ./tacmd tepsLogout

管理agent：

    ./tacmd startAgent/stopAgent ???

刷新Netcool/OMNIbus：

    ./tacmd refreshTECinfo {-t|--type} {eif|maps|attr|all}

## itmcd

用于Linux/Unix系统的命令

/opt/IBM/ITM/bin/itmcmd

查看itmcmd手册：

    ./itmcmd help
    ./itmcmd ?

启动或停止TEMS:

    ./itmcmd server [-options] {start|stop} tems_name

启动或停止agent：

    ./itmcmd agent [-options] {start|stop} {pc ...|all}

启动MTEMS(manage tivoli enterprise monitoring services):

    ./itmcmd manage &

## tivcmd


