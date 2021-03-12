> 6.5 -> 7 -> 8 更新

## CentOS8 最小安装

略

timedatectl 查看时区；一般安装界面选了上海，就没问题

cat /etc/os-release

cat /etc/redhat-release

systemctl status chrony  => timedatectl set-ntp true 修改时间

## 更新

`yum update && yum upgrade`

## 开启网卡

`ip addr` 查看是否开启网卡

`CentOS7`中支持`network.service`与`NetworkManager（NM）`，并同时启用了

`CentOS8`弃用了`network.service`，采用`NetworkManager（NM）`为网卡启用命令，当然`CentOS8`也可以安装`network.service`作为网卡服务，可以通过`yum install network-scripts`来安装传统的`network.service`，不过`redhat`说了，在下一个 RHEL 的大版本里将彻底废除，因此不建议使用`network.service`。

#### 一次开启，重启失效

开启：`nmcli c(connection) up ens33`

关闭：`nmcli c(connection) down ens33`

#### 永久开启

修改 `/etc/sysconfig/network-scripts/ifcfg-ens33` 配置文件

将里面的 NOBOOT=no 改成 yes

> 远程链接不到的话就`systemctl status sshd`查看一下 sshd 的状态

## 更改主机名

查看`echo $HOSTNAME`

1. hostnamectl

查看：`hostnamectl`

修改：`hostnamectl set-hostname xxxxx`

2. nmcli

查看：`nmcli g hostname`

修改：`nmcli g hostname xxxx`

## 关闭防火墙

CentOS 8 最小安装默认防火墙是关闭的

查看：`systemctl status firewalld.service`

开启：`systemctl start firewalld.service`

关闭：`systemctl stop firewalld.service`

禁用：`systemctl disable firewalld.service`

启用：`systemctl enable firewalld.service`

## 配置 selinux

selinux 有 3 中模式

1. enforcing: 强制模式
2. permissive：宽容模式
3. disabled：禁用

`sestatus` 查看当前的 selinux 状态

