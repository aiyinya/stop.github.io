---
layout:     post
title:      Markdown Beginner
subtitle:   
date:       2018-09-25
author:     Xin YAO
catalog: true
tags:
    - Markdown
---
<!-- MarkdownTOC -->

- [前言](#%E5%89%8D%E8%A8%80)
    - [Tools](#tools)
- [Markdown: Syntax](#markdown-syntax)
    - [目录](#%E7%9B%AE%E5%BD%95)
    - [标题](#%E6%A0%87%E9%A2%98)
    - [列表](#%E5%88%97%E8%A1%A8)
        - [无序](#%E6%97%A0%E5%BA%8F)
        - [有序](#%E6%9C%89%E5%BA%8F)
        - [嵌套列表](#%E5%B5%8C%E5%A5%97%E5%88%97%E8%A1%A8)
    - [引用](#%E5%BC%95%E7%94%A8)
    - [图片](#%E5%9B%BE%E7%89%87)
    - [链接](#%E9%93%BE%E6%8E%A5)
    - [索引链接](#%E7%B4%A2%E5%BC%95%E9%93%BE%E6%8E%A5)
    - [本身就是链接](#%E6%9C%AC%E8%BA%AB%E5%B0%B1%E6%98%AF%E9%93%BE%E6%8E%A5)
    - [分割线](#%E5%88%86%E5%89%B2%E7%BA%BF)
    - [表格](#%E8%A1%A8%E6%A0%BC)
    - [代码块](#%E4%BB%A3%E7%A0%81%E5%9D%97)
    - [转义](#%E8%BD%AC%E4%B9%89)
    - [Others](#others)
        - [粗体](#%E7%B2%97%E4%BD%93)
        - [斜体](#%E6%96%9C%E4%BD%93)
        - [字体, 字号, 和颜色](#%E5%AD%97%E4%BD%93-%E5%AD%97%E5%8F%B7-%E5%92%8C%E9%A2%9C%E8%89%B2)
- [Reference](#reference)

<!-- /MarkdownTOC -->

# 前言
阶段性总结有利于精确自己的目标, 以及为后续的想法开辟空间.

因此开始有必要整理记录.

但是因为没必要像写paper那样规范使用latex, 因此就选择了Markdown.


## Tools
Windows - [MarkdownPad](http://www.markdownpad.com/)

Github Pages - (If you have one)

# Markdown: Syntax
## 目录
    [TOC]

由于github不支持显示TOC, 因此需要先用**markdown-toc**[4]进行预处理
也可以使用sublime里的**markdown-toc**[5]插件.

## 标题
    # content
    ## content
    ### content
    ......

一共可以设置六级标题

## 列表
### 无序
    * 1
    * 2
    * 3
* 1
* 2
* 3

### 有序
    1. 1
    2. 2
    3. 3
1. 1
2. 2
3. 3

### 嵌套列表
    - AAA
      + A
        - a
          1. contentA
          2. contentB

- AAA
  + A
    - a
      1. contentA
      2. contentB

## 引用
    > contentA
      >> contentB

> contentA
  >> contentB

之后的文本内容需要插入空行

## 图片
    ！[icon](link to the picture)

## 链接
    [content](link to the content)

## 索引链接
    [content][1]
    [1]:Url
[content][1]
[1]:Url

## 本身就是链接
    <url>
<https://xinyao1994.github.io/>

## 分割线
    ***
	---

## 表格
    | Tables        | Are           | Cool  |
    | ------------- |:-------------:| -----:|
    | col 3 is      | right-aligned | $1600 |
    | col 2 is      | centered      |   $12 |
    | zebra stripes | are neat      |    $1 |

| Tables        | Are           | Cool  |
| ------------- |:-------------:| -----:|
| col 3 is      | right-aligned | $1600 |
| col 2 is      | centered      |   $12 |
| zebra stripes | are neat      |    $1 |

## 代码块
    ``` [python]
    @requires_authorization
    def add(a, b): # add a and b
        return a+b
    class TA:
    ```

``` [python]
@requires_authorization
def add(a, b): # add a and b
	return a+b
class TA:
```

or 每行文字前加4个空格或者1个Tab

## 转义


## Others
### 粗体
    **content**
**content**

    __content__
__content__

### 斜体
    *content*
*content*

    _content_
_content_

### 字体, 字号, 和颜色
    <font face="黑体">我是黑体字</font>
    <font face="微软雅黑">我是微软雅黑</font>
    <font face="Verdana">I like Verdana format</font>

<font face="黑体">我是黑体字</font>

<font face="微软雅黑">我是微软雅黑</font>

<font face="Verdana">I like Verdana format</font> 

# Reference
[1]:[Markdown: Syntax](https://daringfireball.net/projects/markdown/syntax)

[2]:[认识与入门 Markdown](https://sspai.com/post/25137)

[3]:[Markdown 语法大全](https://blog.csdn.net/qcx321/article/details/53780672)

[4]:[markdown toc](https://github.com/houbb/markdown-toc)

[5]:[sublime with markdown-toc](https://www.cnblogs.com/Sinte-Beuve/p/5148108.html)
