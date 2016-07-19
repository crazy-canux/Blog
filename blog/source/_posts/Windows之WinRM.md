---
layout: post
title: Windows之WinRM
comments: true
date: 2016-07-17 08:36:36
updated:
tags:
- winrm
categories:
- Windows
permalink:
---

# WinRM

Windows Remote Management

# python

    import winrm
    s = winrm.Session('host', auth=('user', 'password'))
    r = s.run_cmd('cmd')
    r = s.run_ps('ps')
    return_code = r.status_code
    output = r.std_out
    error = r.std_err
