---
layout: post
title: Wordpress 无法切换可视化和文本编辑器
categories: [Wordpress]
tags : []
---


## 背景介绍

升级 WordPress 到最新版本后，发现点击“添加媒体”、“可视化/文本编辑模式切换”等功能按钮均失效没反应


## 原因

查找资料发现wordpress为了提高效率以及加载速度，把要用到的js文件合并在一起，升级到新版本后可能因为某些原因导致合并出现错误，因此产生了按钮异常等情况。


### 官方解释

> ### Disable Javascript Concatenation

>To result in a faster administration area, all Javascript files are concatenated into one URL. If Javascript is failing to work in your administration area, you can try disabling this feature:

>`define('CONCATENATE_SCRIPTS', false);`

大概意思是：

>wordpress 为了提高效率要求你所有的js要集中到一起，只需更改路径集中存放，问题迎刃而解，具体操作很简单，在wordpress根目录下找到 wp-config.php 这个配置文件，打开文件后在页面的最后添加下面代码:

>`define('CONCATENATE_SCRIPTS', false);`


## 解决办法

在网站根目录的wp-config.php文件中，添加以下这句代码即可：

```
define('CONCATENATE_SCRIPTS', false);
```

这段代码的作用是禁止js连接在一起