---
title: React 里面如何使用jQuery 和 jQuery 的插件
---
如果直接 import $ from './jquery.min' 引入的话，会报错。
webpack 下使用jQuery ，要先安装。
在index.js 的目录下，执行以下命令：
```
npm install jquery -D
```
在js里引入jquery 
```
import $ from 'jquery'
```
在webpack react项目里怎么使用jQuery的插件？

修改组建源码，将方法暴露出去。
```
function reflection($) {

	$.fn.reflect = function(options) {
		options = $.extend({
			height: 1/3,
			opacity: 0.5
		}, options);

		return this.unreflect().each(function() {
```
将方法暴露出去

```

	$.fn.unreflect = function() {
		return this.unbind("load").each(function() {
			var img = this, reflected = $(this).data("reflected"), wrapper;

			if (reflected !== undefined) {
				wrapper = img.parentNode;
				img.className = wrapper.className;
				img.style.cssText = reflected;
				$(img).data("reflected", null);
				wrapper.parentNode.replaceChild(img, wrapper);
			}
		});
	}

}

export default reflection;
```
在js中引用
```
import $ from 'jquery';
import cloud9carousel from './../js/jquery.cloud9carousel';
import reflection from './../js/jquery.reflection';
//初始化组件
cloud9carousel($);
reflection($);
```