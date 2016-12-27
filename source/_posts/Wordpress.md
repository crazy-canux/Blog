---
layout: post
title: Wordpress
comments: true
date: 2016-11-18 00:06:31
updated:
tags:
- wordpress
categories:
- Web
permalink:
---

# WordPress

# 安装

安装依赖：

    sudo apt install apache2
    sudo apt install mysql-server
    sudo apt install php5

下载wordpress：

    $cd /var/www/html
    $git clone https://github.com/WordPress/WordPress.git

# 配置

添加mysql数据库：

    $mysql -u root -p
    mysql> create user 'wordpress'@'localhost' identified by '******';
    mysql> create database 'wordpress';
    mysql> GRANT ALL PRIVILEGES ON wordpress.* TO "wordpress"@"localhost";
    mysql> FLUSH PRIVILEGES;

登陆并安装站点：

    http://localhost/WordPress/wp-admin/install.php

***

# 主题

修改wp-config.php安装主题不用输入ftp信息：

    define("FS_METHOD", "direct");
    define("FS_CHMOD_DIR", 0777);
    define("FS_CHMOD_FILE", 0777);

主题安装在：

    wordpress/wp-content/themes

主题数据导入到:

    wordpress/wp-content/uploads

***

# 插件

插件安装在：

    wordpress/wp-content/plugins

## WordPress Reset

一款可以重置所有数据库数据的插件。

## widget-settings-importexport

## wordpress-importer

## wordpress-move
