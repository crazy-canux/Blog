---
layout: post
title: Django
comments: true
date: 2016-09-20 23:14:07
updated:
tags:
- python
- django
categories:
- Web
- Django
permalink:
---

# django

<https://github.com/django/django>

<https://www.djangoproject.com/>

安装：

    $pip install diango==1.8.2
    $sudo apt-get install python-django

验证安装：

    $python
    >>>import django
    >>>django.VERSION
    >>>django.get_version()

django的1.8和1.11是长期支持版。

从1.7开始支持python3。

django采用MTV框架。

M: model,数据存取

T: template，如何展现数据

V: view，展现哪些数据

***

# project

创建一个名为mysite的项目

    django-admin startproject mysite

    mysite
    |-- manage.py
    |-- mysite
        |- __init__.py
        |- settings.py
        |- urls.py
        |- wsgi.py

> mysite/: 外层目录，可随意重命名

> manage.py: 一个实用的命令行工具，可以让你已各种方式和django交互。

> mysite/mysite/: 内层目录，python包,通过它导入其它类

> init.py: 一个空文件。

> settings.py: django项目的配置。

> urls.py: django项目的URL声明。

> wsgi.py: 一个WSGI兼容的web服务器入口。

验证开发服务器：

    python manage.py runserver

浏览器输入：

    http://127.0.0.1:8000

也可以指定别的ip和port：

    python manage.py runserver 0.0.0.0:8080

## settings.py

默认使用sqlite3数据库：

    DATABASES = {
        'DEFAULT': {
            'ENGINE':'django.db.backends.sqlite3',
            'NAME':os.path.join(BASE_DIR,'db.sqlite3'),
        }
    }

手动配置：

    ENGINE:
        django.db.backends.mysql
        django.db.backends.oracle
        django.db.badkends.postgresql_psycopg2

    NAME:
        your database name

    USER:
        your database username

    PASSWORD:
        your database password

    HOST:
        local database or remote database

    PORT:
        database port

django包含下列默认应用:

    INSTALLED_APPS = {
        'django.contrib.admin',
        'django.contrib.auth',
        'django.contrib.contenttypes',
        'django.contrib.sessions',
        'django.contrib.messages',
        'django.contrib.staticfiles',
        # 在下面注册你的所有应用,django会自动查找应用的templates和static目录中的文件。
        'register your application here',
    }

> admin: 管理站点

> auth: 认证系统

> contenttypes: 用于内容类型的框架

> sessions: 会话框架

> messages: 消息框架

> staticfiles: 管理静态文件的框架

在数据库中创建默认application的表：

    $python manage.py migrate

## urls.py

    from django.conf.urls import include, url
    from django.contrib import admin

    urlpatterns = [
        # 默认的项目的admin的url
        url(r'^admin/', include(admin.site.urls)),
        # 在项目URL添加链接到应用URL：
        # 在下面添加你的所有应用的url
        url(r'^polls/', include('polls.urls', namespace='polls')),
        ...,
    ]

在项目的urls添加所有应用的urls，为每个应用独立创建urls，方便管理。

项目的admin的url应该是: http://domain.com/admin/ ，这个默认设置

应用的主url就应该是： http://domain.com/application/ , 需要设置r'^application/'.

然后这个url链接到application.urls，需要设置include('application.urls').

***

# application

应用，一个项目可以有多个应用，一个应用可以用到多个项目中。

可以单独打包应用发布到pypi，包名格式django-project，参考python的打包方法。

创建一个名为polls的应用：

    $python manage.py startapp polls

    polls/
    |- admin.py
    |- __init__.py
    |- migrations
    |  |- __init__.py
    |- models.py
    |- tests.py
    |- views.py

## admin.py

    from django.contrib import admin

创建一个管理员用户：

    $python manage.py createsuperuser

管理员登陆界面：

    http://localhost:8080/admin/

在admin.py中注册模型，然后就可以在登陆界面管理模型了

    from .models import Question
    admin.site.register(Question)

自定义管理表单：

    from .models import Question
    class QuestionAdmin(admin.ModelAdmin):
        fileds = ['pub_date', 'question_date']
    admin.site.register(Question, QuestionAdmin)

