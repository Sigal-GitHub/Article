## VS Code 修改背景图的两种方式

[toc]

#### 一. 插件修改

安装 background 或者 background-cover；选一个就可以；前者比较多人安装

这两个都是中文介绍，进去插件详情里面就已经说得很清楚了

传送门: [background](https://marketplace.visualstudio.com/items?itemName=shalldie.background) and [background-cover](https://marketplace.visualstudio.com/items?itemName=manasxx.background-cover)

有问题的是：

系统会不停提示你：`background-attachmentYour Code installation appears to be corrupt. Please reinstall.`，设置以后不提示就可以解决

#### 二. css 文件修改

找到 VS Code 的安装目录，我的 win10 是:`C:\Users\sigal\AppData\Local\Programs\Microsoft VS Code\resources\app\out\vs\workbench`,打开下面的`workbench.desktop.main`文件，如果是一串压缩代码的话，可以先格式化一下

添加一下代码到文件里：

```
 body {
    pointer-events: auto !important;
    background-size: coner !important;
    opacity: 0.8 !important;
    background-position: 0 0 !important;
    background-image: url('file://d://1.jpg') !important;
    content: "";
    position: relative;
    z-index: 99999;
    width: 100%;
    background-attachment: fixed;
    background-repeat: no-repeat;
}
```

重启就可以了

有问题的是：

1. 系统会不停提示你：`background-attachmentYour Code installation appears to be corrupt. Please reinstall.`，设置以后不提示就可以解决
2. 随着VS Code版本的更新，可能会出现一些莫名其妙的事情
3. 与前面介绍的插件有冲突，会导致开启 VS Code 时闪动

#### 三. 优缺点

插件相对直接修改文件来说配置比较方便，但是随着插件的增多，还安装插件的话就有点臃肿了，而且还需要管理员身份运行，说白了插件也是修改 css 文件生效的，个人是比较推荐自己修改 css 文件

> END