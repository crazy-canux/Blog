---
layout: post
title: Database之MSSQL
comments: true
date: 2016-04-06 15:33:42
updated:
tags:
- mssql
- database
- pymssql
- pyodbc
- freetds
categories:
- Database
permalink:
---

# MSSQL

商业版：
1. 企业版
2. 商业智能版
3. 标准版

免费版：
1. Express
2. Compact
3. Web

SQL Server Management Studio是mssql的图形化管理界面。

system databases:
1. master
2. model
3. msdb
4. tempdb

# sql query

查询数据库版本：

    SELECT @@VERSION

查询数据库服务器：

    SELECT @@SERVERNAME

查询数据库实例名,默认MSSQLSERVER：

    SELECT @@SERVICENAME

创建/删除数据库：

    CREATE DATABASE databasename
    DROP DATABASE databasename

# freeTDS

> FreeTDS is a set of libraries for Unix and Linux that allows your programs to
natively talk to Microsoft SQL Server and Sybase databases.

<http://www.freetds.org/>

<https://github.com/FreeTDS/freetds>

    sudo apt-get install freetds*

配置freetds，/etc/freetds/freetds.conf:

    # A typical Sybase server
    [egServer50]
            host = symachine.domain.com
            port = 5000
            tds version = 5.0

    # A typical Microsoft server
    [egServer70]
            host = ntmachine.domain.com
            port = 1433
            tds version = 7.0

# Python

通过python访问mssql需要安装相应的包，linux还需要安装freeTDS。

## pymssql

    import pymssql
    conn = pymssql.connect(server, user, password, database, timeout, login_timeout, charset, as_dict, appname, port)
    # charset='utf-8'
    # as_dict, appname, port 三个是关键字选项。
    # as_dict=true 表示每行以字典的形式返回，而不是默认的元组。
    cursor = conn.cursor()
    cursor.execute(SQL)
    ...
    cursor.close()
    conn.close()

debug:

(7202, "Could not find server 'euedcapp0049.edc.eu.corp' in sys.servers. Verify
that the correct server name was specified. If necessary, execute the stored
procedure sp_addlinkedserver to add the server to sys.servers.DB-Lib error
message 7202, severity 11:General SQL Server error: Check messages from the SQL
Server")

(7391, 'The operation could not be performed because OLE DB provider "SQLNCLI10"
for linked server "euedcapp0049.edc.eu.corp" was unable to begin a distributed
transaction.DB-Lib error message 7391, severity 16:\nGeneral SQL Server error:
Check messages from the SQL Server\n')

## pyodbc

(linux测试没有通过，linux好像还需要安装配置ODBC）

导入

    import pyodbc

windows连接

    cnxn = pyodbc.connect('DRIVER={SQL Server};SERVER=localhost;PORT=1433;DATABASE=testdb;UID=me;PWD=pass')

linux连接

    cnxn = pyodbc.connect('DRIVER={FreeTDS};SERVER=localhost;PORT=1433;DATABASE=testdb;UID=me;PWD=pass;TDS_Version=7.0')

通过ODBC配置了DSN的连接

    cnxn = pyodbc.connect('DSN=DataSourceName;UID=user;PWD=password')

使用

    cursor = cnxn.cursor()
    cursor.execute(SQL)
    ...
    cursor.close()
    cnxn.close()

# java

需要安装sqljdbc才能通过java访问mssql数据库

    Class.forName("com.microsoft.sqlserver.jdbc.SQLServerDriver");
    String connectionUrl = "jdbc:sqlserver://localhost;database=AdventureWorks;integratedSecurity=true;"
    Connection con = DriverManager.getConnection(connectionUrl);

## Installation Instructions for the Microsoft Windows version of the JDBC Driver

Note: By downloading the Microsoft JDBC Driver 6.0 (Preview), 4.2, 4.1, or 4.0
for SQL Server, you are accepting the terms and conditions of the End-User
License Agreement (EULA) for this component. Please review the End-User License
Agreement (EULA) located on this page and print a copy of the EULA for your
records.

1. Download sqljdbc_<version>_<language>.exe to a temporary directory.

2. Run sqljdbc_<version>_<language>.exe.

3. Enter an installation directory when prompted. We recommend that you unpack
   this zip file in %ProgramFiles% with the default directory: "Microsoft JDBC
   Driver x.x for SQL Server".

## Installation Instructions for the UNIX version of the JDBC Driver

1. Download sqljdbc_<version>_<language>.tar.gz to a temporary directory.

2. To unpack the zipped tar file, navigate to the directory where you want
   the driver unpacked and type gzip -d sqljdbc_<version>_<language>.tar.gz.

3. To unpack the tar file, move it to the directory where you want the
   driver installed and type tar –xf sqljdbc_<version>_<language>.tar.
