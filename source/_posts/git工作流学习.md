---
title: git工作流学习
tags:
 - git
---

[git 的工作流程 纯干货](https://blog.csdn.net/zyw0713/article/details/80083431)
[git workflow 工作流](https://git.ninghao.net/gitflow-workflow.html)
#### 1. 有一次线上项目出bug了，需要把master上的项目拉取到本地
```
git checkout master
git pull
```
##### 然后在本地修改完bug，重新上传到master上
```
git add .
git commit -m '修改了bug'
git pull    #看看有没有新的提交
git push    #同步到远程仓库
```
##### 然后把master上的修改的内容同步到开发分支上，以防下次bug再出现
```
git checkout feature    #先切换到feature分支（开发分支）
git merge master    #把master分支合并到当前分支
```
###### 修改完毕


```
#Git创建Develop分支的命令
git checkout -b develop master
#将Develop分支发布到Master分支的命令
git checkout master
git merge --no-ff develop

```