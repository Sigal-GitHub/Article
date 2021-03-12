## Nginx 1.18.0

#### 前置条件

`yum -y install gcc gcc-c++ automake make zlib-devel pcre-devel openssl-devel`

-   gcc 编译 C，C++其实只装这个就可以

-   gcc-c++ 编译 C++  下面mysql是需要这个的

-   automake/autoconf 生成 makefile

-   make 执行 makefile

-   zlib-devel 一个通用的无损数据压缩库

-   pcre-devel 重写，正则，都需要这个来提供

-   openssl && openssl-devel 到时能不能搭建 HTTPS 的网站，就看支不支持 openssl 了

#### 安装

1. 下载：`curl -o nginx-1.18.0.tar.gz http://nginx.org/download/nginx-1.18.0.tar.gz`

2. 解压：`tar xzf nginx-1.18.0.tar.gz`

3. 新建用户：`useradd -M -s /sbin/nologin nginx`

4. 检测

```
./configure --prefix=/usr/local/nginx \
--with-http_stub_status_module \
--with-http_ssl_module \
--with-http_random_index_module \
--with-http_sub_module
```

`--prefix=/usr/local/nginx`：安装目录

`--with-http_stub_status_module`：开启 status 检测

`--with-http_ssl_module`：操作 https

`--with-http_random_index_module`：随机首页

`--with-http_sub_module`：替换某些内容

> 反向代理，负载均衡等，默认开启了

5. 源码编译安装

`make && make install`

6. 简单配置

修改配置文件`/usr/local/nginx/conf/nginx.conf`

`user nobody;` => `user nginx;`

7. 启动`/usr/local/nginx/sbin/nginx`

8. 重载`/usr/local/nginx/sbin/nginx -s reload || stop`

> `/usr/local/nginx/sbin/nginx -t` 查看语法有没有问题

9. 开机启动`vim /etc/rc.local`最后添加`/usr/local/nginx/sbin/nginx`

## MySQL 8.0.18

#### 前置条件

`yum install -y cmake ncurses-devel libtirpc*`

准备：

