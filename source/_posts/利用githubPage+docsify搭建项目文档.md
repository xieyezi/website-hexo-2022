---
title: 利用githubPage+docsify搭建项目文档
tags:
  - Github
  - docsify
---

### 前言

  这段时间从上海离职回到重庆了,所以一直没有更新我的博客和GitHub,为自己的自律打负分.我可以说最近事情繁多,但是这也不能成为我懒惰的理由.

### 需求

  有时候,我们做了一个项目,我们自己能看懂项目,但是我们需要给他人提供API文档,但是我们又没有多余的服务器和域名,这个时候咋办？那么我们就可以用到GitHubPage+[docsify](https://docsify.js.org/#/)搭建我们的项目文档.<!-- more -->
### 步骤

  进入你项目的根目录,在命令行输入以下命令创建项目文档目录(docs):

  ```
  docsify init ./docs
  ```
  这个命令执行完成之后,你会看见你的项目文档多了一个docs目录.你的项目文档就可以写在这个目录里面.
  进入这个目录会看见以下文件:
  - index.html 入口文件
  - README.md 会做为主页内容渲染
  - .nojekyll 用于阻止 GitHub Pages 会忽略掉下划线开头的文件
  - 直接编辑 docs/README.md 就能更新网站内容,当然也可以写多个页面.




  在README.md写你的项目文档就可以了.

  预览文档:
  ```
  docsify serve docs
  ```
  如果你觉得构建得差不多了,你就可以将它放置到GitHub上面.

  首先你得保证你的项目已经托管到GitHub上面.
  推荐直接将文档放在 docs/ 目录下,在设置页面开启 GitHub Pages 功能并选择 master branch /docs folder 选项：
  在GitHub里面,点击进入项目:

  ![QQ20181211-084924@2x.png](https://i.loli.net/2018/12/11/5c0f09dc82ac1.png)

  设置master branch /docs folder:

  ![QQ20181211-084951@2x.png](https://i.loli.net/2018/12/11/5c0f0a0978667.png)

  完成之后,它会提示你的文档目录已经生成,并且已经可以通过GitHub的子域名进行访问了.
  比如我的音乐[webApp项目文档](https://xieyezi.github.io/myMusic/#/).
