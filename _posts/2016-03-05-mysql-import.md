---
layout: post
title: Mysql高版本导入到低版本
categories: [Web]
tags : [mysql]
---


## 背景介绍

由于现在阿里云的主机只支持 Mysql5.1 版本，而我们本地开发环境一般使用 Mysql5.5 。
这样就导致了数据库版本不兼容。

## 方法一

一般的解决办法是在高版本（Mysql5.5）通过 phpMyAdmin 导出数据时导出方式选择自定义，兼容性选 MYSQL40 ，然后再导入到低版本数据库（Mysql5.1）。


## 方法二

而阿里云在前段时间将 phpMyAdmin 下架，现在只能使用 DMS 管理，结果用上面的方法通过 DMS 导入数据总是提示错误，无法导入成功。给阿里云提交工单后，他们给出的回复

> 您好，此情况您只能先将备份恢复导入您本地的低版本的数据库，然后再备份后通过如下链接的网站搬家恢复到虚机数据库。https://help.aliyun.com/knowledge_detail/6699338.html

PS: 我真的好想吐槽啊！

## 方法三

没有用方法二，因为一般人也不会特地装两个版本的数据库吧。而是自己给主机安装 phpMyAdmin ：

1 下载phpmyadmin安装包,解压到服务器的Web站点文件根目录

2 然后将安装目录重命名为phpmyadmin, 进入目录/data/www/phpMyAdmin/libraries，查看配置文件config.default.php。

3 修改配置文件config.default.php

    - $cfg['Servers'][$i]['host'] = 'localhost';
    指定MySQL服务器所在的主机名，通常用默认值。

    - $cfg['Servers'][$i]['port'] = '';
    指定MySQL的监听端口，保持空白则表示使用默认端口3306。

    - $cfg['blowfish_secret'] = '任意字符(例如asdfghk) ';
    指定cookie的短语密码

    - $cfg['Servers'][$i]['auth_type'] = 'config';
    指定认证方法。在本机调试时用config。如果在外部访问调试，使用cookie。

    - $cfg['blowfish_secret'] = 'php';
    指定用于cookie认证的信息，可以是任何字符串。

    - $cfg['Servers'][$i]['user'] = 'root';
    填写MySQL管理者的帐号,一般是root。

    - $cfg['Servers'][$i]['password'] = 'rootpass';
    填写root帐户的密码。

4 访问http://1.1.1.1/phpmyadmin即可（将1.1.1.1替换成你自己的IP或者域名）。

5 然后使用方法一将数据文件导入即可。