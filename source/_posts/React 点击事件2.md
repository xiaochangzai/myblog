---
title: React 点击事件2
---
##### 1. this.state
```
var LikeButton = React.createClass({
  getInitialState:function(){
    return {
      like:false
    };
  },
  handleClick: function(event) {
    alert(556);
    this.setState({
      like:!this.state.like
    });
    alert(this.state.like);
  },
  render: function() {
    var text = this.state.liked ? 'like' : 'haven\'t liked';
    return (
      <p onClick={this.handleClick}>
        {this.state.like.toString()}
      </p>
      )
  }
});

ReactDOM.render(
  <LikeButton />,
  document.getElementById('example')
);
```
getInitialState 方法返回的是this.state，this.state 改变，DOM绑定的值也会变。

this.setState可以改变state的值。
##### 2. this.refs.ref
```
var HelloMessage = React.createClass({
    handleClick:function(){
        this.refs.myTextInput.focus();
        this.refs.myTextInput.value = "1234567";

    },
    render:function(){
        return	(
            <div>
                <input type="text" ref="myTextInput" />
                <input type="button" value="Focus the text input" onClick={this.handleClick} />
                </div>
        );
    }
});

ReactDOM.render(
    <HelloMessage name="join" />,
    document.getElementById("example")
)
```
给input加一个ref属性，方法中通过访问this.refs.ref名称来获取dom节点。