---
title: 微信POST请求接收不到数据问题
---
用微信的wx.request发送POST请求，发现返回结果总是“请填写正确的用户名及密码”。后台查看一下，发现没有获取到值。于是就去网上查了一下。

`wx.request post` 的 `content-type` 默认为 `'application/json'`
这是错误的
要改成 `"content-type": "application/x-www-form-urlencoded"`
这样就好了。