---
title: React npm 环境搭建
---
#### 1. 安装淘宝镜像
```
$ npm install -g cnpm --registry=https://registry.npm.taobao.org
$ npm config set registry https://registry.npm.taobao.org
```
#### 2. 使用 create-react-app 快速构建 React 开发环境
```
$ cnpm install -g create-react-app
$ create-react-app my-app
$ cd my-app/
$ npm start
```
#### 3. 使用外部React组件
test.js
```
import React, { Component } from 'react';
class Test extends Component{
	render () {
		return (<div>1234</div>)
	}
}
export default Test;
```
index.js
```
import React from 'react';
import ReactDOM from 'react-dom';
import './index.css';
import App from './App';
import Test from './test';
import registerServiceWorker from './registerServiceWorker';

ReactDOM.render(<Test />, document.getElementById('root'));
registerServiceWorker();

```
