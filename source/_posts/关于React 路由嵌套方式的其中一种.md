---
title: 关于React 路由嵌套方式的其中一种
tags:
  - javascript
  - react
---
现在react router v4 的路由嵌套改成这样子了。和之前的大不一样。
不过也不是也别麻烦。
代码如下：
```
import React from 'react'
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
      <Route path="/topics" component={Topics}/>
    </div>
  </Router>
)

const Home = () => (
  <div>
    <h2>Home</h2>
  </div>
)
const Bus =()=>(<h2>Bus</h2>);
const Car =({match})=>(<h2>Car {match.params.message}</h2>);
const About = ({match}) => (
  <div>
    <h2>About</h2>
    <Link to={`${match.url}/car/123`}>Car</Link>
    <Link to={`${match.url}/bus`}>Bus</Link>
    <Route path={`${match.url}/car/:message`} component={Car} />
    <Route path={`${match.url}/bus`} component={Bus} />
    <Route exact path={match.url} component={()=>(<h2>请选择一辆车</h2>)} />

  </div>
)

const Topics = ({ match }) => (
  <div>
    <h2>Topics</h2>
    <ul>
      <li>
        <Link to={`${match.url}/rendering`}>
          Rendering with React
        </Link>
      </li>
      <li>
        <Link to={`${match.url}/components`}>
          Components
        </Link>
      </li>
      <li>
        <Link to={`${match.url}/props-v-state`}>
          Props v. State
        </Link>
      </li>
    </ul>

    <Route path={`${match.url}/:topicId`} component={Topic}/>
    <Route exact path={match.url} render={() => (
      <h3>Please select a topic.</h3>
    )}/>
  </div>
)

const Topic = ({ match }) => (
  <div>
    <h3>{match.params.topicId}</h3>
  </div>
)


export default BasicExample
```
和之前相比，Router 标签里多了一个叫match 的东西。通过match来获取当前组件的路径。
也是通过match 来获取参数。
获取参数代码如下：
```

const Topic = ({ match }) => (
  <div>
    <h3>{match.params.topicId}</h3>
  </div>
)
```
传入的时候以以下方式传入：
```
<Link to={`${match.url}/props-v-state`}>
          Props v. State
        </Link>
<Link to={`${match.url}/components`}>
          Components
        </Link>
<Route path={`${match.url}/:topicId`} component={Topic}/>
```
但是如果组件是通过Component 建立的,可以通过 this.props.match.params 获取参数。代码如下：
```
<div>
    <div className="subject-tit">
       {this.props.match.params.message}
        <a href="#">（查看原因）</a>
    </div>
    <div className="img-box"></div>
    <input type="button" value="返回首页"/>
</div>
```
