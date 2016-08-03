---
layout: post
title: PowerShell
comments: true
date: 2016-04-26 09:52:02
updated:
tags:
- powershell
- windows
categories:
- Windows
- PowerShell
permalink:
---

# Powershell

Console: command line interface

ISE: script editor and console combination

Version:

2.0,3.0,4.0.

C:\windows\System32\powershell 存放64位powershell

C:\windows\SysWOW64\powershell 存放32位powershell

    >$PSVersionTable
    >$HOST

Install/Update:

<https://www.microsoft.com/zh-CN/download/details.aspx?id=40855>

安装Windows Management Framework4.0即可。

    >$PSHOME

多版本时切换版本:

    >powershell -version 2

# powershell相关项目

## psget

安装powershell的模块

<https://github.com/psget/psget>

# powershell命令

    >powershell -?
    >powershell /?
    >powershell -help

# powershell script

powershell是默认大小写不敏感的。

## 注释

行注释：

    # comment

块注释/多行注释：

    <#
    comment1
    comment2
    ...
    #>

## 运算符


## 数据类型

系统变量：

    $_    # 表示管道中的当前对象

自定义变量：

    $name

hash/字典：

    @{L=<key>;
    E={$_.<value>};
    formatstring=<format>}

    @{N=<key>;E={$_.<value>}}
    @{Label=<key>;E={$_.<value>}}
    @{Name=<key>;E={$_.<value>}}

## 输入输出

## 控制流

## 函数

