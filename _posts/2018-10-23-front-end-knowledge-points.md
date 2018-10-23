---
layout: post
title:  "前端常见知识点总结"
date:   2018-10-23 13:02:18 +0800
categories: 前端知识
tags:  前端知识 CSS 三栏布局
author: Xu ShiJie
---

* content
{:toc}

> 一直想着多总结工作当中的经验。苦于没时间，一直耽搁了，记着的知识点全都放在电脑，总觉得它会一直在磁盘里又跑不掉，忘记了翻翻总会记得。可是，好记性不如烂笔头，是时候总结一篇文章，记录一下经常记不住又容易混淆的前端知识点！本文参考了 [郑州卓越](https://www.jianshu.com/p/f60e83e24296) 的简书。


### session、cookie、sessionStorage、localStorage等区别？

`session` 会在一定的时间内存储在服务器端，用来保存用户的对象信息，`session` 不能区分路径，同一个用户在访问一个网站期间，所有的 `session` 在任何一个地方都可以访问到；

`cookie`、`sessionStorage`、`localStorage`的相同点是都存储在客户端，不同点分别表现在存储大小、有效时间、数据与服务器的交互方式

>1）存储大小

`cookie`数据大小不能超过4k。

`sessionStorage`和`localStorage`虽然也有存储大小的限制，但比`cookie`大得多，可以达到5M或更大。

>2）有效时间





`localStorage` :存储持久数据，浏览器关闭后数据不丢失除非主动删除数据。
`sessionStorage` : 数据在当前浏览器窗口关闭后自动删除。         
`cookie` : 设置的 `cookie` 过期时间之前一直有效，即使窗口或浏览器关闭。

>3） 数据与服务器之间的交互方式

`cookie` 的数据会自动的传递到服务器，服务器端也可以写`cookie` 到客户端

`sessionStorage` 和 `localStorage` 不会自动把数据发给服务器，仅在本地保存。

### HTML5新增了哪些内容或API，使用过哪些？
>1）document.querySelector()和document.querySelectorAll()方法

```js
document.querySelector();document.querySelectorAll();
```

#### document.querySelector();
根据css选择器返回第一个匹配的元素，如果没有匹配返回 `null`。

#### document.querySelectorAll("selector");
`querySelectorAll` 和 `querySelector` 作用一样的，只是 `querySelectorAll` 返回的是元素数组， `querySelector` `返回的是一个元素。如果querySelectorAll` 没有匹配的内容返回的是一个空数组。

>2）HTML5之classList属性

classList属性没有出现之前js操作元素class都是使用className,但是在开发一个网站的时候标签的class不只是一个，有可能有很多。这个时候使用className操作多个类就比较麻烦了。

##### `length`属性:
表示元素类名的个数，只读；

##### `item()`
支持一个参数，为类名的索引，返回对应的类名；

##### `add(value);`
将给定的字符串值添加到列表中。如果值已经存在，就不添加了；

##### `contains(value);`
表示列表中是否存在给定的值，如果存在则返回true，否则返回false。

##### `remove(value);`
从列表中删除给定的字符串。

##### `toggle(value);`
如果列表中已经存在给定的值，删除它。如果列表中没有给定的值，添加它。

>3）内容可编辑（contenteditable）。

>4）HTML5之全屏

>5）HTML5之页面可见性(Page Visibility) 

...等等

### input和textarea的区别？

不同点：是一个单行输入框，有value属性（value属性指定初始值），但是它不能自动换行；用来放置字数较少的单行文字内容。是一个多行输入框，没有value属性，但是它能自动换行；一般让用户可以输入多行文字,输入的文字信息量相比较大。

相同点：input标签和textarea标签的使用目的都是让用户输入内容，提交内容。

### 用一个div模拟textarea的实现?

在一个普通的div上添加h5里面的内容contenteditable="true"，就可以实现一个div变成textarea文本输入框，contenteditable不会存在兼容性的问题，在IE6已经得到支持。

```html
<div contenteditable="true"></div>
```

### 移动设备忽略将页面中的数字识别为电话号码的方法?

如果忽略页面中的数字识别为电话号码, 只要把这个默认行为关闭就行，只要一行代码: 

```html
<meta name="format-detection" content="telephone=no"> 
// 扩展
<meta name="format-detection" content="emial=no,address=no">
```

### 谈谈你对盒式模型的理解？

所有的HTML元素都可以看成一个盒子，它包括边距 `margin` ，边框 `border` ，填充`padding`，内容`content`。盒式模型分为IE盒式模型和W3C标准盒式模型，区别：IE的盒式模型元素的宽度（高度）为内容`Content`、边框`border`以及填充padding的宽度（高度）之和；标准盒式模型元素的宽度（高度）为内容`Content`的宽度（高度）之和，不包含边框`border`与`padding`的宽度与高度。标准盒式模型与W3C标准盒式模型可以通过`box-sizing`属性指定，`box-sizing：border-box`为IE盒式模型（又称怪异盒式模型），`box-sizing`默认为`content-box`标准盒式模型。

### 如何实现div块级元素的水平居中、水平与垂直居中，都有哪些实现方式？

>水平居中：

（1）`margin：0 auto;`（2）`display：flex;` 、`justify-content：center；`

>水平与垂直居中：（div的父级position：relative）

（1）div宽高确定，设置div的`position：absolute`，top和left设置成50%，再设置`margin-top`:高度/2,`margin-left`:宽度/2;

（2）div宽高确定，设置div的`position：absolute`；top、right、bottom、right设置为0，`margin`设置为auto；

```html
<div class='div'>
    我的宽高确定
</div>
<style> 
    .div{
        position：absolute;
        top:0;
        right:0;
        bottom:0;
        right:0;
        margin:auto;
    }
</style>
```

（3）不论div的宽高是否确定，使用`transform`。
父级`position:relative;`子级`postion:absolute;`left:50%;top:50%;`transform`:`translate`(-50%,-50%);

```html
<div class='parent'>
    我是父级元素
    <div calss='child'> 
    我是子级元素
    </div>
</div>

<style> 
.parent{
    position:relative
}

.child {
    position:absolute;
    left:50%;
    top:50%;
    transform:translate(-50%,-50%);
}
</style>
```

（4）不论div的宽高是否确定，flex布局（IE9以下不支持）
```html
display：flex，justify-content：center；align-items：center；
```

### 扩展问题： CSS中常见的三栏布局/圣杯布局有哪几种方式？
> 左右各300，中间自适应？

 1、浮动 2、绝对定位 3、flex 4、table-cell 5、grid 网格布局 

直接上代码吧。。。。

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>layout</title>
</head>

<style media="screen">
    html * {
        padding: 0;
        margin: 0;
    }

    .layout {
        margin-top: 10px;
    }

    .layout article div {
        min-height: 100px;
    }

    .layout.float .left {
        width: 300px;
        float: left;
        background: red;
    }

    .layout.float .right {
        width: 300px;
        float: right;
        background: green;
    }

    .layout.float .center {
        background: yellow;
    }
</style>

<body>
    <!-- 这是浮动解决方案 -->
    <section class="layout float">

        <article class="left-center-right">
            <div class="left"></div>
            <div class="right"></div>
            <div class="center">
                <h2>这是浮动解决方案</h2>
                我是中间，我自适应了！！
                我是中间，我自适应了！！
            </div>

        </article>

    </section>

    <!-- 这是定位解决方案 -->
    <section class="layout absolute">
        <style media="screen">
            .layout.absolute .left-center-right>div {
                position: absolute;
            }

            .layout.absolute .left {
                left: 0;
                width: 300px;
                background: red;
            }

            .layout.absolute .center {
                left: 300px;
                right: 300px;
                background: yellow;
            }

            .layout.absolute .right {
                right: 0;
                width: 300px;
                background: green;
            }
        </style>
        <article class="left-center-right">
            <div class="left"></div>
            <div class="right"></div>
            <div class="center">
                <h2>绝对定位解决方案</h2>
                我是中间，我自适应了！！
                我是中间，我自适应了！！
            </div>
        </article>
    </section>


 <!-- 这是flexbox解决方案 -->
    <section class="layout flexbox">

        <style>
            .layout.flexbox {
                margin-top: 140px;
            }

            .layout.flexbox .left-center-right {
                display: flex;
            }

            .layout.flexbox .left {
                width: 300px;
                background: red;
            }

            .layout.flexbox .center {
                flex: 1;
                background: yellow;
            }

            .layout.flexbox .right {
                width: 300px;
                background: green;
                ;
            }
        </style>
        <article class="left-center-right">
            <div class="left"></div>
            <div class="center">
                <h2>flexbox解决方案</h2>
                我是中间，我自适应了！！
                我是中间，我自适应了！！
            </div>
            <div class="right"></div>
        </article>

    </section>


    <!-- 这是table解决方案 -->
    <section class="layout table">
        <style>
            .layout.table .left-center-right {
                width: 100%;
                display: table;
                height: 100px;
            }

            .layout.table .left-center-right>div {
                display: table-cell;
            }

            .layout.table .left {
                width: 300px;
                background: red;
            }

            .layout.table .right {
                width: 300px;
                background: green;
            }

            .layout.table .center {
                background: yellow;
            }
        </style>
        <article class="left-center-right">
            <div class="left"></div>
            <div class="center">
                <h2>table解决方案（表格布局）</h2>
                我是中间，我自适应了！！
                我是中间，我自适应了！！
            </div>
            <div class="right"></div>
        </article>
    </section>

    <!-- 这是网格解决方案 -->
    <section class="layout grid">
        <style>
            .layout.grid .left-center-right {
                display: grid;
                width: 100%;
                grid-template-rows: 100px;
                grid-template-columns: 300px auto 300px;
            }

            .layout.grid .left {
                background: red;
            }

            .layout.grid .center {
                background: yellow;
            }

            .layout.grid .right {
                background: green;
            }
        </style>
        <article class="left-center-right">
            <div class="left"></div>
            <div class="center">
                <h2>grid解决方案（网格布局）</h2>
                我是中间，我自适应了！！
                我是中间，我自适应了！！
            </div>
            <div class="right"></div>
        </article>
    </section>
</body>

</html>
```


### 流式布局，自适应布局，响应式布局，弹性布局优缺点以及使用场景？

>静态布局：给页面元素设置固定的宽度与高度，单位px，窗口缩小；实际开发中再PC端比较实用，手机端适配不同分辨率，要写多个样式文件。

>自适应布局：创建多个静态布局，每个静态布局对应一个屏幕分辨率，使用@media媒体查询技术。

>流式布局：元素的宽高用百分比做单位，元素的宽高按屏幕分辨率调整。

>响应式布局：采用自适应布局与流式布局的结合，为不同分辨率范围创建流式布局。

>弹性布局：使用em或rem单位来定义元素宽度，与流式布局有极大的相似性

关于本段可以延伸出更多的知识点，会在下一篇详细记录。


