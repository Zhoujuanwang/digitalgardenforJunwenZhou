---
{"dg-publish":true,"permalink":"/Obsidian学习/HTML语法/","dgPassFrontmatter":true}
---

## HTML介绍

### 开始学习HTML

#### HTML元素

##### 学习过程中涉及到的元素

```html
<p>段落元素</p>
<em>一种内联元素</em>
<a href="" title="" target="">超链接元素</a>
<!-- 下面这个输入框不包含 disabled 属性，所以用户可以向其中输入 -->
<input type="text">
```

##### 块级元素和内联元素

```html
<em>第一</em><em>第二</em><em>第三</em>

<p>第四</p>
<p>第五</p>
<p>第六</p>
```

我理解的：块级元素就是会自动换行的；而内联元素可以多个出现在同一行

##### 空元素
不需要开始标签和结束标签，比如\<img>元素

#### 属性
属性和元素之间，属性和属性之间需要用空格分开；包括属性名称和属性值

```html
<font color='green'>这是一个定义文本颜色为绿色的属性</font>
```

例子：超链接的属性
超链接由元素\<a>和<\\a>定义，包括href、title、target三个属性，href制定了超链接的地址，title指定了超链接的名称，target决定是否在新标签页中打开超链接
```html
<p>这是一个<a href='https://www.bilibili.com/' title="B站">B站</a>的超链接</p>
```

##### 布尔属性
有时你会看到没有值的属性，这也是完全可以接受的。这些属性被称为布尔属性。布尔属性只能有一个值，这个值一般与属性名称相同。例如，考虑 [`disabled`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/input#disabled) 属性，你可以将其分配给表单输入元素。用它来禁用表单输入元素，这样用户就不能输入了。被禁用的元素通常有一个灰色的外观。

```html
<input type="text" disabled="disabled" />
<!--可以简写为-->
<input type="text" disabled />
```

实例

```html
<!doctype html>
<html lang="zh-CN"> <!-- html元素包裹所有元素，被称为根元素-->
  <head> <!--head元素，包含了所有你想包含在HTML页面中但不在HTML页面中显示的内容-->
    <meta charset="utf-8" /> <!--这个元素代表了不能由其他 HTML 元相关元素表示的元数据，比如 <base>、<link>、<script>、<style> 或 <title>-->
    <title>我的测试站点</title>
  </head>
  <body>
    <p>这是我的页面</p>
  </body><!--<body> 元素。包含了你访问页面时所有显示在页面上的内容，包含文本、图片、视频、游戏、可播放音频轨道等等-->
</html>

```

##### 特殊字符的转义？
请参见 [XML 和 HTML 字符实体引用列表](https://zh.wikipedia.org/wiki/XML%E4%B8%8EHTML%E5%AD%97%E7%AC%A6%E5%AE%9E%E4%BD%93%E5%BC%95%E7%94%A8%E5%88%97%E8%A1%A8)

### HTML头元素
所谓html头元素就是\<head>元素里面的内容，这些内容是不会在网页的界面中显示的，头元素的作用是存储这个网页的“元数据”
头元素包括：

#### \<title>
标题元素，是给整个网页命名的

#### \<meta>
该元素中有一个属性，可以指定文档的字符编码

```html
<meta charset="utf-8" />
```

还有name属性和content属性可以指定网页的作者和描述

```html
<meta name="author" content="Chris Mills" />
<meta
  name="description"
  content="The MDN Web Docs Learning Area aims to provide
complete beginners to the Web with all they need to know to get
started with developing web sites and applications." />

```
description的作用之一就是搜索引擎优化，就是通过搜素引擎找到这个网页时，可以看到这个给网页的描述，让我们能简单了解这个网页的内容。

##### 为网页添加图标

```html
<link rel="icon" href="favicon.ico" type="image/x-icon" />
<!--图片的位置要与html文件放在同一个目录下-->
```

#### 与CSS和JavaScript联用
与css联用时，需要用到\<link>元素，该元素包括两个属性：rel属性表明这是该HTML文档的css/样式表格式，href属性指定该css文件的路径

```html
<link rel="stylesheet" href="my-css-file.css" />
```

### HTML文本处理基础
标题：
从\<h1>一直到\<h6>
段落元素被\<p>包围：
<p>这是一个段落</p>

#### 有序列表和无序列表
有序列表用\<ul> 包裹，每一个项由\<li>，有序列表则由<\ol>包裹
示例区：

<ul>This is a unordered list
<li>one</li>
<li>two</li>
</ul>
<ol>This is a ordered list
<li>one</li>
<li>two</li>
</ol>

