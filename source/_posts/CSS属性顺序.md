---
title: CSS属性顺序
---

##### 推荐样式书写顺序
1. Position
2. Box Model
3. Typographic
4. Visual

由于定位（positioning）可以从正常的文档流中移除元素，并且还能覆盖盒模型（box model）相关的样式，因此排在首位。盒模型决定了组件的尺寸和位置，因此排在第二位。

其他属性只是影响组件的内部（inside）或者是不影响前两组属性，因此排在后面:

```
.declaration-order {
    /* Positioning */
    position: absolute;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;
    z-index: 100;
    
    /* Box-model */
    display: block;
    float: right;
    width: 100px;
    height: 100px;
    
    /* Typography */
    font: normal 13px "Helvetica Neue", sans-serif;
    line-height: 1.5;
    color: #333;
    text-align: center;
    
    /* Visual */
    background-color: #f5f5f5;
    border: 1px solid #e5e5e5;
    border-radius: 3px;
    
    /* Misc */
    opacity: 1;
}
```

链接的样式请严格按照如下顺序添加：
```
a:link -> a:visited -> a:hover -> a:active（LoVeHAte）
```

[规则示例：](https://blog.csdn.net/SyKent/article/details/7862172)

```
.cl {
    display: ;
    visibility: ;
    float: ;
    clear: ;
    
    position: ;
    top: ;
    right: ;
    bottom: ;
    left: ;
    z-index: ;
   
    width: ;
    min-width: ;
    max-width: ;
    height: ;
    min-height: ;
    max-height: ;
    overflow: ;
 
    margin: ;
    margin-top: ;
    margin-right: ;
    margin-bottom: ;
    margin-left: ;
 
    padding: ;
    padding-top: ;
    padding-right: ;
    padding-bottom: ;
    padding-left: ;
 
    border-width: ;
    border-top-width: ;
    border-right-width: ;
    border-bottom-width: ;
    border-left-width: ;
 
    border-style: ;
    border-top-style: ;
    border-right-style: ;
    border-bottom-style: ;
    border-left-style: ;
 
    border-color: ;
    border-top-color: ;
    border-right-color: ;
    border-bottom-color: ;
    border-left-color: ;
 
    outline: ;
 
    list-style: ;
 
    table-layout: ;
    caption-side: ;
    border-collapse: ;
    border-spacing: ;
    empty-cells: ;
 
    font: ;
    font-family: ;
    font-size: ;
    line-height: ;
    font-weight: ;
    text-align: ;
    text-indent: ;
    text-transform: ;
    text-decoration: ;
    letter-spacing: ;
    word-spacing: ;
    white-space: ;
    vertical-align: ;
    color: ;
 
    background: ;
    background-color: ;
    background-image: ;
    background-repeat: ;
    background-position: ;
 
    opacity: ;
 
    cursor: ;
 
    content: ;
    quotes: ;
}

```
