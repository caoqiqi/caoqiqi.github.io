---
layout: post
title: 其他
date: 2016-07-21
excerpt: position跟display、margin collapse、overflow、float这些特性相互叠加后会怎么样？
tags: [position,display,margin collapse,overflow,float]
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
 
## 一、position，display，float的关系
Position：absolute|fixed或float时，会改变display的设置，变为inline-block（display：none时除外）;
当position：absolute|fixed时，float设置失败

## 二、margin collapse
这两个或多个外边距没有被非空内容、padding、border或clear分隔开；
这些 margin 都处于普通流中。
注：创建了块级格式化上下文的元素，不和它的子元素发生 margin 折叠

## 三、position、overflow的关系
父节点设置overflow：scroll且没有设置position
子节点的Position：static|relative|时，子节点会滚动；
                   absolute|fixed时，子节点不会滚动
父节点设置overflow：scroll且设置了position
子节点的Position：static|relative|absolute时，子节点会滚动；
                      fixed时，子节点不会滚动

