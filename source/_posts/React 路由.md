---
title: React 路由
tags:
  - javascript
  - react
---
[react-router-dom](http://reacttraining.cn/) 的使用方法

1. 先安装 react-router-dom
 在index.html 的目录下执行以下命令：
```
npm install react-router-dom -D
```
2. 导出路由配置
```
import React from "react";
import createBrowserHistory from 'history/createBrowserHistory'
import {
  BrowserRouter as Router,
  Route,
  Link
} from 'react-router-dom'

const BasicExample = () => (
  <Router>
    <div>
      <ul>
        <li><Link to="/">Home</Link></li>
        <li><Link to="/about">About</Link></li>
        <li><Link to="/topics">Topics</Link></li>
      </ul>

      <hr/>

      <Route exact path="/" component={Home}/>
      <Route path="/about" component={About}/>
    </div>
  </Router>
)

const Home = () => (
  <div>
    <h2>Home</h2>
  </div>
)

const About = () => (
  <div>
    <h2>About</h2>
  </div>
)

export default BasicExample
```
3. 使用路由
```
import React from 'react';
import ReactDOM from 'react-dom';
import './index.css';
import BasicExample from "./router" 
import registerServiceWorker from './registerServiceWorker';
import Home from "./components/home"
ReactDOM.render(<BasicExample />, document.getElementById('root'));
registerServiceWorker();

```