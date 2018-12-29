---
title: 关于数组遍历dom没有key导致的错误 react&npm 中的state
tags:
  - javascript
  - react
  - npm
---
##### React 报错 Warning: Each child in an array or iterator should have a unique "key" prop.
这个是和react的dom-diff算法相关的。react对dom做遍历的时候，会根据data-reactid生成虚拟dom树。如果你没有手动的添加unique constant key的话，react是无法记录你的dom操作的。它只会在重新渲染的时候，继续使用相应dom数组的序数号(就是array[index]这种)来比对dom树。

解决办法：
```
bannerArr.map(function (src,index) {
    // body...
    return (
        <div className="banner-box" key={index}>
            <img src={src} />
        </div>
        )
})
```
在遍历的dom节点加个key属性
#### 2. react&npm 中的this.state
```
constructor(props) {
    super(props);
    // this.onClickButton = this.onClickButton.bind(this);
    this.state = {
        left: 0,
        curr:0
    };
}

```
html代码
```
<span className="prev" onClick={this.prev.bind(this)}></span>
<span className="next" onClick={this.next.bind(this)}></span>
```