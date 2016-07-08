---
layout: post
title: 事件-1
date: 2012-07-08
excerpt: 完整的阻止事件冒泡和事件默认行为代码
tags: [事件, 事件捕获, 事件冒泡]
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

## 生成句柄——阻止事件冒泡和事件默认行为
 
```javascript
var EventUtil = {
    addHandler:function(element,type,handler){
        if(element.addEventListener){
            element.addEventListener(type,handler,false);//非IE DOM2
        } else if(element.attachEvent){
            element.attachEvent("on"+type,handler);//IE DOM2
        } else {
            element["on"+type] = handler;//DOM0
        }
    },
    getEvent:function(event){
        return event ? event : window.event;
    },
    getTarget:function(event){
        return event.target || event.srcElement
    },
    preventDefault:function(event){
        if(event.preventDefault){
            event.preventDefault();
        } else {
            event.returnValue = false;
        }
    },
    removeHandler:function(element,type,handler){
        if(element.removeEventListner){
            element.removeEventListner(type,handler,false);
        } else if(element.detachEvent){
            element.detachEvent("on"+type,handler);
        } else {
            element["on"+type] = null;
        }
    },
    stopPropagation:function(event){
        if(event.stopPropagation) {
            event.stopPropagation();
        } else {
            event.cancelBubble = true;
        }
    }
};
```
