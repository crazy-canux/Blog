---
layout: post
title: Tivoli之AgentBuilder
comments: true
date: 2016-04-25 10:19:28
updated:
tags:
- ITM
- IBM
- Tivoli
- Monitoring
- Agent Builder
categories:
- DevOps
- Tivoli
permalink:
---

# Agent Builder

IBM Agent Builder agents

windows:

    C:\Program Files(x86)\IBM\AgentBuilder

aix/linux:

    /opt/ibm/AgentBuilder

Data source:
1. JDBC
2. HTTP
3. SOAP
4. Ping
5. Socket
6. Java API

# Universal Agent

Data source:
1. ODBC
2. SOCKET
3. API
4. POST

# create agent

Every agent have a unique produce code.

Like: k00-k99, k{0-9}{A-Z}.

1. Create the agent in the Agent Builder
    agent information
    data source
    runtime configuration

2. Install and test the agent
    output and install the agent
    config and start agent in MTEMS.
    confirm agent data
    revise and retest as needed

3. Add application support
    create in TEP, including queries, workspaces, situations, and take actions.
    Import application support into agent in Agent Builder.
    Retest the agent and application support

4. Create an installation solution.
    Create solution install package from the agent.
    Create solution install package from the package.
    Run the image on the target location.

# install agent

Three ways to instal the agent.

You must install the TEMS and TEPS support on TEMS and TEPS server.

1. generate the agent files in an ITM installation on this machine

    通过GUI快速安装，Agent Builder和ITM（TEMS和TEPS）安装在同一台机器上。

2. generate a solution install package

    创建安装镜像来安装，windows的.exe和linux/unix的.bin。

3. create a compressed file so that the agent can be installed on another system

    命令行安装。
    生成一个.zip和一个.tgz文件。
    包括windows的.bat和linux/unix的.sh安装文件
    installIra.sh/bat 安装下面三个文件和第一种方式一样。

    安装下面三个包：

        InstallIra.bat/.sh itm_install_location [[-h Hub_TEMS_hostname] -u HUB_TEMS_username -p Hub_TEMS_password]
        InstallIra.bat C:\IBM\ITM -h <HTEMS> -u <username> -p <password> # for windows
        ./InstallIra.sh /opt/IBM/ITM -h <HTEMS> -u <username> -p <password> # for linux

    在被监控机器安装agent:

        installIraAgent.bat/.sh itm_install_location
        installIraAgent.bat C:\IBM\ITM # for windows
        ./installIraAgent.sh /opt/IBM/ITM # for linux

    在TEMS服务器安装对agent的支持：

        installIraAgentTEMS.bat/.sh itm_install_location [[-h Hub_TEMS_hostname] -u HUB_TEMS_username -p Hub_TEMS_password]
        installIraAgentTEMS.bat C:\IBM\ITM -h <HTEMS> -u <username> -p <password> # for windows
        ./installIraAgentTEMS.sh /opt/IBM/ITM -h <HTEMS> -u <username> -p <password> # for linux

    在TEPS服务器安装对agent的支持：

        installIraAgentTEPS.bat/.sh itm_install_location
        installIraAgentTEPS.bat C:\IBM\ITM # for windows
        ./installIraAgentTEPS.sh /opt/IBM/ITM # for linux

# config agent

可以通过MTEMS来配置和启动，也可以通过命令行。

config agent:

    ./itmcmd config -A <product code>

start agent:

    ./tacmd agent start <product code>

# uninstall agent

1. uninstall from commandline.

    windows:

        cd ITM_INSTALL/TMAITM6
        cd C:\IBM\ITM\TMAITM6_x64
        kxx_uninstall.vbs ITM_INSTALL
        K<product code>_uninstall.vbs C:\IBM\ITM

    linux/unix:

        /opt/IBM/ITM/bin/cinfo -i # check the product and platformCode.
        /opt/IBM/ITM/bin/uninstall.sh [-f] [-i] [-h install_dir] product platformCode

2. Remove from TEP client(clear offline entry)

# Monitoring windows resources

1. Windows Management Instrumentation(WMI)

2. Windows Performance Monitor(Perfmon)

3. Windows Event Log

# Monitoring process and command return codes

1. Monitoring process

2. Monitoring command return code

# Monitoring custom data sources

1. Monitoring script output

2. Monitoring log file

# Monitoring remote resources

1. Monitoring SNMP

2. Monitoring CIM

3. Moitoring JMX

