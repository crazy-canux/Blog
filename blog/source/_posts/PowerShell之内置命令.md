---
layout: post
title: PowerShell之内置命令
comments: true
date: 2016-05-24 10:44:44
updated:
tags:
- powershell
- windows
categories:
- Windows
- PowerShell
permalink:
---

# Get-Help和Help:

get-help查看帮助信息,help分页查看帮助信息，man是help的别名

命令说明：

    Get-Help
    Help

查看所有命令和概念：

    Get-Help *
    Help *

模糊查找命令和概念：

    Get-Help *<name>*
    Help *<name>*

查看具体命令帮助：

    Get-Help {<CmdletName> | <TopicName>}
    Help {<CmdletName> | <TopicName>}
    <CmdletName> -?

get-help/help的选项:

    get-help get-help
    -examples # 查看示例
    -full # 查看所有帮助
    -parameter # 查看选项的帮助
    -detailed
    -showwindow
    -online

# helpfile

3.0/4.0 需要先下载帮助手册：

    update-help

查看helpfile：

    Get-Help/Help about_*
    Get-Help/Help about_<name>

# cmdlets:

powershell的内置命令

    Get-Command -CommandType cmdlet # 查看所有cmdlet命令
    Get-Command
    Get-Service
    Get-Process
    Get-Host
    Get-Date
    Get-Eventlog
    Get-Random
    Get-Hotfix
    Get-Member
    Out-File    # 重定向，也可以用>, >>
    Out-Host
    Out-Printer
    Out-Default
    Out-String
    Out-Null
    Out-GridView
    Start-Transcript
    Stop-Transcript
    Invoke-Command
    ...

# function

# alias

    Get-Alias # 查看所有alias
    Set-Alias
    New-Alias

    ForEach-Object    %/foreach
    Where-Object    ?/where
    Add-Content    ac
    Add-PSSnapin    asnp
    Get-Content    cat
    Set-Location    cd/chdir
    Clear-Content    clc
    Clear-Host    clear/cls
    Clear-History    clhy
    Clear-Item    cli
    Clear-ItemProperty    clp
    Clear-Variable    clv
    Connect-PSSession    cnsn
    Compare-Object    compare/diff
    Copy-Item    copy/cp/cpi
    Copy-ItemProperty    cpp
    Invoke-WebRequest    curl
    Convert-Path    cvpa
    Disable-PSBreakpoint    dbp
    Remove-Item    del/erase
    Get-ChildItem    dir
    Disconnect-PSSession    dnsn
    Enable-PSBreakpoint    ebp
    Write-Output    echo
    Export-Alias    epal
    Export-Csv    epcsv
    Export-PSSession    epsn
    Enter-PSSession    etsn
    Exit-PSSession    exsn
    Format-Custom    fc
    Format-List    fl
    Format-Table    ft
    Format-Wide    fw
    Get-Alis    gal
    Get-PSBreakpoint    gbp
    Get-Content    gc
    Get-ChildItem    gci
    Get-Command    gcm
    Get-PSCallStack    gcs
    Get-PSDrive    gdr
    Get-History    ghy
    Get-Item    gi
    Get-Job    gjb
    Get-Location    gl
    Get-Member    gm
    Get-Module    gmo
    ...
    help    man
    mkdir    md
    ...

## object

object主要通过管道|使用。

object相关的cmdlet：

    Compare-Object
    ForEach-Object
    Get-Wmiobject
    Group-Object
    Measure-Object
    New-Object
    Register-ObjectEvent
    Remove-WmiObject
    Select-Object
    Sort-Object
    Tee-Object
    Where-Object

object转化：

    get-command -verb *convert*
    ...

导出object：

    get-command -verb *export*
    ...

导入object：

    get-command -verb *import*
    ...

# provider

    Get-PSProvider # 查看provider
    Get-PSDrive    # 查看驱动器
    New-PSDrive    # 新建驱动器
    Remove-PSDrive    # 删除驱动器

    Alias
    Environment
    FileSystem
    Function
    Registry
    Variable

    help/get-help <provider_name>    # 查看provider帮助
    help Alias

    cd <drive_name>:    # 进入到某个provider的驱动器
    cd/chdir Alias:

# module

    Get-Module
    get-module -listavailable # 查找安装的模块
    Import-Module
    import-module sqlps # 导入mssql模块
    get-command -module sqlps # 查看模块中所有命令
    New-Module
    Remove-Module

# format

安装路径有一些xml文件已经做了一些默认的格式化。

格式化的数据只能传给Out-File/out-host/out-printer/out-null/out-string/out-default.

    Export-FormatData
    Get-FormatData
    Update-FormatData
    Format-Custom
    Format-List
    Format-Table
    Format-Wide
