## 远程操作(使用场景分类)

[toc]

####操作自己的库

如果需要链接远程库的话还需要下面的**前置操作**：

- 创建 SSH Key：`ssh-keygen -t rsa -C "youremail@example.com"`
- 到用户主目录的`.ssh`文件中找到 `id_rsa.pub`，将文件里的代码记下并在各大平台填入；如 Gitee 在设置里添加 SSH 公钥，GitHub 在设置里添加 SSH Key

**操作远程库的两种情况：**

###### 一. 本地已有项目，需要同步到远程的一个新库（空库）

- // 前置操作
- 本地项目如果没使用过 Git 的话，需要先初始化：`git init`
- 本地与远程库(空库)建立链接：`git remote add origin Addr`
- //TODO: 新建文件并提交更改：`git add` and `git commit`
- 推送更改到远程库：`git push -u origin master`

> `origin` 就是你在本地仓库给这个远程库起的名字，如此仓库都链接了 Gitee 和 GitHub，就可以起一个 gitee 和 github；后面的就是 SSH 地址，也可以是其他甚至 HTTPS 地址，不过 SSH 最快

> `master` 就是你要提交的分支名


###### 二. 本地无项目，需要从一个已有的远程库中同步项目

// TODO: git push -u 什么意思


> 现在的github 默认的主分支名变成了main记得修改`git branch -M main`

此情况也有两种方式：

1. 克隆项目
    - // 前置操作
    - 直接克隆整个远程库的项目到本地：`git clone Addr FileName`
    - 克隆下来的项目带`.git`文件，`commit`后就可以`push`到远程，默认远程库名就是：`origin`
    - `git push -u origin master`
    - 修改默认的`origin`：`git remote rename origin NewName`

2. 拉取项目到本地文件
    - // 前置操作
    - 新建本地文件夹并初始化：`git init`
    - 与远程库(带文件)建立链接：`git remote add Name Addr`
    - 把远程库的文件`pull`到本地：`git pull Name Branch`
    - 本地修改文件`commit`后推送到远程库：`git push -u Name Branch` 

// TODO: pull 和 fetch 的区别

> 一般使用第一种情况

###### 三. 仓库同时链接 Gitee 和 GitHub 推送

如果有个库在 Gitee 和 GitHub 都有，需要同时推送到两个平台，有两种方式：

1. 两个平台分别建立链接，也就是起不同的名称，并`push`两次
2. 一个名称链接两个远程库
    - 先建一个链接：`git remote add origin Addr`
    - 再链接第二个仓库到`origin`：`git remote set-url --add origin Addr`
    - 这样每次`push`都能同时推送到链接的平台
    - 如果两个库不同步，需要先同步再操作

> 查看此仓库链接了几个远程库：`git remote -v`