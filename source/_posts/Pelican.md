---
layout: post
title: Pelican
comments: true
date: 2016-12-24 23:37:09
updated:
tags:
categories:
- Python
- Pelican
permalink:
---

# Pelican

python开发的静态站点生成器.

<http://blog.getpelican.com/>

<https://github.com/getpelican/pelican>

<http://pelican-docs-zh-cn.readthedocs.io/en/latest/getting_started.html>

<http://pelican-zh.readthedocs.io/en/latest/zh-cn/>

# 搭建博客

创建环境:

    $mkdir blog_pelican
    $cd blog_pelican
    $virtualenv venv
    $source venv/bin/activate
    $pip install pelican
    $pip install markdown

创建pelican项目:

    $pelican-quickstart

生成下列文件和目录:

    publishconf.py
    pelicanconf.py
    fabfile.py
    develop_server.sh
    Makefile
    content
      |-
    output
      |-


