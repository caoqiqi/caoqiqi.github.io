---
layout: post
title: 居中
date: 2012-07-08
excerpt: css实现水平居中、垂直居中
tags: [水平居中, 垂直居中, css]
comments: true
---
<style type="text/css">
    *{
    font-family:"幼圆";
    font-weight:bold;   
}
    h2{
    color:#000;
    background-color:#1CA366;
}
    em{
    color:red;
}
	h3{
	color:#2841D8;
}
</style>
## 水平居中

### text-align：center

* 针对要居中元素的父元素；
* 图片，按钮，文字等行内元素(display为inline或inline-block等)；
* IE6、7都可以

### margin：0 auto

* 针对要居中的元素；
* 父元素要设置width；

## 垂直居中

### line-height

* 文字的line-height设为文字父容器的高度；
* 适用于只有一行文字的情况

## 水平+垂直居中

### 表格

1. td或th设置属性：align="center"；valign="middle" 如：<td align="center">hahah</td>
2. css样式：表格默认垂直居中，也可vertical-align:middle；
			水平居中：text-align:center（IE6、7都有效，IE8+以及谷歌、火狐只对行内元素有效）；

### display:table-cell

* 将要居中元素的父元素添加display:table-cell，模拟表格单元格，再用表格居中的方法进行设置；
* IE8+、谷歌、火狐等浏览器上适用，IE6、IE7都无效。

### 绝对定位法1

已知元素及其父元素的宽度或高度

```html
<style>
	body{margin:0; padding:0;}
	.parent{width:200px; height:200px; border:1px solid red; position:relative;}
	.child{width:100px; height:100px; background:#000; position:absolute;
		left:50%;
		top:50%;
		margin-left:-50px;  /****负的元素宽度的一半****/
		margin-top:-50%;	/****负的元素高度的一半****/
	}
</style>
<body>
	<div class="parent">
		<div class="child"></div>
	</div>
</body>
```

### 绝对定位法2

* 已知元素及其父元素的宽度或高度
* 适用于IE9+,谷歌，火狐等符合w3c标准的现代浏览器

```html
<style>
	body{margin:0; padding:0;}
	.parent{width:200px; height:200px; border:1px solid red; position:relative;}
	.child{width:100px; height:100px; background:#000; position:absolute;
		left:0;
		top:0;
		right:0;
		bottom:0;
		margin:auto;
	}
</style>
<body>
	<div class="parent">
		<div class="child"></div>
	</div>
</body>
```

### 居中浮动元素
 1. 层相对于浏览器窗口居中

```html
<style type="text/css">        
div {
	position:absolute;
	top:50%;
	left:50%;
	margin:-150px 0 0 -200px;
	width:400px;
	height:300px;
	border:1px solid #008800;
}
</style>
<div>让层垂直居中于浏览器窗口</div>
```

2. 子div居中于父div

只需将父div添加position：relative，设置宽高；


