## 分文件管理

1. 配置文件目录

在 nginx.conf 中加入 `include xxx文件名xxx/*;`

2. 创建文件夹

然后创建对应的文件夹

3. 配置

将 nginx.conf 中的 server 模块复制，修改里面的内容在新建的配置文件夹中保存为单独的配置文件 *.conf