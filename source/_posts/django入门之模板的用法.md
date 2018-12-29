---
title: django入门之模板的用法
tags:
  python
tit: '{{title}}'
var: '{{需要输出的变量}}'
---
##### 1.为什么要使用模板？

  看下以前的代码

```
#-*- coding:utf-8 -*-
from django.shortcuts import render
from django.http import HttpResponse
# Create your views here.

def index(request):
    return HttpResponse(t.render("<h1>Hello,World!</h1>"))
```
 这里是把页面以字符串的形式返回。如果页面有点多，页面内容有点多的话，就得返回写好的html网页了。

##### 2. 使用写好的网页。

首先得引入django的模板加载器，代码如下：
```
from django.template import loader,Context
```
然后要创建一个加载器，和一个返回动态数据的Context对象，最后返回个模板。
```
 def index(request):
     t = loader.get_template("index.html")
     c = Context({"title":"django模板添加动态数据"})
     return HttpResponse(t.render(c))
```
##### 3. 创建模板。然后在你的app文件夹下，也就是和你的views.py同级目录下新建个文件夹templates，并在templates文件夹下创建个html文件，这里叫index.html

##### 4. 编辑模板。打开index.html，随意输入点html代码
```
<html>
    <body>
      <h1>Hello,django!</h1>
    </body>
</html>
```
 最后你可以运行服务器，在cmd中打开项目目录，输入命令：`manage.py runserver` 或者 `python manage.py runserver`，然后你会看到如下界面：
![](https://sunchang.oss-cn-beijing.aliyuncs.com/image/828578-20170104205957675-468248005.png)

你可以打开你的浏览器，在导航栏中输入地址: `http://127.0.0.1:8000/blog/index` ，`blog`是指你的应用名，我的是`blog`。然后你就可以看到你的`index.html`了。

##### 5. 在模板里获取动态数据
打开`index.html`的编辑界面，在需要输出的地方加上`{{var}}`。比如我上面的代码里传入了`title`，在`html`里只要写`{{tit}}`就行了
```
<title>Hello,{{title}}</title>
```