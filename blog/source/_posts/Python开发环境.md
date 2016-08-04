---
layout: post
title: Python
comments: true
date: 2016-04-03 10:49:21
updated:
tags:
- Python
categories:
- Python
permalink:
---

# python

Windows安装：

    安装python到C:\Python27，添加系统环境变量path：C:\Python27\和C:\Python27\Scripts\。
    可以使用IDLE或python命令行或cmd执行python命令

Linux安装：

    $sudo apt-get install python
    $sudo yum install python

标准库的路径：

    C:\Python27\Lib
    /usr/lib/python2.7/

命令：

    $python/ipython --help     # 进入python解释器
    >>>exit()/Ctrl+d     # 退出python解释器
    >>>help()            # 进入help工具
    help>quit            # 退出help工具
    $pydoc --help        # 文档工具

IDE：

1. Windows: IDLE
2. Linux: Vim + Scripts

# python的其它解释器

## cpython

比python更快的python。

python的默认解释器，安装python即可获得。

## pypy

用python写的python解释器。

比cpython更快的python。

<http://pypy.org/>

    sudo apt-get install pypy

## ipython

python写的交互式解释器。

<https://github.com/ipython/ipython>

    sudo apt-get install ipython

## jpython

运行在java平台的python解释器。

## ironpython

运行在.net平台的python解释器。

# pyenv

python版本管理

<https://github.com/yyuu/pyenv>

# virtualenv

分离的虚拟的python环境

<https://github.com/pypa/virtualenv>

# 第三方库

<https://pypi.python.org/pypi>

第三方库路径：

    C:\Python27\Lib\site-packages
    /usr/lib/python2.7/dist-packages
    /usr/local/lib/python2.7/ dist-packages
    /usr/local/lib/python2.7/site-packages

* 二进制安装：

        sudo apt-get install python-packagename

* 源码安装第三方库：

        cd package
        python setup.py install

* easy_install(setuptools)安装：

    setuptools带的工具,需要安装第三方库setuptools。

    从egg归档格式中安装。

    <https://github.com/pypa/setuptools>

        easy_install packagename[=version] # 安装
        easy_install -U packagename[=version] # 升级

* pip安装：

    python自带的安装工具。

    升级pip：

        pip install -U pip # for linux
        python -m pip install -U pip # for windows

    可以从whell，tarball等归档格式安装。

    <https://github.com/pypa/pip>

        pip install packagename[=version] # 安装
        pip install -U packagename[=version] # 升级
        pip uninstall packagename # 卸载
        pip install XXX.whl # 安装wheel包

# python代码检查

* hacking

<https://github.com/openstack-dev/hacking>

* flake8

<https://github.com/PyCQA/flake8>

Include:
pyflakes
pep8
pep257
McCabe

* pylama

Code audit tool for python and javascript.

<https://github.com/klen/pylama>

Include:
pyflakes
pylint
pep8
pep257
mccabe
ghslint(for js)

* pep8/pycodestyle

<https://github.com/PyCQA/pycodestyle>

* pep257/pydocstyle

<https://github.com/PyCQA/pydocstyle>

* jedi

<https://github.com/davidhalter/jedi>

* mccabe

<https://github.com/PyCQA/mccabe>

* pyflakes

Faster than pylint.

<https://github.com/pyflakes/pyflakes>

* pylint

<https://github.com/PyCQA/pylint>

    sudo apt-get install pylint
    sudo yum install pylint

* rope

<https://github.com/python-rope/rope>

> a python refactoring library

    sudo apt-get install python-rope
