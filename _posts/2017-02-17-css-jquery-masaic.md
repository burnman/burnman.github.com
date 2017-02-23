---
layout: post
title: 使用 CSS 和 jQuery 制作文字马赛克效果
categories: [CSS]
tags : [css jquery]
---


## 需求

一段文本中，给指定的文字打上马赛克，然后付费阅读


## 解决方法

### 方法一：使用 CSS 模糊文字

```
span.mosaic {
	color: transparent;
	text-shadow: 0 0 10px rgba(0,0,0,0.5);
}
```

上面的代码使class为`mosaic`的<span>中的文字变得透明，只保留文字的text-shadow，从而模拟出一种文字模糊的效果。你可以通过text-shadow属性的第三个参数来调整文字模糊的效果。

效果：

>Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod
tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam,
quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo
consequat. <span class="mosaic" style="color: transparent; text-shadow: 0 0 10px rgba(0,0,0,0.5);">Duis aute irure dolor in reprehenderit in voluptate velit esse
    cillum dolore</span> eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non
proident, sunt in culpa qui officia deserunt mollit anim id est laborum.

增加 IE 支持

```
span.mosaic {
	color: transparent;
	text-shadow: 0 0 10px rgba(0,0,0,0.5);
	filter: DXImageTransform.Microsoft.Blur(pixelradius=2);
	zoom: 1;
}
```

这种办法是以模糊文字来达到马赛克效果，但是有时客户会要求用其它图片或者符号来替换被打了马赛克的文字，这种办法就无法满足了。


### 方法二：使用图片马赛克遮罩文字

#### 效果一

因为直接接给标签`samp`加上图片遮罩层，在原本文字换行的情况下，会直接显示在下一行，破坏原本的结构。


#### 效果二

在效果一基础上，为了不破坏原本的结构。需要将一段文字拆分成单个文字，然后使用标签`span`包裹，最后使用 `span::before` 给每个文字增加一个图片遮罩层。

#### 效果：

<p data-height="265" data-theme-id="0" data-slug-hash="vgMPNy" data-default-tab="css,result" data-user="spaling" data-embed-version="2" data-pen-title="文字马赛克" class="codepen">See the Pen <a href="http://codepen.io/spaling/pen/vgMPNy/">文字马赛克</a> by spaling (<a href="http://codepen.io/spaling">@spaling</a>) on <a href="http://codepen.io">CodePen</a>.</p>
<script async src="https://production-assets.codepen.io/assets/embed/ei.js"></script>


***

## 最终代码

HTML

``` html
Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod
tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam,
quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo
consequat. <samp>Duis aute irure dolor in reprehenderit in voluptate</samp> velit esse
    cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non
proident, sunt in culpa qui officia deserunt mollit anim id est laborum.
```

SASS

```
samp {
    &>span {
        position: relative;
        display: inline-block;
        *display: inline;
        *zoom: 1;
        &::before {
            position: absolute;
            content: '';
            width: 100%;
            height: 100%;
            z-index: 2;
            left: 0;
            top: 0;
            background: #fff url(../images/mask.jpg) repeat;
            -webkit-background-size: contain;
            background-size: contain;
        }
    }
}
```

Jquery

```
$('samp').each(function() {
    var letters = $(this).text().split(''),
        $container = $(this).empty();

    $.each(letters, function(_, letter) {
        $('<span>', {
            text: letter
        }).appendTo($container);
    });
});
```




