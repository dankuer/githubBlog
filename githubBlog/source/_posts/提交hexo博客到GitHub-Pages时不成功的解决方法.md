---
title: 提交hexo博客到GitHub Pages时不成功的解决方法
date: 2016-08-01 23:35:00
tags: git hexo
comments: true
---
### 由来
最近正在自己研究基于**Nodejs** 的简单 **Blog** 实现，也算是练练手吧。
今天突发奇想，看看 **GitHub** 上边比较火的博客系统有哪些，于是就找到了火火的 **hexo** 博客
心血来潮，按照官方的教程进行了配置，准备架设到 **GitHub** 提供的 **GitHub Pages** 上边。
[官方配置及部署教程见这里](https://hexo.io/zh-cn/docs/deployment.html#Git)
<!-- more -->
### 问题
官方文档还是比较清楚了，配置过程闲话不表。修改了_config.ym 文件下边的**deploy** 部分如下
``` javascript
deploy:
  type:git
  repo:https://github.com/dankuer/dankuer.github.io.git
```

安装了官方要求的针对 **git** 的部署插件
``` javascript
npm install hexo-deployer-git --save
```

然后使用部署命令进行部署
``` javascript
hexo d
```
命令一闪而过，没有任何错误，但是就是未能成功提交！！！
仔细在网上搜查了一通，终于发现问题所在！

### 解决方法
原来在 **hexo** 中，默认配置项的 **key** 冒号之后要加一个空格，不然无法识别！
做出如下修改
```diff
deploy:
-   type:git
+   type: git
-   repo:https://github.com/dankuer/dankuer.github.io.git
+   repo: https://github.com/dankuer/dankuer.github.io.git
```

### 心得体会
小小的一个空格，却足足折腾了快一晚上。虽然最后终于解决，但也给出了提示。
1. 认真阅读官方文档，即使那些没有明确标识的地方，比如官方文档的示例中就存在一个空格，结果后边自己写的时候没有完全按照官方文档的格式，随意地就去掉了空格。
2. 善于求助搜索引擎
