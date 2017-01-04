---
layout: post
title: DjangoCMS
comments: true
date: 2016-12-28 00:15:47
updated:
tags:
categories:
- Python
- Django-CMS
permalink:
---

# django-cms

<https://github.com/divio/django-cms>

python基于django的CMS/Blog框架.

# 安装

初始化虚拟环境:

    $cd hydra
    $virtualenv venv
    $source venv/bin/activate

独立项目:

    $pip install djangocms-installer
    $djangocms -f -p . hydra

集成到django项目:

    $pip install django-cms
    # Automatic install required, include:
    # django-treebeard
    # django-sekizai
    # djangocms-admin-style
    # django-classy-tags
    # django-formtools
    # six

    # Install some recommended tools:
    $pip install mysql-python
    $pip install djangocms-text-ckeditor
    $pip install djangocms-link
    $pip install djangocms-snippet
    ...

    # Install file and image handing packages.
    $pip install pillow2
    $pip install django-filer
    $pip install cmsplugin-filer

#




