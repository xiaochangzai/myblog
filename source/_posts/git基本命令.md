---
title: git基本命令
---

## git基本命令
```
git status //查看当前git情况 参数-s
git init //git 初始化
git config --global user.name ''//设置用户名
git config --global user.email ''//设置email
git config --list //查看配置
git clone '仓库地址' //复制远程仓库到本地
git add file // 提交文件到临时仓库
git rm -cached '文件路径' 从临时仓库删除
git commit -m '描述内容' // 把临时仓库文件提交到本地仓库
git push -u origin master //提交到远程仓库
git pull origin master从远程仓库拉回来
git pull --rebase
git diff
git log 
git reset --hard 哈希值的前六位//回滚到之前的版本
git branch v2 //添加一个分支v2
git branch gh-pages //添加个可以直接浏览的分支 //浏览地址 sorry510.github.io/仓库名
git checkout gh-pages 
git push origin gh-pages
```
设置密码
```
git config --global user.password "xxxxxx(your password)"
```
设置远程仓库地址
```
git remote add origin https://sorry510:xp28344655@github.com/sorry510/cms
git remote -v 查看远程仓库地址
git remote set-url origin https://github.com/sorry510/cms 修改地址

git fetch origin php 更新远程上的php分支
```
提交到远程仓库设置权限
修改.git/config
remote "origin"]
	url = https://github.com/sorry510/test.git
改为
remote "origin"]
	url = https://用户名:密码@github.com/sorry510/test.git
	例如//url = https://sorry510:xp28344655@github.com/sorry510/test.git

## vi常用快捷键
正常模式
启动vim后默认位于正常模式。不论位于什么模式，按下<Esc>键(有时需要按两下）
都会进入正常模式。
ctrl+r 撤销 +u
插入模式
在正常模式中按下i, I, a, A等键（后面系列文章会详细介绍），会进入插入模式。

命令模式
在正常模式中，按下：（冒号）键，会进入命令模式。
:w   保存文件但不退出vi
:w file 将修改另外保存到file中，不退出vi
:w!   强制保存，不推出vi
:wq  保存文件并退出vi
:wq! 强制保存文件，并退出vi
:q  不保存文件，退出vi
:q! 不保存文件，强制退出vi
:e! 放弃所有修改，从上次保存文件开始再编辑

:set nu 显示行数

可视模式
在正常模式按下v, V, <Ctrl>+v，可以进入可视模式
```
ssh-keygen -t rsa -C "chen.jinlong@vmicloud.com"

①   cd ~/.ssh/    【如果没有对应的文件夹，则执行  mkdir  ./.ssh】
②  git config --global user.name "xb12369"
③  git config --global user.email "1234@qq.com"
④  ssh-keygen -t rsa -C "1234@qq.com"
```


合并分支
```
git merge --no-ff  分支

git checkout -b develop origin/develop
```