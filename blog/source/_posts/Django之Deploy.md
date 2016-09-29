---
layout: post
title: Django之Deploy
comments: true
date: 2016-09-27 10:23:22
updated:
tags:
- django
- apache
- nginx
categories:
- Web
- Django
permalink:
---

# 发布django项目

django内置一个轻量级web开发服务器。

如果要发布django项目需要另外的操作。

WSGI: web server gateway interface

WSGI是python web服务器和应用的标准，PEP3333.

django默认会生成wsgi.py文件。

wsgi.py -> settings.py -> urls.py -> application

***

# apache2 + mod_wsgi

<https://github.com/GrahamDumpleton/mod_wsgi>


先安装apache2：

    sudo aptitude install apache2

两种方式安装mod_wsgi:

1. 作为apache2的模块安装

        sudo aptitude install libapache2-mod-wsgi

2. 作为python的包安装

        pip install mod_wsgi-httpd
        pip install mod_wsgi

创建网站的配置文件/etc/apache2/sites-available/mysite.conf:

    <VirtualHost *:80>
        ServerName www.yourdomain.com
        ServerAlias otherdomain.com
        ServerAdmin youremail

        Alias /media/ /home/user/mysite/media/
        Alias /static/ /home/user/mysite/static/

        <Directory /home/user/mysite/media>
            Required all granted
        </Directory>

        <Directory /home/user/mysite/static>
            Required all granted
        </Directory>

        WSGIScriptAlias / /home/user/mysite/mysite/wsgi.py
        WSGIPythonPath /home/user/mysite

        <Directory /home/user/mysite/mysite>
        <Files wsgi.py>
            Required all granted
        </Files>
        </Directory>
    </VirtualHost>

修改项目的wsgi.py:

因为环境变量是进程范围的，在同一个进程运行多个站点会出问题，所以推荐多站点使用mod_wsgi的守护进程模式,也可以在单进程中覆盖DJANGO_SETTINGS_MODULE这个变量。

    import os

    from django.core.wsgi import get_wsgi_application

    # Add project dir to sys.path
    from os.path import dirname, abspath
    PROJECT_DIR = dirname(dirname(abspath(__file__)))
    import sys
    sys.path.insert(0, PROJECT_DIR)

    # If you have more than 1 django project you need to change this
    # os.environ.setdefault("DJANGO_SETTINGS_MODULE", "mysite.settings")
    os.environ["DIANGO_SETTINGS_MODULE"] = "{{ mysite }}.settings"
    application = get_wsgi_application()

修改项目的settings.py:

ROOT表示存放位置，URL表示对应网址。

注意为这些目录设置权限。

    # Static files (CSS, JavaScript, Images)
    STATIC_URL = '/static/'

    STATIC_ROOT = os.path.join(BASE_DIR, 'static')

    # Media files (upload files)
    MEDIA_URL = '/media/'

    MEDIA_ROOT = os.path.join(BASE_DIR, 'media')

测试静态文件：

    $python manage.py collectstatic

激活网站：

    $sudo a2ensite mysite
    $service apache2 reload

***

# Gunicon

<https://github.com/benoitc/gunicorn>

纯python写的WSGI服务器。

安装：

    pip install gunicorn

在manage.py目录测试：

    gunicorn mysite.wsgi

***

# uWSGI

<https://github.com/unbit/uwsgi>

安装：

    pip install uwsgi

测试：

    uwsgi --http :8000 --chdir /path/to/project --module mysite.wsgi
