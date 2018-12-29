---
title: React-router config 的用法
tags:
  - javascript
  - react
---
React有好几种路由嵌套的用法。感觉都不好用。终于我找到已一个React Router Config 的方法
官方例子如下：
```
import React from 'react';
import ReactDom from 'react-dom';
import {
    BrowserRouter as Router,
    Route,
    Link
} from 'react-router-dom'

const Main = () => <h2>Main</h2>
const Sandwiches = () => <h2>Sandwiches</h2>

const Tacos = ({ routes }) => (
    <div>
        <h2>Tacos</h2>
        <ul>
            <li><Link to="/tacos/bus">Bus</Link></li>
            <li><Link to="/tacos/cart">Cart</Link></li>
        </ul>

        {routes.map((route, i) => (
            <RouteWithSubRoutes key={i} {...route} />
        ))}
    </div>
)

const Bus = () => <h3>Bus</h3>
const Cart = () => <h3>Cart</h3>

const routes = [
    {
        path: '/sandwiches',
        component: Sandwiches
    },
    {
        path: '/tacos',
        component: Tacos,
        routes: [
            {
                path: '/tacos/bus',
                component: Bus
            },
            {
                path: '/tacos/cart',
                component: Cart
            }
        ]
    }
]

const RouteWithSubRoutes = (route) => (
    <Route path={route.path} render={props => (
        // pass the sub-routes down to keep nesting
        <route.component {...props} routes={route.routes} />
    )} />
)

const RouteConfigExample = () => (
    <Router>
        <div>
            <ul>
                <li><Link to="/tacos">Tacos</Link></li>
                <li><Link to="/sandwiches">Sandwiches</Link></li>
            </ul>

            {routes.map((route, i) => (
                <RouteWithSubRoutes key={i} {...route} />
            ))}
        </div>
    </Router>
)

export default RouteConfigExample;
```
主要思想是：把配置的页面配置到一个叫 routes 的变量里。模式是 path和component 对应的。

RouteWithSubRoutes 的作用是循环遍历 routes 函数，将对应的组件渲染到对应的位置里。
