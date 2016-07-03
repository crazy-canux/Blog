---
layout: post
title: Shell
comments: true
date: 2016-04-01 20:42:59
updated:
tags:
- Shell
- Bash
categories:
- Linux
- Shell
permalink:
---

# Shell

Linux的shell有很多种,大多数linux发行版的默认登录shell是BASH。

查看当前使用的shell：

    echo $SHELL
    echo $0

查看安装了哪些shell：

    cat /etc/shells

常用的shell：
1. bash
2. zsh
3. fish

# Shell命令

shell命令分为内置命令和外部命令.

查看一个命令是内置命令还是外部命令：

    type [command]

提示"[command] is a shell builtin"就表示是内置命令，否则就是外部命令。

# shell脚本

