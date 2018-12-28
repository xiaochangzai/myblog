---
title: JQuery源码之自调用匿名函数
---
JQuery的自调用匿名函数如下：
```
(function(window,undefind){
    var jQuery = ...
    //...
    window.jQuery = window.$ = jQuery;
})(window)
```
##### 1. 为什么要创建这样一个自调用匿名函数？
目的是创建一个特殊的函数作用域，防止 ==命名冲突==
##### 2. 为什么要为自调用匿名函数设置参数window，并传入window对象？
是为了让window变成局部变量。这样在jQuery访问window对象时，不用把作用域链回退到顶层作用域。
##### 3. 为什么要为自调用匿名函数设置参数undefined？
特殊值undefined是window对象的一个属性。执行以下语句会弹出 true:
```
alert("undefined" in window)
```
通过把参数undefined作为局部变量使用，但是又不传入任何值，可以缩短查找undefined时的作用域链

另外，通过这种方式可以确保undefined的值是undefined，因为undefined有可能会辈重写为新的值。
```
undefined = "now its defined";
alert(undefined);
```