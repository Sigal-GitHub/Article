## VS Code PicGo 插件 + 阿里云 + 域名搭建个人图床

[toc]

> 搭建一个私人图床，方便自己写笔记，写博客之类的，特别是用 Markdown 语言或者自建站，不用到处去拷贝图片也能减少站点对服务器的访问

> 如果不使用阿里云，可以使用七牛云，个人感觉区别就是，七牛有免费的空间，阿里是收费的，不过域名这块比较麻烦，我个人的域名都在阿里上，就不去省这十块钱了

#### 阿里云配置

开通阿里云的云存储 OSS，然后购买，基础 40G 一年也就不到十块钱，不是用来存摄影图，生活图，只是写文章的截图，40G 也就差不多了，不够再补

根据需求选择类型购买使用，我们用图床的话一般就第一个标准类型，如下图：

![20200906103213](http://pic.sigalx.com/pic/20200906103213.png)

一开始用，可以全部都选择第一项，以后需要的话再升级，如下图：

![20200906103226](http://pic.sigalx.com/pic/20200906103226.png)

进入到 OSS 管理控制台 -> Bucket 列表，创建  Bucket ，如下图：截图并不完整

![20200906103248](http://pic.sigalx.com/pic/20200906103248.png)

> 版本控制这些就没必要了，毕竟存个图片，权限需要是公共的，加密这些也不用，权限下面这些都是不开通就好了

这个时候 OSS 就可以使用，可以上传文件试试，进入刚刚新建的 Bucket 找到文件管理就能上传了

![20200906103334](http://pic.sigalx.com/pic/20200906103334.png)

里面的 URL 就是访问地址，现在还没绑定域名，域名绑定如下：

在传输管理 -> 域名管理 -> 绑定域名，把你在阿里云的域名填上，一般都填二级域名的吧，比如我的博客地址是 `www.sigalx.com`，我解析的是`pic.sigalx.com`，再选上自动添加，就能生效了，不用手动去解析

![20200906103356](http://pic.sigalx.com/pic/20200906103356.png)

接下来下需要一些信息，用来建立双方之间的链接使用；打开右上角个人信息，进入到 AccessKey 管理

![20200906103408](http://pic.sigalx.com/pic/20200906103408.png)

没有 AccessKey 的话需要新建一个，关于安全性的问题，如果你觉得不安全的话，可以创建一个子用户，设置权限来使用，只是图床的话就没什么必要了

![20200906103419](http://pic.sigalx.com/pic/20200906103419.png)

新建完的 AccessKey 会在列表显示，复制 AccessKey ID 和 AccessKey Secret 后面要用

#### VS Code 中 PicGo 插件的使用

安装 PicGo 插件

配置，如下图：

![20200906103434](http://pic.sigalx.com/pic/20200906103434.png)

只需要配置这些就可以

```
Aliyun: Access Key ID 和 Access Key Secret 就是上面记下来的两串字符

Aliyun: Area 就是创建 Bucket 中 Endpoint 中的前段字符

Aliyun: Bucket 就是你的 Bucket 名了

Aliyun: Custom Url 就是你绑定的域名，要是没有绑定，就填没绑定的，记得要加上 http:// or https://

Aliyun: Path 就是放图片存放在 Bucket 的路径了

Pic Bed: Current 一定要改成 aliyun ，这个插件默认是 SM.MS
```

做完这些配置，就可以测试了

先截图到剪切板，Ctrl + Alt + U 上传，看到下图就 OjbK了

![20200906103446](http://pic.sigalx.com/pic/20200906103446.png)

关于配置问题，也可以写个 json 文件，直接在下图的地方引入，省的自己一个个配置，在重装或者拷贝的时候也比较方便，这里我就没有花时间去测试了，如果有需要的，可以自行研究一下

![20200906103457](http://pic.sigalx.com/pic/20200906103457.png)

最后附上这个插件的快捷：

Ctrl + Alt/Cmd + Opt + U ：从剪贴板上传图像

Ctrl + Alt/Cmd + Opt + E ：从资源管理器上传图像

Ctrl + Alt/Cmd + Opt + O ：从输入框上传图像 （和 Tim 有冲突）


> END