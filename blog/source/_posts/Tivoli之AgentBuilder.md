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

Universal Agent(UA) 已经被AgentBuilder取代。

windows:

    C:\Program Files(x86)\IBM\AgentBuilder

aix/linux:

    /opt/ibm/AgentBuilder

<http://www-933.ibm.com/support/fixcentral/swg/downloadFixes?parent=ibm%2FTivoli&product=ibm/Tivoli/IBM+Tivoli+Monitoring&release=All&platform=All&function=fixId&fixids=6.3.0-TIV-ITM_ABLDR-IF0001&includeRequisites=1&includeSupersedes=0&downloadMethod=http>

# create agent

1. define the agent in the agent builder
    agent information
    data source
    runtime configuration
2. Test the agent
3. Add ITM queries, workspaces, situations, and take actions.
4. create and install production agent.

# create agent for ITM

1. use agent builder's agent generator to install process.

2. use MTEMS to starting and configuring agent.

    METEMS -> your agent -> configure useing defaults -> start

3. use TEP client to create workspaces, queries, situations, and take actions for agent.

# Monitoring windows resources

1. Windows Management Instrumentation(WMI)

2. Windows Performance Monitor(Perfmon)

3. Common Information Model(CIM)

4. Windows Event Log

# Monitoring process and command return codes

# Monitoring custom data sources

# Monitoring remote and optional resources
