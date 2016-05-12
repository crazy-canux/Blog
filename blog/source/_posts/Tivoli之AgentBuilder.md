---
layout: post
title: ITM之AgentBuilder
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

# uninstall agent

1. uninstall from commandline.

    windows:

        cd C:\IBM\ITM\TMAITM6_x64
        Kxx_uninstall.vbs C:\IBM\ITM

    linux/unix:

        /opt/IBM/ITM/bin/uninstall.sh -f -i -h /opt/IBM/ITM [product_platformCode]

2. Remove from TEP client(clear off-line entry)

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

