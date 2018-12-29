---
title: React 点击事件怎么传参
tags:
  - javascript
  - react
---

先看一下代码：

```
 React.Children.map(this.state.hours,function(item,index){
    return <li key={index} index={index} onClick={this.clickItem.bind(this,index)}>{item}</li>
}.bind(this))
```
#### map里的函数为什么要执行 bind(this)?
因为这个函数的this是指向window的，要把当前作用域传入，是this指向React的this。
####  onClick={this.clickItem(index)} 这样写会怎么样？

会在加载的时候执行。点击的时候并不执行。
#### 如何才能正确的传入参数呢？
```
<li key={index} index={index} onClick={this.clickItem.bind(this,index)}>{item}</li>
```
把参数通过bind函数传进去。