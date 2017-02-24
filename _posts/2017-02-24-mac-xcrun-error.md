---
layout: post
title: Mac 出现 missing xcrun 错误
categories: [Mac]
tags : [xcrun]
---

升级到 macOS Sierra 10.12.3 后，在更新 [oh my zsh](https://github.com/robbyrussell/oh-my-zsh) 时出现下面错误提示

> xcrun: error: invalid active developer path (/Library/Developer/CommandLineTools), missing xcrun at: /Library/Developer/CommandLineTools/usr/bin/xcrun

## 解决办法

重装下`xcode command line`

在命令行中执行以下代码

{% highlight SCSS %}
xcode-select --install
{% endhighlight %}

然后会弹出窗口让你安装，安装完就ok了

[stackoverflow](http://stackoverflow.com/questions/32893412/command-line-tools-not-working-os-x-el-capitan-macos-sierra/)