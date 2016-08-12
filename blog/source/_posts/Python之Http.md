---
layout: post
title: Python之Http
comments: true
date: 2016-08-12 14:25:10
updated:
tags:
categories:
- Python
permalink:
---

# xml库

## xmlrpclib

## SimpleXMLRPCServer

## DocXMLRPCServer

# url库

URL: Uniform Resource Locator

URI: Universal Resource Identifier

> prot_sch://net_loc/path;params?query#frag
> prot_sch: http/https/ftp/file
> net_loc: username:password@host:port
> path: /path/to/path
> params: options arguments
> query: connector&key-value
> frag:

python2的url标准库：
1. urlparse
2. urllib
3. urllib2

python3的url标准库：
1. urllib

## urllib

## urllib2

## urlparse

## urllib3

<https://github.com/shazow/urllib3>

    pip install urllib3

    import urllib3

# http库

python2的http标准库
1. httplib for client
2. BaseHTTPServer, CGIHTTPServer, SimpleHTTPServer, cookielib, Cookie for server

python3的标准库
1. http

## httplib

## BaseHTTPServer

## CGIHTTPServer

## SimpleHTTPServer

## cookielib

## Cookie

## requests

<https://github.com/kennethreitz/requests>

    pip install requests

    import requests

## bs4

<https://www.crummy.com/software/BeautifulSoup/>

    pip install beautifulsoup4

    from bs4 import BeautifulSoup
