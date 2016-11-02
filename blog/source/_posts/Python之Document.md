---
layout: post
title: Python之Document
comments: true
date: 2016-08-03 21:57:26
updated:
tags:
- reSt
- Sphinx
- readthedoc
categories:
- Python
permalink:
---

# Sphinx

<https://github.com/sphinx-doc/sphinx>

<https://zh-sphinx-doc.readthedocs.io/en/latest/contents.html>

Sphinx就是python处理reStructuredText格式的工具。

安装：

    pip install -U Sphinx

使用sphinx：

    $cd your-project/docs

    $sphinx-quickstart
    # 以下选项需要手动设定，其它都可以用默认值：
    > Project name: pydeveloper
    > Author name(s): Canux CHENG
    > Project version: 1.0.0.0
    > autodoc: automatically insert docstrings from modules (y/n) [n]: y

配置conf.py：

    # 包含刚才的所有配置，可以在这里手动修改。

# sphinx文档语法

<https://zh-sphinx-doc.readthedocs.io/en/latest/markup/index.html#sphinxmarkup>

根据语法创建rst格式的文档。

修改index.rst:

    # index.rst这是文档的首页。

# sphinx-build

生成web可读的文档。

简单方法生成文档：

    # 生成html格式的文档
    $make html

# sphinx-apidoc

自动生成API文档。

# ReadTheDocs

将项目文档部署到readthedocs站点。

<https://readthedocs.org/>

<http://readthedocs.readthedocs.io/zh_CN/latest/>

***

# pandoc

<https://github.com/bebraw/pypandoc>

安装：

    pip install pypandoc

