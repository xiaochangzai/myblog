---
title: only-child 用法 React click事件
---
今天遇到了一个需求：
 
案例列表有的会有两个图片，有的有一个图片。两个图片中间又要留出空隙。一般做法都是用js解决。而我的想法是能用css解决的，就不用js

我的思路是：only-child 处理有一个图片的情况。
nth-child(2) 处理有两个图片下的间距问题。代码如下：
```
#case-list .case-item .imgs img{
	width: 300px;
	height: 300px;
	display: block;
	float: left;
}
#case-list .case-item .imgs img:nth-child(2){
	margin-left: 16px;
}
#case-list .case-item .imgs img:only-child{
	width: 610px;
}
```
所有主流浏览器均支持 :only-child 选择器，除了 IE8 及更早的版本。


[JQuery源码之自调用匿名函数](http://note.youdao.com/noteshare?id=50abee06b14c1ff465032d07289ccaa0)

---
React 添加事件
```
_init_ = (function(window,undefined){
	return {
		getWidthOfClient:function(){
			var width = document.body.clientWidth;
			var container = document.getElementById("container");
			//container.style.width = width + "px";
		},
		bindBannerClickHandeler(){
			var pos_left = 0;
			var Banner = React.createClass({
				prevHandle:function(){
					pos_left = -300;
				},
				render:function(){
					return <div>
						<img className="logo" src="img/logo.png" ></img>
						<div className="img-list" style={{left:pos_left}}>
							<div className="banner-box">
								<img src="img/banner2.png"></img>
								</div>

								<div className="banner-box">
									<img src="img/banner2.png"></img>
									</div>

									<div className="banner-box">
										<img src="img/banner2.png"></img>
										</div>

									</div>

									<div className="modal-box">
										<div className="width-base height-max auto">
											<span className="prev" onClick={this.prevHandle}></span>
											<span className="next"></span>
										</div>
									</div>
					</div>
				}
			});

			ReactDOM.render(<Banner />,document.getElementById("banner"))
		}
	}
})(window)
```