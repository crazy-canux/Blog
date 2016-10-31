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

***

# shell相关项目

## bash-it

大部分发行版默认使用bash,无需额外安装。

bash的优化项目bash-it：

<https://github.com/Bash-it/bash-it>

## oh-my-zsh

安装zsh：

    sudo apt-get install zsh

zsh的优化项目oh-my-zsh:

<https://github.com/robbyrussell/oh-my-zsh>

***

# bash命令

    bash --help

***

# bash script