把表单分割成字段集：

    from .models import Question
    class QuestionAdmin(admin.ModelAdmin):
        fieldsets = [
            (None,               {'fields': ['question_text']}),
            ('Date information', {'fields': ['pub_date']}),
        ]
    admin.site.register(Question, QuestionAdmin)

## models.py

    from django.db import models

创建应用的模型，定义模型对应的数据库设计及其附带的元数据。

每个模型都是django.db.models.Models的一个python子类。

每个模型(一个类）对应数据库中唯一的一张表。

模型的每个属性都表示为数据库中的一个字段。

* 在项目的settings.py中激活应用，并设置数据库相关参数。

* 让django包含你的应用：

    告诉django你对模型做了更改，并且将这些更改存储为迁移文件polls/migrations/0001_initial.py:

        $python manage.py makemigrations polls

    可以查看迁移文件执行了哪些sql语句,并不真的在数据库执行：

        $python manage.py sqlmigrate polls 0001

    可以检查项目中的模型是否存在问题：

        $python manage.py check

    在数据库中创建模型,查找还没有被应用的迁移文件然后和数据库同步：

        $python manage.py migrate

## views.py

    from django.shortcuts import render

定义自己的视图：

    from django.http import HttpResponse

    from .models import Question

    def index(request):
        latest_question_list = Question.object.order_by('-pub_date')[:5]
        output = ', '.join([p.question_text for p in latest_question_list])
        return HttpResponse(output)

在视图中使用模板：

默认django会在项目的所有应用的templates中查找模板，所以为了防止多个应用有同名的模板，需要在templates下新建application同名的目录来存放模板。

应用的模板文件需要在应用目录创建templates文件夹

默认模板放在polls/templates/polls/XXX.html

应用的静态文件需要在应用目录创建static文件夹

默认静态文件存放在polls/static/polls/XXX.css

静态文件夹用来集中存放和管理图片，js脚本和css样式表等静态文件。

    def index(request):
        ...
        return render(request, 'polls/index.html', {'name': 'value',...})

引发404错误：

    from django.shortcuts import get_object_or_404, render

    def detail(request, question_id):
        question = get_object_or_404(Question, pk=question_id)
        return render(request, 'polls/detail.html', {'question': question})

render的使用：

    render(request, template_name, context=None, context_instance=<object object>, content_type=None, status=None, current_app=<object object>, dirs=<object object>, dictionary=<object object>, using=None)
    render(request, XXX.html, {'name': value}) # value传给html中同名的变量。

## tests.py

    from django.test import TestCase

应用的测试程序一般放在tests.py文件中。

测试应用：

    $python manage.py test polls

## urls.py

应用通过url和项目链接在一起。

将应用的视图映射到URL：

需要在应用目录新建urls.py文件,然后在项目的url中包含应用的url。

    from django.conf.urls import url
    from . import views

    urlpatterns = [
        url(r'^$', views.index, name='index'),
        ...,
    ]

应用的url应该是： http://domain.com/application/ 加上你在应用的url的正则部分，这个url调用views里面的对应视图。

***

# manage.py

manage.py有下面子命令：

    [staticfiles]
        collectstatic # 设置STATIC_ROOT = '/var/www/static/project/'用来收集静态文件
        findstatic
        runserver # 启动django自带的web开发服务器

    [sessions]
        clearsessions

    [server]
        runmodwsgi #

    [auth]
        changepassword
        createsuperuser

    [django]
        check
        compilemessages
        createcachetable
        dbshell # 数据库命令行
        diffsettings
        dumpdata # 导出数据
        flush # 清空数据库
        inspectdb
        loaddata # 导入数据
        makemessages
        makemigrations # 创建迁移文件
        migrate # 执行迁移文件
        runfcgi
        shell # 项目环境终端
        showmigrations
        sql
        sqlall
        sqlclear
        sqlcustom
        sqldropindexes
        sqlflush
        sqlindexes
        sqlmigrate # 查看迁移文件会执行哪些sql
        sqlsequencereset
        squashmigrations
        startapp
        startproject
        syncdb
        test
        testserver
        validate

***

# 模板


