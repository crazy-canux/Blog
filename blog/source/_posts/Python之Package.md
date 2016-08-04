---
layout: post
title: Python之Package
comments: true
date: 2016-06-22 05:17:19
updated:
tags:
- python
categories:
- Python
permalink:
---

# ensurepip/pip

内置模块,提供使用pip从pypi安装模块。

# distutils

内置的模块。处理简单的包安装。

# distutils2

distutils的升级版，已经废弃。

# distlib

取代distutils和distutils2.

安装distlib：

    sudo pip install distlib

<https://bitbucket.org/pypa/distlib>

使用distlib：

    import distlib

# distribute

已经并入setuptools。

# setuptools

setuotppls是第三方模块, 高级包管理工具，需要安装：

最新的setuptools是合并了原来的setuptools和distribute。

自动处理依赖，egg分发格式，包含了easy_install 来安装egg格式的包。

    sudo apt-get install python-setuptools

使用setuptools：

    from setuptools import setup, find_packages
