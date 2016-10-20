---
layout: post
title: Html
comments: true
date: 2016-06-23 09:40:39
updated:
tags:
- web
- html
categories:
- Web
- Html
permalink:
---

# HTML

HTML是超文本标记语言

# XHTML

XHTML是更严谨的更纯净的HTML

# HTML5

HTML5是下一代HTML

# html元素和属性

html元素指从开始标签到结束标签的所有代码,包括元素内容：

html元素可以嵌套。

    <p> This is paragrph </p>
    <p></p> # 空内容的元素
    <br /> # 空元素，在开始标签中关闭

html标签可以拥有属性，属性总是以name='value'的形式出现，属性总是在html元素的开始标签中规定。

    <a href="http://www.test.com">This is a link</a>

html属性和值大小写不敏感，推荐使用小写,始终给属性值加引号。

# html标题

    # 文档类型
    <!DOCTYPE html>

## <!-- -->

    # 注释, 浏览器会忽略注释,支持标准属性和事件属性
    <!-- This is a comment -->

## <html>

    # html文档,支持全局属性
    <html>
    ...
    </html>

    # mainfest属性，定义一个url，描述文档缓存信息

    # xmlns属性，定义XML的namespace属性

## <head>

可以在head标签中使用的标签：

base, link, meta, script, style, title.

    # html文档的头部, head支持全局属性
    <head>
    ...
    </head>

    # profile属性

## <body>

    # html文档的主体, body标签支持全局属性和事件属性
    <body>
    ...
    </body>

## <h1> - <h6>

    # 标题,浏览器会自动在标题前后添加空行,支持标准属性和事件属性。
    <h1>This is the max heading</h1>
    ...
    <h6>This is the min heading</h6>

## <hr />

    # 水平线分割线，支持全局属性和事件属性
    <hr />

# html段落

## <p>

    # 段落, 浏览器会自动在段落前后添加空行,支持全局属性和事件属性
    <p>This is a paragraph</p>

## <br />

    # 空行, 支持全局属性和事件属性
    <br />

    # clear属性

# 链接和图像

## <a>

支持全局属性和事件属性

    # href属性定义指向另一个文档的链接
    <a href="http://www.test.com">Click me as link</a>

    # target属性，定义被链接的文档在何处显示, blank在新窗口显示,rect, circle, poly
    <a href="http://www.test.com" target="_blank">Link</a>

    # name属性定义文档内的书签
    <a href="http://www.test.com" name="label">Link</a>

    # hreflang

    # rel

    # download

    # media

    # type

## <img>

支持全局属性和事件属性

    # src属性定义源
    <img src="url" />

    # alt属性，当图像不能显示，就显示alt的默认值。
    <img src="http://www.test.com/images/test.img" alt="default value"/>

    # height

    # ismap

    # longdesc

    # usemap

    # width

## <map>

支持全局属性和事件属性

    # id属性为map定义唯一的名称
    <map id="planetmap">
    ...
    </map>

    # name属性为image-map规定的名称

## <area>

# html样式

内联样式,style样式属性可以包含任何的css属性。

    <h1 style="font-family:verdana">A heading</h1>
    <p style="font-family:arial;color:red;font-size:20px">A paragraph</p>

## <style>

内部样式表

    <style> 定义样式定义
    <head>
    <style type="text/css">
    h1 {color: red}
    p {color: blue}
    </style>
    </head>

## <link>

外部样式表

    <link> 定义资源引用
    <head>
    <link rel="stylesheet" type="text/css" href="mystyle.css">
    </head>

## <div>

    <div> 定义文档中的块

## <span>

    <span> 定义文档中的行内的块

# html格式化

文本格式化标签：

    <b> 定义粗体文本
    <big> 定义大号字
    <em> 定义着重文字
    <i> 定义斜体字
    <small> 定义小号字
    <strong> 定义加重语气
    <sub> 定义下标字
    <sup> 定义上标字
    <ins> 定义插入字
    <del> 定义删除字

计算机输出标签：

    <code> 定义计算机代码
    <kbd> 定义键盘码
    <samp> 定义计算机代码样本
    <tt> 定义打字机代码
    <var> 定义变量
    <pre> 定义预格式文本

引用和术语标签：

    <abbr> 定义缩写
    <p><abbr title="Hyper Text Markup Language">HTML</abbr>is perfect.</p>

    <acronym> 定义首字母缩写
    <address> 定义地址
    <bdo> 定义文字方向
    <blockquote> 定义长的引用
    <q> 定义短的引用
    <cite> 定义著作的标题
    <dfn> 定义一个项目或缩写

# 表格

# 列表

