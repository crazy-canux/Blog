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

# Monitoring(Nagios/naemon/icinga/shinken/sensu) Plugins

Office project:

<https://github.com/monitoring-plugins>

<https://www.monitoring-plugins.org/>

My project:

<https://github.com/crazy-canux/xPlugin_Monitoring>

<http://crazy-canux.github.io/2016/04/08/Monitoring%E4%B9%8BPlugins/>

Open source project:

<https://github.com/crazy-canux/awesome-monitoring>

## Windows monitoring

* check_wmi_plus.pl

    <http://www.edcint.co.nz/checkwmiplus/>

## Vitual Machine monitoring

* check_wmware_api.pl

    <https://kb.op5.com/display/PLUGINS/Check+VMware+API+nagios+plugin>
    <http://git.op5.org/gitweb?p=system-addons%2Fplugins%2Fop5%2Fcheck_vmware_api.git;a=summary>

* check_vmware_esx.pl

    <https://github.com/BaldMansMojo/check_vmware_esx>

## DB monitoring

* check_mysql_health.pl

    <https://github.com/lausser/check_mysql_health>

* check_oracle_health.pl

    <https://github.com/lausser/check_oracle_health>

* check_db2_health.pl

    <https://github.com/lausser/check_db2_health>

* check_mssql_health.pl

    <https://github.com/lausser/check_mssql_health>

## Log monitoring

* check_logfiles.pl

    <https://github.com/lausser/check_logfiles>

* check_events.pl

    <https://kb.op5.com/display/PLUGINS/check_events.pl>
    <https://sites.google.com/site/peterwirdemo/home/nagios-plugins>

## Network monitoring

* check_nwc_health.pl

    <https://github.com/lausser/check_nwc_health>

## Application monitoring

* check_sap_health.pl

    <https://github.com/lausser/check_sap_health>

* check_mailbox_health.pl

    <https://github.com/lausser/check_mailbox_health>

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
