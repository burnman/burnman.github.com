---
layout: post
title: 博客简介
categories: [intro]
tags : [intro， jekyll, github-pages]

---
## 简介
博客使用 Jekyll + Github Pages 搭建
使用主题：lanyon

### lanyon介绍
> Lanyon is an unassuming [Jekyll](http://jekyllrb.com/) theme that places content first by tucking away navigation in a hidden drawer. It's based on [Poole](http://getpoole.com/), the Jekyll butler.

- 项目地址: https://github.com/poole/lanyon
- 展示地址: http://lanyon.getpoole.com


### 基于lanyon的修改
在lanyona的基础上增加了三个页面

{% highlight js %}
tag.md                  //标签页·按文章标签(tags)来进行归档
category.md             //分类页· 按(category)分类名来进行归档
archive.md              //归档页·按时间来进行归档
{% endhighlight %}

这些分类都依赖于文章页(post)头部的代码来识别，下面是示例：

{% highlight  %}
---
layout: post            //调用_layouts中的post.html作为布局模板
title: Introducing      //文章标题
categories: [intro]     //分类名，用于'category.md'页面的归档
tags : [intro, tag]     //标签，用于'tag.md'页面的归档
---
{% endhighlight %}

### 使用
1. 首先你需要拥有自己的Github账号并已经创建了自己的个人主页`User Pages`
    - 关于Github Pages的分类，请参考：[User, Organization and Project Pages](https://help.github.com/articles/user-organization-and-project-pages)
    - 如果你还不会创建，可以参考这个两个教程：
        * [通过GitHub Pages建立个人站点（详细步骤）](http://www.cnblogs.com/purediy/archive/2013/03/07/2948892.html)
        * [一步步在GitHub上创建博客主页](http://pchou.info/web-build/2013/01/05/build-github-blog-page-02.html)
2. 克隆项目，去除_posts下的文章，上传至你的仓库
3. 访问地址，其中`USERNAME`是你的Github用户名
```
USERNAME.github.io
```