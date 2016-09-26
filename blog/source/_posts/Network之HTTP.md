---
layout: post
title: Network之HTTP
comments: true
date: 2016-09-13 01:39:34
updated:
tags:
categories:
permalink:
---

# http/https

http port: 80

https port: 443

# Python处理协议的第三方库

## httplib2

<https://github.com/httplib2/httplib2>

    pip install httplib2

## urllib3

<https://github.com/shazow/urllib3>

    pip install urllib3

## requests

<https://github.com/kennethreitz/requests>

从http/https获取内容,内置urllib3。

    pip install requests

    import requests

    get(url, params=None, **kwargs) # 返回一个Response类型的对象
    r = requests.get('http://www.goole.com')
    # Method:
    r.close()
    r.iter_content(chunk_size=1, decode_unicode=False)
    r.iter_lines(chunk_size=512, decode_unicode=None, delimiter=None)
    r.json(**kwargs)
    r.raise_for_status()
    # Data:
    r.apparent_encoding
    r.content # 响应内容的bytes形式
    r.text # 响应内容的unicode形式
    r.is_permanent_redirect
    r.is_redirect
    r.links
    r.ok
    r.status_code
    r.headers
    r.url
    r.history
    # other data
    r.encoding # 查看或设置编码
    r.raw
    r.cookies

# Python处理数据的第三方库

## bs4

<https://www.crummy.com/software/BeautifulSoup/>

从XML和HTML文件中提取数据

使用BeautifulSoup处理后文档都是unicode格式，输出都是utf-8格式。

安装bs4:

    $sudo apt-get install Python-bs4
    $pip install beautifulsoup4

安装解析器：

* python标准库的html解析器是HTMLParser（python3中改名为html.parser)
* lxml解析html
* lxml-xml解析xml
* html5lib解析html5

使用bs4和解析器，一般用lxml：

    from bs4 import BeautifulSoup

    # BeautifulSoup
    BeautifulSoup(markup='', features=None, builder=None, parse_only=None, from_encoding=None, exclude_encodings=None, **kwargs)
    soup = BeautifulSoup(r.text, 'lxml') # 返回BeautifulSoup类型对象, 默认html格式
    soup = BeautifulSoup(r.text, "xml") # xml格式
    soup = BeautifulSoup(r.text, ["lxml-xml"]) # 同上
    soup = BeautifulSoup(r.text, "html5lib") # html5格式
    # BeautifulSoup 解析出的python对象有四类： Tag, NavigableString, BeautifulSoup, Comment
    prettify(self, encoding=None, formatter='minimal')
    print(soup.prettify()) # 格式化后以unicode编码输出
    get_text(self, separator=u'', strip=False, types=(<class 'bs4.element.NavigableString'>, <class 'bs4.element.CData'>))
    soup.get_text() # 获取tag中所有内容，以unicode字符串返回
    find(self, name=None, attrs={}, recursive=True, text=None, **kwargs) # 搜索当前节点和子孙节点，查找第一个,返回一个Tag对象
    find_all(self, name=None, attrs={}, recursive=True, text=None, limit=None, **kwargs) # 搜索当前节点和子孙节点，查找所有的, 返回Tag对象的列表
    find_parent(self, name=None, attrs={}, **kwargs) # 搜索当前节点的父辈节点
    find_parents(self, name=None, attrs={}, limit=None, **kwargs) # 搜索当前节点的父辈节点
    find_next_sibling(self, name=None, attrs={}, text=None, **kwargs) # 往后搜索当前节点兄弟节点
    find_previous_sibling(self, name=None, attrs={}, text=None, **kwargs) # 往前搜索当前节点的兄弟节点
    ...

    # Tag
    tag = soup.<tag-name> # 返回一个Tag类型对象
    tag = soup.<tag-name>.<tag-name>...
    tag.name # tag名字
    tag.attrs # tag类型有很多属性,字典类型
    tag.contents # 将tag子节点以列表方式输出
    tag.children
    tag.parent
    tag.next_sibling # 返回下一个兄弟节点
    tag.previous_sibling # 返回上一个兄弟节点
    tag.next_element # 返回下一个字符串或tag
    tag.previous_element # 返回上一个字符串或tag
    ...

    # NavigableString
    ns = tag.string # 返回一个NavigableString类型对象
    unicode(ns) # 转换成unicode
    ns.replace_with(self, replace_with) # 修改内容
    ...

    # Comment, 一个特殊的NavigableString对象,只针对有注释的Tag
    comment = soup.<tag-with-comment>.string # 返回Comment类型对象

## lxml

<https://github.com/lxml/lxml>

XML和HTML的解析器

## html5lib

<https://github.com/html5lib/html5lib-python>

HTML解析器

***

# Java
