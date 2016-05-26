---
layout: post
title: Database之Mysql
comments: true
date: 2016-05-25 12:14:59
updated:
tags:
- mysql
categories:
- Database
permalink:
---

# Mysql

安装mysql服务器

    sudo apt-get install mysql-server
    sudo yum install mysql-community-server

安装mysql客户端

    sudo apt-get install mysql-client
    sudo yum install mysql-community-client

CLI工具： mysql

GUI工具： mysql workbench

需要用root用户进入mysql命令行

    mysql -u root -p
    mysql -h <mysql server> -P <port> -u root -p

# sql query

查看所有用户：

    SELECT DISTINCT(USER) FROM mysql.user;
    SELECT user,host,password FROM mysql.user;

查看当前用户：

    SELECT USER();

创建用户：

    CREATE USER 'username'@'mysqlserver' IDENTIFIED BY 'password';

对本地登陆的用户授

    GRANT ALL ON *.* TO 'username'@'localhost' IDENTIFIED BY 'password';


# MysqlConnector

Mysql官方提供的API

Download:

<http://dev.mysql.com/downloads/connector/>

## connector/ODBC

    sudo yum/apt-get install mysql-connector-odbc

## connector/J

下载java安装包安装。

## connector/Python

    sudo yum/apt-get install mysql-connector-python

    import mysql.connector
    cnx = mysql.connector.connect(user='scott', password='tiger', host='127.0.0.1', database='employees')
    cnx.close()

    from mysql.connector import (connection)
    cnx = connection.MySQLConnection(user='scott', password='tiger', host='127.0.0.1', database='employees')
    cnx.close()

