> 适合：有 Git 基础，都是操作自己的库，协同操作另起一篇

## Git 的简易使用及操作集合

#### 安装完的第一件事

安装完 Git 应该先为本机设置以下两个项：

- `git config --global user.name "Your Name"`
- `git config --global user.email "email@example.com`

> `--global`全局配置，表示此台机器上的所有 Git 仓库都使用这个配置，也可以单独给仓库指定不同的用户名和地址，还有`--local`仓库配置和`--system`系统配置

可以使用：

- `git config -l`： 查看所有配置，如果有重名，可能有就是全局配置和仓库配置重复了
- `git config --global -l`： 查看全局配置
- `git config --local -l`： 查看此仓库配置
- `git config -e`： 打开配置文件

> github 和 gitee是根据邮箱来辨认用户的，如果你设置的邮箱和注册账号的邮箱是同一个，那你不管设置什么用户名，提交上去的时候，现在的都是你这个账号的用户名；

> 同时设置了全局和仓库的用户名邮箱，仓库优先级高

单独查询配置：

- `git config user.name` 查询全局的 user.name
- `git config --local user.name` 查询仓库的 user.name

删除配置：

- `git config --local --unset user.name`
- `git config --global --unset user.name`

#### 初始化仓库

- 初始化此文件夹为仓库：`git init`
- 克隆远程仓库：`git clone Addr`

本地文件夹会生成一个 `.git` 的版本库
