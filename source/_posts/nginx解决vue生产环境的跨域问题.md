---
title: nginx解决vue项目在生产环境的跨域问题
tags:
  - Vue
  - JS
---
### 问题由来

   我最近做项目,我在前端使用了vue开发,使用vue-cli3搭建项目,在开发的过程中,在开发环境中遇到了跨域的问题,我在vue.config.js配置了proxy,然后解决了问题.但是项目总归要上线,我运行了`npm run build`之后生成了dist文件夹.由于我的服务器容器是tomcat,所以刚开始我在tomcat的webapps文件夹下面新建了一个项目名vuemusic,然后将dist文件夹下面的所有东西拷贝至webapps下面,然后去conf文件夹配置了server.xml,然后我很开心的打开浏览器,输入地址`www.xieyezi.com/vuemusic`进行访问,这个时候出现一个问题,请求不到后端数据.
   <!-- more -->

### 问题的分析

   我认真的想了一下,这个项目是前后端分离的项目,我将前端代码放置在tomcat的webapps下面,我的tomcat配置的是80端口,但是我的后端服务采用的是node.js,然后走的是3000端口,但是去访问网站的时候会默认访问同源位置,所以出现了端口跨域的问题.

### 解决的思路

   找到了问题,那我们就可以思考一下怎么去解决问题.
   有两种解决思路:
   * 一是在后端服务模块设置允许跨域,但是我对node.js不是特别熟悉,所以放弃了这个方法.
   * 二是找到一个可以实现跨域的代理方法.我在网上搜索,大家都推荐使用nginx去实现生产环境跨域问题.      




### 解决方法

  所以就使用nginx来解决跨域问题.
  去[nginx官网]下载安装好nginx.
  到ngix根目录点击nginx.exe启动ngix服务器.
  然后将刚刚在webapps文件夹下新建的vumusic文件夹拷贝至nginx目录下的html目录下(如图):

  ![QQ20181106-180932@2x.png](https://i.loli.net/2018/11/06/5be168751fc06.png)

  打开conf文件夹下面的nginx.conf进行编辑:
     ```js
     # 设置vue项目
      server {
          listen  8080;
          server_name www.xieyezi.com;

          #charset koi8-r;
          #access_log  logs/host.access.log  main;
          location / {
              root   html/vuemusic;
              index  index.html index.htm;
          }

  	      #设置代理转发
          location /api/ {
            proxy_pass  http://localhost:3000/;
          }
          #error_page  404              /404.html;

          # redirect server error pages to the static page /50x.html
          #
          error_page   500 502 503 504  /50x.html;
          location = /50x.html {
              root   html;
          }

          # proxy the PHP scripts to Apache listening on 127.0.0.1:80
          #
          #location ~ \.php$ {
          #    proxy_pass   http://127.0.0.1;
          #}

          # pass the PHP scripts to FastCGI server listening on 127.0.0.1:9000
          #
          #location ~ \.php$ {
          #    root           html;
          #    fastcgi_pass   127.0.0.1:9000;
          #    fastcgi_index  index.php;
          #    fastcgi_param  SCRIPT_FILENAME  /scripts$fastcgi_script_name;
          #    include        fastcgi_params;
          #}

          # deny access to .htaccess files, if Apache's document root
          # concurs with nginx's one
          #
          #location ~ /\.ht {
          #    deny  all;
          #}
      }
     ```













   在上面的代码中,将`server_name`设置为你的域名,root设置为你的项目根目录.因为我将vumusic拷贝至html下面了,所以这样设置:`html/vuemusic;`
   在上面代码中,哪里实现了代理转发呢？

   ```
     #设置代理转发
     location /api/ {
       proxy_pass  http://localhost:3000/;
     }
   ```

   意思就是说,在当前这个项目下,所有的`/api/`的请求,都会被代理至`http://localhost:3000/`下面.
   在nginx根目录下打开命令行窗口输入:
   ```
     nginx -s reload
   ```

   重新访问项目,就会发现,跨域问题成功解决.
