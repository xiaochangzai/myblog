---
title: 判断手机系统是ios 还是Android
tags:
  - javascript
---
## 判断手机系统是ios 还是Android
```
var u = navigator.userAgent
var isAndroid = u.indexOf('Android') > -1 || u.indexOf('Adr') > -1; //android终端
var isiOS = !!u.match(/\(i[^;]+;( U;)? CPU.+Mac OS X/); //ios终端
```