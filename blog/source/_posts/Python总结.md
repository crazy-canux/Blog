---
layout: post
title: Python总结
comments: true
date: 2016-06-21 21:18:20
updated:
tags:
- python
categories:
- Python
permalink:
---

# python项目结构

|-- AUTHORS
|-- LICENSE
|-- README.md
|-- devops     项目源代码目录
|   |-- tests  测试程序目录
|-- bin        用来存放将被setup.py安装的二进制脚本
|-- data       用来存放其它类型文件
|-- docs       用来存放文档
|-- etc        用来存放配置文件
|-- tools      用来存放与工具相关shell脚本
|-- setup.py   标准安装脚本
|-- requirementstxt 包含所需以来包
|-- test-requirements.txt 包含测试所需以来包

# python的可用接口

1. python内置函数

c/c++实现的，不需要导入就可以使用的。

2. python标准库

python实现的，需要导入才能使用的。

3. python外部库

需要安装和导入才能使用的。

外部库是对python代码的补充。

4. python框架

需要安装和导入才能使用的。

python代码是对外部库的补充。

# 函数式编程

* 列表解析

    使用中括号，列表解释返回一个列表。

        [expression for item in iterable if condition]

* 生成器表达式

    使用小括号,生成器表达式返回一个生成器。

        (expression for item1 in iterable1 if condition1
                    for item2 in iterable2 if condition2
                    ...)

* 生成器与yield

任何使用yield的函数都称为生成器。

* 协程与yield

* 装饰器

@decorator

* 匿名函数和lambda

* global

# 控制流

* with as上下文管理器

# 异常

* assert断言

# 类与面向对象
