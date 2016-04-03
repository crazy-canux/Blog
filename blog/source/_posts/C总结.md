---
layout: post
title: C总结
comments: true
date: 2016-04-02 16:06:14
updated:
tags:
- C
- Linux
- Unix
- Windows
- POSIX
- ISO C
- ANSI C
categories:
- C
permalink:
---

# C标准

ISO C89(ANSI C89) -> ISO C99 -> ISO C11

ANSI C 和 ISO C是对通用C语言的接口的定义。

符合这种标准的实现为C语言标准库,也叫libc。

Unix/Linux的POSIX包含libc。

Linux的glibc包含libc。

Windows的msvcrt包含libc。

其它和C相关的标准：

BSD

System V

XPG

SUS

# C开发环境

## windows

这些都集成在windows的IDE VC中。

编译器： cl (.c -> .obj)

资源编译器： rc (.rc -> .res)

链接器： link (.obj -> .exe)

## Mac

集成在IDE xcode中

clang(llvm)

## Linux/Unix

### 编辑器或IDE

KDE桌面的IDE:KDevelop

GNOME桌面的IDE: Anjuta

KDE桌面的编辑器： kwrite，kate

GNOME桌面的编辑器： gedit

linux/unix通用的编辑器：vim和emacs。

### 编译器

gcc

clang

### 编译工具

make

cmake

### 调试器

gdb

### 文档工具

doxygen

### Linux的标准C库glibc：

遵循ISO C11 和 POSIX.1-2008。

还包括一些其它标准。

关于ISO C 和 POSIX参考另外两篇博文。
