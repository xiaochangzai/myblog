---
title: CSS笔记
tags:
  - css
---
#### 1. 自定义字体
有的时候系统自带的字体并不能满足我们的字体。有时候我们会在网页上放一些比较炫酷的字体。但是怎么在网页上显示呢？

---
 把使用的字体下载下来，然后找一个字体转化的官网，生成不同所需要的字体格式。推荐一个[字客](https://www.fontke.com/tool/convfont/)。
 把生成的字体下载下来。在css文件里写上如下代码：
 ```
 @font-face {
	font-family: 'Monotype Corsiva';
	src: url('../font/Monotype Corsiva.eot'); /* IE9 Compat Modes */
	src: url('../font/Monotype Corsiva.eot?#iefix') format('embedded-opentype'), /* IE6-IE8 */
         url('../font/Monotype Corsiva.woff') format('woff'), /* Modern Browsers */
         url('../font/Monotype Corsiva.ttf')  format('truetype'), /* Safari, Android, iOS */
         url('../font/Monotype Corsiva.svg#Monotype Corsiva') format('svg'); /* Legacy iOS */
   }
   ```
   其中 ==../font/Monotype Corsiva.eot== 是我的字体文件路径。
   ==font-family== 写的是字体名称。
   ##### 2. 自定义滚动条样式
   有时候我不不太喜欢浏览器自带的滚动条样式，大大的影响了网页的美观。那么怎么去自定义浏览器滚动条样式呢？
   ###### 1. Chrom 浏览器
   ```
   ::-webkit-scrollbar
{
    width: 6px;
    height: 6px;
}
::-webkit-scrollbar-track-piece
{
    background-color: #CCCCCC;
    -webkit-border-radius: 6px;
}
::-webkit-scrollbar-thumb:vertical
{
    height: 5px;
    background-color: #999999;
    -webkit-border-radius: 6px;
}
::-webkit-scrollbar-thumb:horizontal
{
    width: 5px;
    background-color: #CCCCCC;
    -webkit-border-radius: 6px;
}
   ```
###### 2. IE 浏览器
   ```
   /*滚动条*/
body{overflow-y:auto;overflow-x:hidden;height:580px;
scrollbar-arrow-color:#302D30; /*三角箭头的颜色*/
scrollbar-face-color:#000; /*立体滚动条的颜色（包括箭头部分的背景色）*/
scrollbar-3dlight-color:#302D30; /*立体滚动条亮边的颜色*/
scrollbar-highlight-color:#302D30; /*滚动条的高亮颜色（左阴影？）*/
scrollbar-shadow-color:#302D30; /*立体滚动条阴影的颜色*/
scrollbar-darkshadow-color:#302D30; /*立体滚动条外阴影的颜色*/
scrollbar-track-color:#302D30; /*立体滚动条背景颜色*/
scrollbar-base-color:#302D30; /*滚动条的基色*/}
   
   ```
   ---
##### 3. CSS3 box-flex 属性 
子元素平分父元素的宽度：

定义两个可伸缩的 p 元素。如果父元素的总宽度是 300 像素，则 #p1 的宽度是 100 像素，而 #p2 的宽度是 200 像素:
```
#p1
{
-moz-box-flex:1.0; /* Firefox */
-webkit-box-flex:1.0; /* Safari 和 Chrome */
box-flex:1.0;
border:1px solid red;
}

#p2
{
-moz-box-flex:2.0; /* Firefox */
-webkit-box-flex:2.0; /* Safari 和 Chrome */
box-flex:2.0;
border:1px solid blue;
}
```
 ---
 ##### 4. 只显示三行文本，多余的显示...
 ```
 display: -webkit-box;
-webkit-line-clamp: 3;
-webkit-box-orient: vertical;
overflow: hidden;
 ```
 
 [React.child.children 的用法 笔记](http://note.youdao.com/noteshare?id=cd68645a8d2bcc02a0f68b426dbcd729)