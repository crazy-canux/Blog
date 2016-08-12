---
layout: post
title: reStructuredText
comments: true
date: 2016-08-08 13:39:38
updated:
tags:
- reST
categories:
- Web
permalink:
---

# reStructuredText

<http://docutils.sourceforge.net/rst.html>

reST是易读所见即所得的文本标记语言，格式类似markdown。

主标题：

    Title
    =====

副标题：

    Subtitle
    -----

下划线或者上下划线：

    =====
    Title
    =====

    --------
    Subtitle
    --------

三个以上的-表示分割线：

    ----

参考式链接：

    `hyperlink`_

    .. _hyperlink: http://hyperlink.org

行内式链接：

    `link <https://link.com>`_

图片：

    .. image:: https://path/image.png
        :alt: HTTPie compared to cURL
        :width: 679
        :heigh: 781
        :align: center

四个空格表示代码块：

    source code

        print("source")
        return 0
