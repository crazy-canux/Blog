---
layout: post
title: Monitoring之Plugins
comments: true
date: 2016-04-08 16:17:39
updated:
tags:
- nagios
- plugin
categories:
- DevOps
- Monitor
permalink:
---

# Nagios/naemon/icinga/shinken/sensu Plugins

* check_wmi_plus.pl

    <http://www.edcint.co.nz/checkwmiplus/>

* check_wmware_api.pl

    <https://kb.op5.com/display/PLUGINS/Plugins+Home>

    <http://git.op5.org/#/admin/projects/system-addons/plugins/op5/check_vmware_api>

* check_vmware_esx.pl

    <https://github.com/BaldMansMojo/check_vmware_esx>

* check_mssql_health.pl

    <https://labs.consol.de/nagios/check_mssql_health/index.html>

    <https://github.com/lausser/check_mssql_health>

***

# Nagios插件开发

Nagios Plugin API:

<https://assets.nagios.com/downloads/nagioscore/docs/nagioscore/3/en/pluginapi.html>

Developing Plugins For Use With Embedded Perl:

<https://assets.nagios.com/downloads/nagioscore/docs/nagioscore/3/en/epnplugins.html>

Nagios Plugin Development Guidelines:

<https://nagios-plugins.org/doc/guidelines.html>

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

***

# check_MK插件开发
