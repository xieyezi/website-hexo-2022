---
title: Mac安装Vue.js devtools插件无法使用的解决方法
tags:
  - Vue
  - Chrome
  - 插件
---

### Mac安装Vue.js devtools插件无法使用？
  在Mac os的谷歌浏览器里面安装插件[vue.js devtools](https://chrome.google.com/webstore/detail/vuejs-devtools/nhdogjmejiglipccpnnnanhbledajbpd)之后,发现启动vue项目之后,我们无法使用的情况：
  <!-- more -->
  ![无法使用](http://wx4.sinaimg.cn/mw690/89296167gy1fukn6l5256j21kw0zk7j1.jpg)

  可以有如下解决方法：
  在Mac finder前往Chrome安装插件的文件夹：
  ```
   ~/Library/Application Support/Google/Chrome/Default/Extensions
  ```
  找到devtools的安装文件夹：
  ![文件夹位置](http://wx4.sinaimg.cn/mw690/89296167gy1fuknal6mp8j216s0o80z1.jpg)

  打开此文件夹里面的manifest.json文件,作出如下修改：
  ![修改](http://wx1.sinaimg.cn/mw690/89296167gy1fuknf0zp93j21kw0vudtb.jpg)

  然后重启vue项目,进入到Chrome里面,就可以正常使用了.
  ![正常使用](http://wx4.sinaimg.cn/mw690/89296167gy1fuknh431mgj21kw0zkh0l.jpg)