[mysql](https://dev.mysql.com/downloads/mysql/) 8.0.18 版本

[boost](https://www.boost.org/users/history/) 1.70.0 版本

[rpcsvc-proto](https://github.com/thkukuk/rpcsvc-proto/releases) 1.4 版本

> 如果 boost 版本不对，下面./configure 的时候会报错，报错信息会提示你当前 mysql 版本所需要的 boost 是什么版本

#### 安装

##### 安装 boost

解压：`tar xzf boost_1_70_0.tar.gz`

拷贝：`mv boost_1_70_0 /usr/local/boost` PS:这个不需要编译

##### 安装 rpcsve

解压：`tar xzf rpcsvc-proto-1.4.tar.gz`

进入解压文件然后：`./configure`

最后：`make && make install`

##### 安装 mysql-boost

解压：`tar xzf mysql-boost-8.0.22.tar.gz`

进入解压文件编译：

```
cmake -DCMAKE_INSTALL_PREFIX=/usr/local/mysql \
-DWITH_BOOST=/usr/local/boost \
-DFORCE_INSOURCE_BUILD=1 \
-DDEFAULT_CHARSET=utf8 \
-DDEFAULT_COLLATION=utf8_general_ci
```

`安装的目录` boost 目录，就是上一步移动到的目录
`刚才是否编译过，现在单独编译` 设置编码
`` 设置字符集

安装：`make && make install`

##### 配置

以上正确安装完要是没有下面的配置文件，就自己配置上去

如果不知道配置文件放哪，可以使用：`/usr/local/mysql/bin/mysql --help | grep my.cnf` 查看

`/etc/my.cnf`

`/etc/my.cnf.d/client.cnf`

`/etc/my.cnf.d/mysql-default-authentication-plugin.cnf` 支持旧的加密模式

`/etc/my.cnf.d/mysql-server.cnf` skip-grant-tables 破解密码使用

```
/etc/my.cnf

[client-server]

!includedir /etc/my.cnf.d

/etc/my.cnf.d/client.cnf

[client]

[client-mariadb]

/etc/my.cnf.d/mysql-default-authentication-plugin.cnf

[mysqld]
default_authentication_plugin=mysql_native_password

/etc/my.cnf.d/mysql-server.cnf

[mysqld]

#skip-grant-tables
```

##### 新建用户

```
# 新建用户
useradd -M -s /sbin/nologin mysql
# 让用户对mysql文件夹拥有所有权限
setfacl -m u:mysql:rwx -R /usr/local/mysql
setfacl -m d:u:mysql:rwx -R /usr/local/mysql
```

##### 初始化数据库

`/usr/local/mysql/bin/mysqld --initialize --user=mysql`

执行完毕会给你一个默认密码，记下来

##### 启动服务

`/usr/local/mysql/bin/mysqld_safe --user=mysql &`

##### 开机启动

```
vim /etc/rc.local

# 在最后加上
/usr/local/mysql/bin/mysqld_safe --user=mysql &
```

##### 修改密码

进入到数据库:`/usr/local/mysql/bin/mysql -uroot -p系统给的默认密码`

`set password='xxx';` 就可以

##### 关闭 mysql

`pkill mysqld`

## 安装 PHP 7.3.1

#### 前置条件

`yum -y install autoconf freetype gd libpng libpng-devel libjpeg libxml2 libxml2-devel zlib curl curl-devel net-snmp-devel libjpeg-devel php-ldap openldap-devel openldap-clients freetype-devel gmp-devel libzip libzip-devel`

apt-get install -y autoconf libxml2-dev libsqlite3-dev \
libcurl4-openssl-dev libssl-dev libonig-dev libtidy-dev zlib1g-dev


#### 安装

##### 下载解压


[php](https://www.php.net/releases/)

`tar xzf php-7.3.1.tar.gz`

##### 编译

```
./configure --prefix=/usr/local/php \
--with-config-file-path=/usr/local/php/etc \
--with-mysqli \
--with-pdo-mysql \
--with-iconv-dir \
--with-freetype-dir \
--with-jpeg-dir \
--with-png-dir \
--with-curl \
--with-gd \
--with-gmp \
--with-zlib \
--with-xmlrpc \
--with-openssl \
--without-pear \
--with-snmp \
--with-gettext \
--with-mhash \
--with-libxml-dir=/usr \
--with-fpm-user=nginx \
--with-fpm-group=nginx \
--enable-xml \
--enable-fpm \
--enable-ftp \
--enable-bcmath \
--enable-soap \
--enable-shmop \
--enable-sysvsem \
--enable-sockets \
--enable-inline-optimization \
--enable-maintainer-zts \
--enable-mbregex \
--enable-mbstring \
--enable-pcntl \
--disable-fileinfo \
--disable-rpath \
--enable-libxml \
--enable-opcache \
--enable-mysqlnd
```

> ` ./configure --help | grep xmlrpc` 查找配置项

```
./configure --prefix=/usr/local/php \            # 安装路径
--with-config-file-path=/usr/local/php/etc \     # 配置文件路劲
--with-mysqli \                                  # MySQLi 支持
--with-pdo-mysql \                               # MySQL 的 PDO 支持
--with-iconv-dir \                               # XMLRPC-EPI 的 iconv 目录  --- 8没有
--with-freetype-dir \                            # GD 的 freetype 支持       --- 8没有
--with-jpeg-dir \                                # GD 的 jpeg支持            --- 8没有
--with-png-dir \                                 # GD 的 png支持             --- 8没有
--with-curl \                                    # cURL 支持
--with-gd \                                      # GD 库支持                 --- 8没有
--with-gmp \                                     # GNU MP支持
--with-zlib \                                    # ZLIB 支持，有版本要求，前置条件已安装
--with-xmlrpc \                                  # XMLRPC-EPI 支持           --- 8没有            
--with-openssl \                                 # openssl 支持
--without-pear \                                 # 不安装 PEAR               --- 8没有
--with-snmp \                                    # SNMP 支持
--with-gettext \                                 # GNU gettext 支持
--with-mhash \                                   # mhash 支持
--with-libxml-dir=/usr \                         # libxml 支持               --- 8没有
--with-fpm-user=nginx \                          # 配置 php-fpm 由谁运行
--with-fpm-group=nginx \                         # ↑
--enable-xml \
--enable-fpm \                                   # 启用 fpm SAPI
--enable-ftp \                                   # 启用 ftp
--enable-bcmath \                                # 启用 bc函数
--enable-soap \                                  # 启用 soap 支持
--enable-shmop \                                 # 启用 shmop 支持
--enable-sysvsem \                               # 启用  System V semaphore 支持
--enable-sockets \                               # 启用 sockets 支持
--enable-inline-optimization \                   # 启用内联优化
--enable-maintainer-zts \                        # 启用线程安全-仅限代码维护人员！！--- 8没有
--enable-mbregex \                               # 启用多字节正则表达式支持
--enable-mbstring \                              # 启用多字节字符串支持
--enable-pcntl \                                 # 启用pcntl支持（仅限CLI/CGI）
--disable-fileinfo \                             # 禁用 fileinfo 支持
--disable-rpath \                                # 禁用 rpath
--enable-libxml \                                # 启用 libxml               --- 8没有
--enable-opcache \                               # 启用 Zend OPcache 支持     --- 8没有
--enable-mysqlnd                                 # 显式启用 mysqlnd，在其他扩展需要时隐式启用
```

[相关的配置说明](https://www.php.net/manual/en/configure.about.php)

##### 安装

`make && make install`

##### 配置

将解压的 php 文件夹下的 php.ini-development 拷贝到/usr/local/php/etc 下:`cp /root/php-7.3.1/php.ini-development /usr/local/php/etc/php.ini`

将/usr/local/php/etc 下的 php-fpm.conf.default 改名：`mv php-fpm.conf.default php-fpm.conf`

将/usr/local/php/etc/php-fpm.d/下的www.conf.default改名：`mv www.conf.default www.conf`

> 编译的默认是走的端口，不是 socket，走的端口就能查找到端口号

##### 管理

/etc/local/php/sbin/

启动：`./php-fpm`

查看语法：`./php-fpm -t`

关闭：`pkill php-fpm`

重载：`pkill -USR2 php-fpm`

##### 开机启动

`vim /etc/rc.local` + `/etc/local/php/sbin/php-fpm`

> 要查看下 /etc/rc.local 是否有执行权限，不然开机启动不生效 `chmod +x /etc/rc.local`

## 配置

PHP-FPM 运行模式：

1. socket

/etc/local/php/etc/php-fpm.d/www.conf

listen = /usr/local/php/var/run/www.sock

> 单机的话socket会比较快

2. tcp

/etc/local/php/etc/php-fpm.d/www.conf

listen = 127.0.0.1:9000

Nginx 结合 PHP-FPM 的两种模式：

1. socket

fastcgi_pass unix:/usr/local/php/var/run/www.sock;

2. tcp

fastcgi_pass 127.0.0.1:9000;

Nginx 支持 PHP 程序：

```
# /usr/local/nginx/conf/nginx.conf

        location / {
            root   html;
            index  index.php index.html index.htm;
        }

        location ~ \.php$ {
            root           html;
            fastcgi_pass   127.0.0.1:9000;
            fastcgi_index  index.php;
            fastcgi_param  SCRIPT_FILENAME  $document_root$fastcgi_script_name;
            include        fastcgi_params;
        }
```

3. 改成socket模式

`/etc/local/php/etc/php-fpm.d/www.conf` 将 `listen = 127.0.0.1:9000` 改成 `listen = /usr/local/php/var/run/www.sock`

`/etc/local/nginx/conf/nginx.conf` 里的 `fastcgi_pass   127.0.0.1:9000;` 改成 `fastcgi_pass   unix:/usr/local/php/var/run/www.sock;`

如果要使用socket，就要下面这步，增加权限

给用户nginx php文件夹的权限：`setfacl -m u:nginx:rwx -R /usr/local/php` and `setfacl -m d:u:nginx:rwx -R /usr/local/php`

重启nginx:`/usr/local/nginx/sbin/nginx -s reload`

重启php


## 安装 PHP 8.0.1

#### 前置

`dnf install -y 等会走一遍再说`

`dnf --enablerepo=PowerTools install oniguruma-devel`

`dnf -y install libzip-devel`

#### 安装

```
./configure --prefix=/usr/local/php8 \
--with-config-file-path=/usr/local/php8/etc \
--enable-fpm \
--enable-mysqlnd \
--enable-opcache \
--enable-pcntl \
--enable-mbstring \
--enable-soap \
--enable-zip \
--enable-calendar \
--enable-bcmath \
--enable-exif \
--enable-ftp \
--enable-intl \
--with-mysqli \
--with-pdo-mysql \
--with-openssl \
--with-curl \
--with-gd \
--with-gettext \
--with-mhash \
--with-openssl \
--with-mcrypt \
--with-tidy \
--enable-wddx \
--with-xmlrpc \
--with-zlib
```

其他和php7一样

## 安装 Composer

#### 三部曲

> 将php添加到系统`ln -s /usr/local/php8/bin/php    /usr/local/bin/php`，不然composer用不了

进入到/usr/local/php/bin/目录下，不进也行

`php -r "copy('https://install.phpcomposer.com/installer', 'composer-setup.php');"`

`php composer-setup.php`

`php -r "unlink('composer-setup.php');"`

#### 添加到系统

`sudo mv composer.phar /usr/local/bin/composer`

#### 安装 Redis

#### 下载

#### 解压

#### 安装

进入到Redis目录，直接`make && make install`

## 其他

给php做一个system service 

`vim /lib/systemd/system/php7.3.1-fpm.service`

```
[Unit]
Description=The PHP 7.3 FastCGI Process Manager
Documentation=man:php-fpm7.3(7)
After=network.target

[Service]
Type=simple
PIDFile=/var/run/php7.3-fpm.pid
ExecStart=/usr/local/php/sbin/php-fpm --nodaemonize --fpm-config /usr/local/php/etc/php-fpm.conf
ExecReload=/bin/kill -USR2 $MAINPID

[Install]
WantedBy=multi-user.target
```
pkill php-fpm 干掉之前开启的php

用新的方式开启：`systemctl start php7.3.1-fpm.service`

以上只做了start和reload的配置


ps -ef | grep nginx 查看进程
ps aux | grep nginx 查看进程
pstree -u | grep nginx
netstat -tunpl | grep nginx 查看端口

> 如果要使用pstree 需要安装 psmisc.x86_64