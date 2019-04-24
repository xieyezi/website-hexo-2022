---
title: 将本地项目同步至github
tags:
  - git
  - GitHub
---
### 将你的项目同步至github
 注：此操作满足在你本机git已经配置到github环境下进行操作.
  先在项目根目录下：

  ```git
  git init
  ```

  打开你的github首页,新建一个repository.
  复制你刚刚新建的repository的地址,像这样: <!-- more -->
  ```
  https://github.com/xieyezi/your-Repository.git
  ```
  回到项目根目录,将你的本地项目和新建的repository联系起来:
  ```
  git remote add origin https://github.com/xieyezi/your-Repository.git

  ```

  在当前根目录下新建.gitignore文件
  将你不需要同步的文件和目录写到.gitignore,例如:

  ```
  .DS_Store
  node_modules/
  ```

  完成之后,到根目录:
  ```
  git add ./
  //当前目录下的有改动的文件全部加入,除开.gitignore备注的文件之外   
  ```

  ```
  git commit -m 'commit information'
  //这里将代码文件放入提交准备中， “commit information”字段填写自己的更新信息

  ```

  最后一步:

  ```
 git push --set-upstream origin master

  ```

  到你的github里面查看,成功提交!!!!


  奉上两张git操作命令图😄:

  ![git命令1.png](https://i.loli.net/2019/03/26/5c9a278b188be.png)


  ![git命令2.png](https://i.loli.net/2019/03/26/5c9a278b03086.png)
