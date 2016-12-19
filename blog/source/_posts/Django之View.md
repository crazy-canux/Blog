---
layout: post
title: Django之View&URL
comments: true
date: 2016-10-04 04:20:39
updated:
tags:
categories:
permalink:
---

# views.py

    from django.shortcuts import render

定义自己的视图函数：

    from django.http import HttpResponse
    from django.template import RequestContext, loader

    # 导入模板中的类
    from .models import Question

    def index(request):
        ...
        t = loader.get_template('application/index.html')
        c = RequestContext(request, {'foo': 'bar'})
        return HttpResponse(t.render(c), content_type="text/html")

当请求一个页面时django会建立一个包含请求元数据的HttpRequest对象，当django加载对应视图时，这个对象作为视图第一个参数。

每个视图会返回一个HttpResponse对象。

每个视图函数都用HttpRequest对象（通常用request）作为第一个参数。

每个视图函数都返回一个HttpResponse对象，包含生成的响应。

HttpRquest和HttpResponse在django.http包中，参考：

<http://python.usyiyi.cn/documents/django_182/ref/request-response.html>

HttpRequest对象属性：

    request.scheme # http/https
    request.body
    request.path
    request.path_info
    request.method # GET/POST
    request.encoding
    request.user
    request.session
    request.urlconf
    request.GET
    request.POST
    request.REQUEST
    request.COOKIES
    request.FILES
    request.META

HttpRequest对象方法：

    request.get_host()
    ...

HttpResponse对象属性：

    response.content
    response.charset
    response.status_code
    response.reason_phrase
    response.streaming
    response.closed

HttpResponse对象的方法：

    response.getvalue()
    ...

返回错误：

HttpResponse的子类提供了对不同类型HTTP响应。

    from django.http import HttpResponseBadRequest, HttpResponseNotFound, HttpResponseForbidden, HttpResponseServerError,
    return HttpResponseNotFound("<h1>Page not found</h1>")

http404异常：

在应用的模板目录顶层定义一个404.html模板文件，当跑出Http404异常就会调用这个模板文件展示。

    from django.http import Http404

    def index(request):
        try:
            ...
        except Application.DoesNotExist:
            raise Http404("Application does not exist")
        return HttpResponse(...)

自定义错误视图：

参考urls中的内容。

# 快捷函数

django.shortcuts中定义了多个快捷函数。

    from django.shortcuts import render
    render(request, template_name, context=None, context_instance=<object object>, content_type=None, status=None, current_app=<object object>, dirs=<object object>, dictionary=<object object>, using=None)
    # render第一个参数是request，根据给定模板和上下文字典，返回一个渲染后的HttpResponse对象。
    return render(request, 'application/index.html', {'foo': 'bar'}, content_type="text/html")

    from django.shortcuts import get_object_or_404
    get_object_or_404(klass, *args, **kwargs)
    # 在给定的模型管理器调用get()，如果不存在引发Http404异常。

# 基于类的视图

基于类的视图的基类在django.views.generic中

    from django.views.generic import View
    def MyView(View):
        def get(self, request):
            return HttpResponse(...)

# TemplateResponse和SimpleTemplateResponse

    from django.template.response import TemplateResponse, SimpleTemplateResponse

# 视图装饰器

django.views.decorators包中定义了视图的装饰器。

    from django.views.decorators import *

# 内建的视图

django.views.static.serve定义了开发环境的文件服务器视图，仅用于开发。

    from django.views.static import serve

django.views.defaults定义了内建的错误处理的视图

    from django.views.defaults import *

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

