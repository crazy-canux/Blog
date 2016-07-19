---
layout: post
title: PowerShell之wmi和cim
comments: true
date: 2016-07-18 14:54:39
updated:
tags:
- powershell
- wmi
- cim
categories:
- Windows
- PowerShell
permalink:
---

# wmi

    Get-WmiObject
    Invoke-WmiMethod
    Register-WmiEvent
    Remove-WmiObject
    Set-WmiInstance

# cim

powershell建议使用cim。

    Get-CimClass
    Get-CimInstance
    Get-CimSession
    Get-CimAssociatedInstance
    Invoke-CimMethod
    New-CimInstance
    New-CimSession
    New-CimSessionOption
    Register-CimIndicationEvent
    Remove-CimInstance
    Remove-CimSession
    Set-CimInstance
