---
layout: post
title: Python之WeChat
comments: true
date: 2016-10-07 22:01:44
updated:
tags:
- python
- django
- wechat
categories:
- Python
permalink:
---

# python开发微信公众号

1. 注册微信公众号
2. 在微信公众平台（开发->基本配置）修改服务器配置，URL添加你的代码的URL，Token添加你代码中的Token。
3. 用git管理代码提交到URL，或者用云服务器。

微信开发文档：

<https://mp.weixin.qq.com/wiki>

    wechat user <=> send/receive message <=> wechat server <=> POST XML message <=> your server

# 新浪SAE平台部署python项目

以django项目为例。

<http://www.sinacloud.com/doc/sae/python/index.html>

添加第三方依赖：

<http://www.sinacloud.com/doc/sae/python/tools.html#tian-jia-di-san-fang-yi-lai-bao>

使用mysql：

<http://www.sinacloud.com/doc/sae/python/mysql.html#api-shi-yong-shou-ce>

## 创建一个django项目叫mysite。

SAE平台需要config.yaml和index.wsgi两个文件.

SAE的入口就是index.wsgi文件中名叫application的可调用对象。

mysite/config.yaml

添加用到的第三方库和版本号

    name: "mysite"
    version: "1.0.0.0"

    # 添加用到的第三方库和版本
    libraries:
    - name: "django"
      version: "1.8.2"

    # 这个是默认的，可以省略，在项目路径创建static目录，用collectstatic收集静态文件，在settings.py添加STATIC_ROOT。
    handlers:
    - url: /static
      static_dir: static

mysite/index.wsgi

整个项目的wsgi接口，内部调用wsgi.py中的

    import sae

    # SAE如果不支持当前版本的第三方库，可以上传自己的版本
    # 在项目目录新建site-packages目录，用pip install -t site-packages django==1.8.2安装第三方库。
    import os
    import sys
    root = os.path.dirname(__file__)
    sys.path.insert(0, os.path.join(root, "site-packages"))

    from mysite import wsgi
    application = sae.create_wsgi_app(wsgi.application)

mysite/mysite/settings.py

在SAE设置mysql，在项目添加mysql的参数。

用migrate同步本地数据库后，用mysqldump -u <username> -p <databasename> > <filename>.sql到出本地数据为sql文件。

在SAE上传sql文件把数据同步到SAE的mysql。

    DEPLOY = 'SERVER_SOFTWARE' in os.environ

    DEBUG = not DEPLOY

    # For SAE
    if DEPLOY:
        import sae.const
        MYSQL_DB = sae.const.MYSQL_DB
        MYSQL_USER = sae.const.MYSQL_USER
        MYSQL_PASS = sae.const.MYSQL_PASS
        MYSQL_HOST = sae.const.MYSQL_HOST
        MYSQL_PORT = sae.const.MYSQL_PORT
    # For Local
    else:
        MYSQL_DB = 'xfullstack'
        MYSQL_USER = 'django'
        MYSQL_PASS = '******'
        MYSQL_HOST = 'localhost'
        MYSQL_PORT = '3306'

## 创建一个应用wechat。

在mysite/mysite/settings.py中添加wechat应用。

在mysite/mysite/urls.py中添加wechat的url。

/mysite/wechat/urls.py

    from django.conf.urls import url
    from . import views
    urlpatterns = [
        url(r'^$', views.wechat),
    ]

mysite/wechat/views.py

    # 定义这三个微信的变量
    WECHAT_TOKEN = yourtoken
    WECHAT_APPID
    WECHAT_APPSECRET
    def wechat(request):
        if request.method == "GET":
            # 开发者提交信息后，微信服务器将发送GET请求到填写的服务器地址URL上
            # 1. 将token、timestamp、nonce三个参数进行字典序排序
            # 2. 将三个参数字符串拼接成一个字符串进行sha1加密
            # 3. 开发者获得加密后的字符串可与signature对比，标识该请求来源于微信
            token = WECHAT_TOKEN

            signature = request.GET.get(u'signature', None)
            timestamp = request.GET.get(u'timestamp', None)
            nonce = request.GET.get(u'nonce', None)
            echostr = request.GET.get(u'echostr', None)

            tmp_list = [token, timestamp, nonce]
            tmp_list.sort()
            sha1 = hashlib.sha1()
            map(sha1.update, tmp_list)
            hashcode = sha1.hexdigest()

            if hashcode == signature:
                return HttpResponse(echostr)
            else:
                return HttpResponse(None)
        elif request.method == "POST":
            #当普通微信用户向公众账号发消息时，微信服务器将POST消息的XML数据包到开发者填写的URL上。
            return HttpResponse(<xml-message>)

## 修改wechat的配置

    URL: http://mysite.applinzi.com/wechat/
    TOKEN: yourtoken
