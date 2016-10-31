---
layout: post
title: Network之FTP
comments: true
date: 2016-07-28 16:08:54
updated:
tags:
- vsftp
categories:
- Network
permalink:
---

# vsftpd

<https://security.appspot.com/vsftpd.html>

    sudo apt-get install vsftpd

ftp的网页浏览格式：

ftp://host/path
ftp://username:password@host/path

windows开启ftp服务即可。

# python

## ftplib

python标准库ftplib

ftplib模块用来编写ftp客户端程序：

    from ftplib import FTP

    ftp = FTP(self, host='', user='', passwd='', acct='', timeout=<object>)
    connect(self, host='', port=0, timeout=-999)    连接到主机
    login(self, user='', passwd='', acct='')    登录
    acct(self, password)
    cwd(self, dirname)    更改工作路径
    dir(self, *args)    列出路径（文件也会输出）, 类似于LIST
    nlst(self, *args)   列出给定路径的文件（目录也会输出）， 类似于NLST
    pwd(self) 返回当前工作路径
    size(self, filename) 获取文件大小
    delete(self, filename)
    getline(self)
    getmultiline(self)
    getresp(self)
    getwelcome(self)
    makepasv(self)
    makeport(self)
    mkd(self, dirname)
    ntransfercmd(self, cmd, rest=None)
    putcmd(self, line)
    putline(self, line)
    rename(self, fromname, toname)

    retrbinary(self, cmd, callback, blocksize=8192, rest=None)
    # cmd: a RETR command, like "RETR filename"

    retrlines(self, cmd, callback=None)
    # cmd: a RETR, LIST, NLST, or MLSD command.

    rmd(self, dirname)
    sanitize(self, s)
    sendcmd(self, cmd)
    sendeprt(self, host, port)
    sendport(self, host, port)
    set_debuglevel(self, level)
    set_pasv(self, val)

    storbinary(self, cmd, fp, blocksize=8192, callback=None, rest=None)
    # 二进制上传文件

    storlines(self, cmd, fp, callback=None)
    # 文本上传文件

    transfercmd(self, cmd, rest=None)
    voidcmd(self, cmd)
    voidresp(self)
    close(self)    关闭连接
    quit(self) 退出并关闭连接

    # get the directory and file
    data = []
    ftp.dir(path, data.append)

# java
