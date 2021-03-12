## Windows10 + phpstudy 下 VS Code + XDebug 本地调试 PHP

[toc]

#### phpstudy 配置

phpstudy(8.1.1.1) 安装好后，软件管理 → php，找到当前版本的 php ，进入到设置里

![20200907232524](http://pic.sigalx.com/pic/20200907232524.png)

选择扩展组件里的XDebug调试组件开启

![20200907232801](http://pic.sigalx.com/pic/20200907232801.png)

> 简单调试的话 Profiler 输出和 Trace 输出选不选都可以，端口的话自己修改，或者默认9000也行，但是端口一定要统一

打开 php.ini 配置文件，phpstudy 会自动在文件最下方添加一些 xdebug 的配置

如下：

```
[Xdebug]
zend_extension=D:/phpstudy_pro/Extensions/php/php7.3.4nts/ext/php_xdebug.dll
xdebug.collect_params=1
xdebug.collect_return=1
xdebug.auto_trace=Off
xdebug.trace_output_dir=D:/phpstudy_pro/Extensions/php_log/php7.3.4nts.xdebug.trace
xdebug.profiler_enable=Off
xdebug.profiler_output_dir=D:/phpstudy_pro/Extensions/php_log/php7.3.4nts.xdebug.profiler
xdebug.remote_enable=Off
xdebug.remote_host=localhost
xdebug.remote_port=9000
xdebug.remote_handler=dbgp
```

这里需要注意的是，下面两个配置必须有，在 PHP Debug 插件介绍里也说明了

```
xdebug.remote_enable=On
xdebug.remote_autostart = 1
```

![20200907234614](http://pic.sigalx.com/pic/20200907234614.png)

> 如果不加上这两个配置，那在你 F5 开启调试后，去浏览器刷新页面，VS Code 是获取不了的

就是说完整的配置应该是：

```
[Xdebug]
zend_extension=D:/phpstudy_pro/Extensions/php/php7.3.4nts/ext/php_xdebug.dll
xdebug.collect_params=1
xdebug.collect_return=1
xdebug.auto_trace=Off
xdebug.trace_output_dir=D:/phpstudy_pro/Extensions/php_log/php7.3.4nts.xdebug.trace
xdebug.profiler_enable=Off
xdebug.profiler_output_dir=D:/phpstudy_pro/Extensions/php_log/php7.3.4nts.xdebug.profiler
xdebug.remote_host=localhost
xdebug.remote_port=9000
xdebug.remote_handler=dbgp
xdebug.remote_enable=On
xdebug.remote_autostart = 1
```

访问本地的 phpinfo.php 搜索 xdebug 看看有没有结果，有的话就安装成功了

![20200907233345](http://pic.sigalx.com/pic/20200907233345.png)

> 有强迫症不想看到橘色那行字的话：

点 [xdebug](https://xdebug.org/wizard) 进入，将刚刚 phpinfo.php 显示的页面，查看源代码，将源代码全部复制到框框里

![20200907233809](http://pic.sigalx.com/pic/20200907233809.png)

点击最下面的按钮，会自动根据源代码的信息，给你匹配出适合版本的 xdebug 供你下载

![20200907233949](http://pic.sigalx.com/pic/20200907233949.png)

将官方下载的 dll 文件改名，替代 php.ini 配置路径里的那个 dll 文件，再重启服务器，就不会有这橘色的显示了

![20200907234834](http://pic.sigalx.com/pic/20200907234834.png)


#### VS Code 配置

VS Code 只需要有 [PHP Debug](https://marketplace.visualstudio.com/items?itemName=felixfbecker.php-debug) 就可以使用了

在站点目录下新建一个 php 文件 index.php，用 VS Code 打开

点击左侧调试图标，创建 launch.json 配置文件，环境选 php

VS Code 会自动在当前的站点目录下新建一个 .vscode 文件夹存放 launch.json
配置文件，以后你要修改配置，也是在这个文件中修改，一般使用默认就好

端口默认就是9000，如果有端口占用的情况，修改一下端口，记得要和 phpstudy(php.ini) 里面 xdebug 端口保持一致

![20200907235441](http://pic.sigalx.com/pic/20200907235441.png)

到这里配置就完成了，可以进行测试：

设置一个断点，F5 打开调试，访问测试文件，就可以看到效果了

![20200907235739](http://pic.sigalx.com/pic/20200907235739.png)

如果觉得调试栏挡住了页面标题，可以在配置文件加上：`"debug.toolBarLocation": "docked"`

![20200907235827](http://pic.sigalx.com/pic/20200907235827.png)

---

#### F&Q

同理，其他集成环境或者自己搭建的环境操作也是大同小异

- 下载对应版本的的 xdebug.dll 文件
- php.ini 增加 xdebug 的配置
- 编辑器或者 IDE 的配置

> END