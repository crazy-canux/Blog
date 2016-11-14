---
layout: post
title: PowerShell之WMI
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

# WMI

    Get-WmiObject
    Remove-WmiObject
    Invoke-WmiMethod
    Register-WmiEvent
    Set-WmiInstance

    # 用powershell跑一个wql。
    Get-WmiObject -Query "select * from win32_service where name='winRM'" | Format-List -Property Name,status

# CIM

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
