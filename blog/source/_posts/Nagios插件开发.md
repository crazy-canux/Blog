---
layout: post
title: Nagios插件开发
comments: true
date: 2016-04-01 13:12:15
updated:
tags:
- nagios
- monitoring
- Plugins
categories:
- DevOps
- Nagios
permalink:
---

# Nagios插件开发的文档

Nagios Plugin API:

<https://assets.nagios.com/downloads/nagioscore/docs/nagioscore/3/en/pluginapi.html>

Developing Plugins For Use With Embedded Perl:

<https://assets.nagios.com/downloads/nagioscore/docs/nagioscore/3/en/epnplugins.html>

Nagios Plugin Development Guidelines:

<https://nagios-plugins.org/doc/guidelines.html>

# Nagios插件开发

Nagios不是基于agent的，所以插件都是通过协议来获取监控信息。

1. windows:
    snmp
    wmi(wmic)

2. linux/unix:
    snmp
    ssh

3. network
    http
    https
    snmp

4. storage
    snmp

5. mssql
    freetds

6. mysql
    mysql

7. oracle
    sqlplus