![20210108021450](http://pic.sigalx.com/pic/20210108021450.png)

Current mode: permissive 就是当前模式

如果只查看当前模式：`getenforce`

临时修改模式：`setenforce 0(permissive) | 1(enforcing)`

永久修改：`/etc/selinux/config` 改成 `SELINUX=disabled`，默认是 enforcing

重启

> 不建议关闭，改成宽容模式：permissive

## 更新 yum 源和添加 EPEL 源

## 配置阿里云的 yum 源

官网: [阿里云官网教程](https://developer.aliyun.com/mirror/centos?spm=a2c6h.13651102.0.0.3e221b117sozbb)

> 在 /etc/yum.repos.d/ 目录下的文件，8.3 版本之前是 CentOS-Base.repo，8.3 版本之后的是 CentOS-Linux-Base.reop

1. 备份系统配置

`mv /etc/yum.repos.d/CentOS-Base.repo /etc/yum.repos.d/CentOS-Base.repo.backup`

2. 下载配置

`curl -o /etc/yum.repos.d/CentOS-Base.repo https://mirrors.aliyun.com/repo/Centos-8.repo`

3. 安装 EPEL 源：`yum install epel-release -y`

4. 清理 yum

`yum clean all`

5. 重新生成缓存：

`yum makecache`

阿里云的repo

```conf
[base]
name=CentOS-$releasever - Base - mirrors.aliyun.com
failovermethod=priority
baseurl=https://mirrors.aliyun.com/centos/$releasever/BaseOS/$basearch/os/
        http://mirrors.aliyuncs.com/centos/$releasever/BaseOS/$basearch/os/
        http://mirrors.cloud.aliyuncs.com/centos/$releasever/BaseOS/$basearch/os/
gpgcheck=1
gpgkey=https://mirrors.aliyun.com/centos/RPM-GPG-KEY-CentOS-Official

#additional packages that may be useful
[extras]
name=CentOS-$releasever - Extras - mirrors.aliyun.com
failovermethod=priority
baseurl=https://mirrors.aliyun.com/centos/$releasever/extras/$basearch/os/
        http://mirrors.aliyuncs.com/centos/$releasever/extras/$basearch/os/
        http://mirrors.cloud.aliyuncs.com/centos/$releasever/extras/$basearch/os/
gpgcheck=1
gpgkey=https://mirrors.aliyun.com/centos/RPM-GPG-KEY-CentOS-Official

#additional packages that extend functionality of existing packages
[centosplus]
name=CentOS-$releasever - Plus - mirrors.aliyun.com
failovermethod=priority
baseurl=https://mirrors.aliyun.com/centos/$releasever/centosplus/$basearch/os/
        http://mirrors.aliyuncs.com/centos/$releasever/centosplus/$basearch/os/
        http://mirrors.cloud.aliyuncs.com/centos/$releasever/centosplus/$basearch/os/
gpgcheck=1
enabled=0
gpgkey=https://mirrors.aliyun.com/centos/RPM-GPG-KEY-CentOS-Official

[PowerTools]
name=CentOS-$releasever - PowerTools - mirrors.aliyun.com
failovermethod=priority
baseurl=https://mirrors.aliyun.com/centos/$releasever/PowerTools/$basearch/os/
        http://mirrors.aliyuncs.com/centos/$releasever/PowerTools/$basearch/os/
        http://mirrors.cloud.aliyuncs.com/centos/$releasever/PowerTools/$basearch/os/
gpgcheck=1
enabled=0
gpgkey=https://mirrors.aliyun.com/centos/RPM-GPG-KEY-CentOS-Official


[AppStream]
name=CentOS-$releasever - AppStream - mirrors.aliyun.com
failovermethod=priority
baseurl=https://mirrors.aliyun.com/centos/$releasever/AppStream/$basearch/os/
        http://mirrors.aliyuncs.com/centos/$releasever/AppStream/$basearch/os/
        http://mirrors.cloud.aliyuncs.com/centos/$releasever/AppStream/$basearch/os/
gpgcheck=1
gpgkey=https://mirrors.aliyun.com/centos/RPM-GPG-KEY-CentOS-Official
```

## yum 搭建 LNMP 环境

#### Nginx 安装

###### 配置 nginx 官方库

新建`/etc/yum.repos.d/nginx.repo`，并写入一下信息：

```
// 稳定版，一般用这个
[nginx-stable]
name=nginx stable repo
baseurl=http://nginx.org/packages/centos/$releasever/$basearch/
gpgcheck=1
enabled=1
gpgkey=https://nginx.org/keys/nginx_signing.key
module_hotfixes=true

// 主线版
[nginx-mainline]
name=nginx mainline repo
baseurl=http://nginx.org/packages/mainline/centos/$releasever/$basearch/
gpgcheck=1
enabled=0
gpgkey=https://nginx.org/keys/nginx_signing.key
module_hotfixes=true
```

安装`yum install nginx -y`

> 这里安装的是 1.18.0 版本

1. `nginx or systemctl status nginx.service`

`nginx -t` 查看配置文件错误的地方

> 没配置官方库的话，yum 源更新较慢，安装的 nginx 版本很旧，好像是 1.14.0

#### MySQL 安装

安装：`yum install -y mysql*`

`/etc/my.cnf.d/mysql-server.cnf` 配置文件

> 8.0.21

#### PHP 安装

`yum install -y php*`

> 7.2.24

1. 主配置文件：`/etc/php-fpm.conf`

2. 子配置文件：`/etc/php-fpm.d/www.conf`

#### 配置

```
启动：
systemctl start nginx.service
systemctl start mysql.service
systemctl start php-fpm.service
添加开机：
systemctl enable xxx

修改mysql密码
mysql -uroot -p   密码空
进入然后：set password='xuniji0017';

nginx配置：
核心配置文件：/etc/nginx/nginx.conf

配置/etc/nginx/conf.d/default.conf,加上

    location ~ \.php$ {
        root   /usr/share/nginx/html;
        fastcgi_pass   unix:/run/php-fpm/www.sock;
        fastcgi_index  index.php;
        fastcgi_param  SCRIPT_FILENAME  $document_root$fastcgi_script_name;
        include        fastcgi_params;
    }


php配置：
修改/etc/php-fpm/www.conf

user=apache => nginx
group=apache => nginx

重启nginx
```

#### Redis安装

`yum install -y redis`

查看版本`redis-cli -v`  => 5.0.3

进入：`redis-cli`

默认只能本地链接

#### Composer安装

[官网](https://pkg.phpcomposer.com/#how-to-install-composer)