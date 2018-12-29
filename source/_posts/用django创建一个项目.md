---
title: 用django创建一个项目
tags:
  - python
---
首先你得安装好python和django，然后配置好环境变量，安装python就不说了，从配置环境变量开始

##### 1.配置环境变量

在我的电脑处点击右键，或者打开 控制面板\系统和安全\系统 ->

左边导航栏的“高级系统设置”->环境变量 -->然后你会看到下面这个界面

![](https://sunchang.oss-cn-beijing.aliyuncs.com/image/828578-20170103195539128-1894247265.png)
-> 点击这个path，然后点编辑

然后找到C:\Python27文件夹，将这个文件夹添加进去。

##### 2.安装django

打开cmd，执行 pip install django 或者 把![](https://sunchang.oss-cn-beijing.aliyuncs.com/image/828578-20170103195951191-1293610516.png)
这个包下载下来，然后解压之后打开，是这样的

![](https://sunchang.oss-cn-beijing.aliyuncs.com/image/828578-20170103200123878-1846022323.png)
->打开cmd ,打开这个文件夹,执行 `python setup.py install`
等着就行了

##### 3. 检验django是否安装成功
`
import django
`
如果这句话不报错的话，就没什么问题了。

##### 4. 配置django环境变质量。

还是像刚才那样打开环境变量里的path，这次添加的路径是：![](https://sunchang.oss-cn-beijing.aliyuncs.com/image/828578-20170103200738237-1012230503.png)

5. 用django创建项目

打开cmd，并进入你的工作空间，执行命令：
![](https://sunchang.oss-cn-beijing.aliyuncs.com/image/828578-20170103200951722-394835961.png)

如果你看到的是下面这样的话，
![](https://sunchang.oss-cn-beijing.aliyuncs.com/image/828578-20170103201030722-218731608.png)

这可能是版本问题导致的，你可以执行
![](https://sunchang.oss-cn-beijing.aliyuncs.com/image/828578-20170103201118253-933553388.png)

如果没有任何提示，就是成功了。如果还报错，就得检查检查了。

执行成功之后，在你的工作空间目录会有两层website文件夹，进入到两层website文件夹下，会有以下几个文件

![](https://sunchang.oss-cn-beijing.aliyuncs.com/image/828578-20170103202329550-1021831256.png)
##### 6. 创建djangoapp
进入website目录下，执行 `admin.py startapp blog` 或者 `admin startapp blog`
![](https://sunchang.oss-cn-beijing.aliyuncs.com/image/828578-20170103202532987-734281570.png)

这里还是没有什么提示，这时候在你的website目录下就多了一个blog文件夹，和一个自带的sqlite3数据库。
![](https://sunchang.oss-cn-beijing.aliyuncs.com/image/828578-20170103202638644-219210958.png)

##### 7.修改 urls.py 和 views.py 

打开 views.py 加入测试代码如下：
![](https://sunchang.oss-cn-beijing.aliyuncs.com/image/828578-20170103203359566-894259538.png)

其实就是定义了一个函数，然后返回一个字符串。
打开 urls.py ，添加一句话
`url(r'^blog/index/$',blog.views.index,name='index')`

![](https://sunchang.oss-cn-beijing.aliyuncs.com/image/828578-20170103203233878-325335233.png)

 ##### 8. 开启服务器
在website目录下运行命令:
![](https://sunchang.oss-cn-beijing.aliyuncs.com/image/828578-20170103203550237-1673257793.png)

或者 `manage.py runserver` ，版本不一样导致
如果你看到下面这个界面，就代表服务器开启成功了
![](https://sunchang.oss-cn-beijing.aliyuncs.com/image/828578-20170103203725644-2085813319.png)

你可以打开浏览器，输入 `127.0.0.0:8000 `

这个地址，查看结果。