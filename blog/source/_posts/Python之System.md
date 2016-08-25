---
layout: post
title: Python之System
comments: true
date: 2016-08-15 11:04:12
updated:
tags:
categories:
- Python
permalink:
---

# Python Runtime Services

## __builtin__

## __main__

## __future__

## sys

## sysconfig

## future_builtins

## warnings

## contextlib

## abc

## atexit

## traceback

## gc

## inspect

## site

## user

## fpectl

# Generic Operating System Services

## os

## time

    # 将时间2011-09-27 10:50:00转换成时间戳（从1970开始的秒数）
    time.mktime(time.strptime("2016-01-01 00:00:00", "%Y-%m-%d %H:%M:%S"))

    # 将时间戳转换成时间2011-09-27 10:50:00
    time.strftime("%Y %m %d %H %H:%M:%S", time.localtime(2016010100000000))

## io

## logging

## getopt

## argparse

## errno

## getpass

## curses

## platform

## ctypes

# Optional Operating System Services

## multiprocessing

## thread

## threading

## readline

## rlcompleter

## select

## dummy_threading

## dummy_thread

## mmap

