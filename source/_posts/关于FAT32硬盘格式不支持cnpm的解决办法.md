---
title: 关于FAT32硬盘格式不支持cnpm的解决办法
---

最近学习`gulp` ，运行 `cnpm install gulp-less --save -dev` 的时候，报了如下错误：

![](https://sunchang.oss-cn-beijing.aliyuncs.com/image/1538374778411-6aced56f-f403-4e44-aa60-4941d8c82a99.png)
 然后改用 `npm` 安装，结果如下：
 
 ![](https://sunchang.oss-cn-beijing.aliyuncs.com/image/1538374852301-bc8c73d5-bcfa-4fb5-aa02-0d6b5d702cef.png)
 
 这是因为硬盘格式是 FAT32 格式的。解决办法如下：

可以使用 `npm` 去解决：`cnpm i --by=npm --no-bin-links`
或者：```npm i --registry=https://registry.npm.taobao.org --no-bin-links```。
在使用```--no-bin-links```时，注意```Maximum call stack size exceeded```的问题。
