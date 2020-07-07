## 禁止IOS文字变链接处理办法

---

在测试中发现iPad上的Safari总会把长串数字识别为电话号码，文字变成蓝色，点击还会弹出菜单添加到通讯录。

别的地方倒也罢了，如果在用户名中出现数字（手机注册新浪微博的话用户名就是“手机用户xxxxxxxx”），版式会很恶心。

经过测试在a标签中的长串数字不会识别为电话，于是给出现用户名但没有链接的地方嵌套一个无动作的a标签，临时解决了这个问题。

但是这样增加了额外的标签，代码的语义性变得很差，而且对大段文字不能用这个方法。

今天无意中撞进Safari的官网，发现了safari有个私有meta属性可以解决这个问题：

```html
<meta name="format-detection" content="telephone=no" />
```

官网的说明如下： 

```
How do I disable automatic detection of phone numbers in webpages? In Safari on iPhone, phone numbers are automatically detected and transformed into links that dial the phone number when tapped. If you have strings of numbers in your webpage that should not be automatically detected as phone numbers, you can choose to disable this feature on the entire page by adding the meta tag shown in Listing 12.
```

