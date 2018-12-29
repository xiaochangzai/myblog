---
title: 在html代码里添加关键字、描述
---
##### 添加关键字和描述
```
<meta name="keywords" content="SVG特效, 手机微信网站特效, css3动画, html5特效, 网页特效" />
<meta name="description" content="网页特效库-专注于HTML5、CSS3、js、jQuery、手机移动端等网页特效的手机与分享。特效库始终坚持：无会员、无积分、无限制的“三无原则”，所有的资源都免费提供广大童鞋下载学习和使用。" />
```
##### animation 一直转特效
```
@-webkit-keyframes rotate{
    0%{
        transform: rotate(0deg);
    }
    100%{
        transform: rotate(360deg);
    }
}
.bagua img{
    width: 548px;
    height: 548px;
    display: block;
    animation:rotate 20s linear 0s infinite;
}
```