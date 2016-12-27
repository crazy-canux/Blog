---
layout: post
title: Django之URL
comments: true
date: 2016-10-04 04:20:39
updated:
tags:
categories:
- Python
- Django
permalink:
---

# urls.py

    from django.conf.urls import url

django请求站点的方法：
1. ROOT_URLCONF，在settings.py中设置。
2. 寻找urlpatterns，它是django.conf.urls.url()实例的一个python列表。
3. dnango依次匹配每个URL模式，在第一个匹配停下。
4. 一旦一个正则表达式匹配，django就调用对应的视图，视图获得HttpRequest实例,如果是没有命名的组返回内容作为位置参数，如果是命名的组返回内容作为关键字参数。
5. 如果没有匹配到或者过程跑出异常，django调用合适的错误处理。

将应用的视图映射到URL：

需要在应用目录新建urls.py文件,然后在项目的url中包含应用的url。

urlpatterns是url()实例类型的python列表。

    from . import views

    urlpatterns = [
        # views内的内容不要引号。
        url(r'^$', views.index, name='index'),
        # 基于类的视图
        url(r'^$', views.IndexView.as_view(), name='index'),
        ...,
    ]

没有命名的组：

视图函数只有request参数，匹配的正则表达式作为位置参数。

    url(r'^pattern1/pattern2/$', views.index, name='index'),

    def index(request):
        ...

命名组：

视图函数除了request参数还有关键字参数，匹配的命名表达式组作为关键字参数,覆盖默认的关键字参数。

使用命名的正则表达式组： (?P<name>pattern)

name就是关键字参数。

    url(r'^pattern1/(?P<name>pattern)/pattern2/$), views.index, name='index),

    def index(request, name):
        ...

错误处理：

django会调用一个错误处理视图处理异常。
1. handler404 页面没找到
2. handler500 服务器错误
3. handler403 权限被拒绝
4. handler400 无效的请求

你也可以在项目的urls.py中重新定义这些默认视图：

    handler404 = 'mysite.views.your_custom_page_not_found_view'
    handler500 = 'mysite.views.your_custom_error_view'
    handler403 = 'mysite.views.your_custom_permission_denied_view'
    handler400 = 'mysite.views.your_custom_bad_request_view'

