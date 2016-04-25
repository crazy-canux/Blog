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

    C:\Program Files(x86)\IBM\AgentBuilder\agentbuilder.exe

aix/linux:

    /opt/ibm/AgentBuilder/agentbuilder

# create agent

1. define the agent in the agent builder
    - agent information
    - data source
    - runtime configuration
2. Test the agent
3. Add ITM queries, workspaces, situations, and take actions.
4. create and install production agent.

# create agent for ITM

## install

1. use agent builder's agent generator to install process.
2. use MTEMS to starting and configuring agent.
    METEMS -> your agent -> configure useing defaults -> start
3. use TEP to create workspaces, queries, situations, and take actions for agent.

# uninstall

1. uninstall
    windows: {agent_home}/TMAITM6 kxx_uninstall.vbs {{agent_home}/}
    aix/linux: {agent_home}/bin/uninstall.sh [-f] [-i] [-h {agnet_home}]
    [product_platformCode]
2. remove from TEP:
    clear off-line entry

# 
