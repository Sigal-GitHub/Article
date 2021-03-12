## Nginx 基于域名的多站点配置

> Nginx 编译安装

`vim /usr/local/nginx/conf/nginx.conf`

在最后添加上以下代码

> 测试的时候一定要注意缓存。。。。坑货

```conf
# blog
server {
    listen       80;
    server_name  www.blog.com;
    root         /sigal/blog/public;
    # 日志配置
    access_log   logs/blog.access.log  main;
    index index.php index.html;

    # 配置支持php
    location ~ \.php$ {
        fastcgi_pass   127.0.0.1:9000;
        fastcgi_index  index.php;
        fastcgi_param  SCRIPT_FILENAME  $document_root$fastcgi_script_name;
        # 下面这个是让nginx支持pathinfo地址
        fastcgi_param  PATH_INFO $1;
        include        fastcgi_params;
    }

    # nginxstatus 模块
    location /nginxstatus {
        stub_status;
    }
}

# test
server {
    listen       80;
    server_name  www.test.com;
    root         /sigal/test;
    access_log   logs/test.access.log  main;
    index index.php index.html;

    location ~ \.php$ {
        fastcgi_pass   127.0.0.1:9000;
        fastcgi_index  index.php;
        fastcgi_param  SCRIPT_FILENAME  $document_root$fastcgi_script_name;
        # 下面这个是让nginx支持pathinfo地址
        fastcgi_param  PATH_INFO $1;
        include        fastcgi_params;
    }
    location /nginxstatus {
        stub_status;
    }
}
```

附 Nginx 根目录配置

```
server {
        listen       80;
        server_name  localhost;

        #charset koi8-r;

        #access_log  logs/host.access.log  main;

        location / {
            root   /sigal;
            index  index.html index.htm index.php;
        }

        location ~ \.php$ {
            root           /sigal;
            fastcgi_pass   127.0.0.1:9000;
            fastcgi_index  index.php;
            fastcgi_param  SCRIPT_FILENAME  $document_root$fastcgi_script_name;
            include        fastcgi_params;
        }

        #error_page  404              /404.html;

        # redirect server error pages to the static page /50x.html
        #
        error_page   500 502 503 504  /50x.html;
        location = /50x.html {
            root   html;
        }

        ...
        ...
        ...
}
```
