> 插件安装的规范： 能不装就不装，简洁明了

> // TODO: 跳转链接未加

## VS Code 自用插件

[toc]

### 外观类

###### [Panda Theme](https://marketplace.visualstudio.com/items?itemName=tinkertrain.theme-panda)

> 就喜欢滚滚。。。。所以用这个，配色也好看

熊猫主题，黑白中带点粉绿

![20200906003041](http://pic.sigalx.com/pic/20200906003041.png)

###### [Material Icon Theme](https://marketplace.visualstudio.com/items?itemName=PKief.material-icon-theme)

> 这个用不用都行，相比其他 Icon 我比较偏向这个吧

图标主题，比较多彩，有配套的配色，我这里只用图标，不用的话自带的也没问题

![20200906003141](http://pic.sigalx.com/pic/20200906003141.png)

###### [Rainbow Brackets](https://marketplace.visualstudio.com/items?itemName=2gua.rainbow-brackets) And [Indent Rainbow](https://marketplace.visualstudio.com/items?itemName=oderwat.indent-rainbow)

> 虽然 VS Code 自带括号匹配高亮，不过也需要光标在正确的位置，Rainbow 插件在你只需要瞄一眼的时候很方便，两个插件结合的话，就有更好的辨识度了

为圆括号，方括号和弯曲的括号提供彩虹色，嵌套的时候特别有用

![20200906003426](http://pic.sigalx.com/pic/20200906003426.png)

由于 html 里的标签本身有配色，本身又是配对的括号，所以在 html 里的结构尖括号是没有彩虹色的，这时可以使用的还有 Indent Rainbow，如下图：

![20200906003450](http://pic.sigalx.com/pic/20200906003450.png)

不过毕竟有标签高亮，这个我就没装，觉得有点太花里胡哨了，供大家选择吧

###### [Fira Code](https://github.com/tonsky/FiraCode/)

> 看腻了其他字体，这个还是会眼前一亮的，好不好看就见仁见智了

Fira Code 开源字体，一些字符比较特立独行

win10安装：

在 GitHub 中下载下来 -> 开打 distr/ttf 文件，右键给所有用户安装里面的 .ttf 字体（全部）

![20200906003518](http://pic.sigalx.com/pic/20200906003518.png)

### 通用类

###### [Vim](https://marketplace.visualstudio.com/items?itemName=vscodevim.vim)

> Vim 就没什么好说的了，需要用到的自己会去研究，主要是一些习惯上的快捷绑定

Vim 党必备，感觉 VS Code 对此类插件比其他好一些，比较少一些莫名其妙的 Bug 

这个就没必要放图，直接放自用配置好了，在全部配置那里

###### [Project Manager](https://marketplace.visualstudio.com/items?itemName=alefragnani.project-manager)

> 此插件作用不止于此，我一般只用来当目录用，后面更新了支持远程，可以发挥想象，自行研究

稍做简单的配置，就能在项目之间快速切换，对同时开发多个项目的人员来说很好用

![20200906011850](http://pic.sigalx.com/pic/20200906011850.png)

配置示例：

![20200906011905](http://pic.sigalx.com/pic/20200906011905.png)

###### [Better Align](https://marketplace.visualstudio.com/items?itemName=wwm.better-align)

> 强迫症患者必备，不过和其他格式化插件会有冲突，你对齐了格式化一下又给恢复了，可以自己做配置

快速对齐 `:,=,+=,-=,*=,/=,=>` 符号，需要配置一下快捷键，直接把插件介绍里面代码复制到快捷配置里就可以了

![20200906011930](http://pic.sigalx.com/pic/20200906011930.png)

快捷配置：File -> Preferences -> Keyboard Shortcuts -> 右上角第一个图标(Open Keyboard Shortcuts)

```
[
    {
        "key": "ctrl+alt+=",
        "command": "wwm.aligncode",
        "when": "editorTextFocus && !editorReadonly"
    }
]
```

###### [Path Intellisense](https://marketplace.visualstudio.com/items?itemName=christian-kohler.path-intellisense)

> 一般都必备的吧，没什么配置，直接安装就好，如果在 windows 下输入 . 号和其他有冲突的话，解除快捷键的绑定就好了，插件详情页有

自动补全文件名和路径的插件，属于 VS Code 功能补全吧

###### [TODO Tree](https://marketplace.visualstudio.com/items?itemName=Gruntfuggly.todo-tree)

标记插件，做整个项目的时候非常好用，安装就可以用，当然，也有很丰富的配置，可以根据手册自己修改

![20200906154839](http://pic.sigalx.com/pic/20200906154839.png)

不想修改的可以装一个 [TODO Highlight](https://marketplace.visualstudio.com/items?itemName=wayou.vscode-todo-highlight) 自带一些很漂流的颜色区分，不过要把 Tree 的高亮关掉，会有冲突

![20200906154856](http://pic.sigalx.com/pic/20200906154856.png)

### Markdown 党

###### [Markdown Preview Enhanced](https://marketplace.visualstudio.com/items?itemName=shd101wyy.markdown-preview-enhanced)

> 一般我都使用有道云笔记各端同步，有道的 Markdown 图片不是本地的，就不方便拷贝，只能分享

> 此插件再配合 Project Manager 有奇效；Project Manager 定义一个本地项目存放文件夹，需要写文章的时候直接新窗口打开就好了

重度使用 Markdown 只推荐这个，[typora](https://www.typora.io/)?，可以删了；更多功能等你自己去挖掘，使用详情点击标题跳转到插件介绍

![20200906012020](http://pic.sigalx.com/pic/20200906012020.png)

###### [PicGo](https://marketplace.visualstudio.com/items?itemName=Spades.vs-picgo)

> 自建了个图床，再远程建个私有仓库，完美解决本地图片保持，和文章同步的问题，这个省事，所以必备

使用图床必备的插件，支持很多平台，配置也简单

附上自建图床的教程: [PicGo 插件 + 阿里云OSS + 域名搭建个人图床](https://note.youdao.com/)

###### [vscode-pdf](https://marketplace.visualstudio.com/items?itemName=tomoki1207.pdf) (可选)

如名，vscode 的 pdf 插件，可以直接在 vscode 中打开 PDF，很实用

如 md 文件导出PDF后检查啊，边看电子书边学习啊，都能用上，一个 VS Code 搞定，实测打开速度还行

唯一的缺点是：没目录

### 前端模块

###### [Auto Rename Tag](https://marketplace.visualstudio.com/items?itemName=formulahendry.auto-rename-tag)

> 前端必备，相似的还有 Auto Close Tag，自动闭合标签插件，一般有 emmet 就不用了，基本很少能用上

自动配对修改标签名

###### [Beautify](https://marketplace.visualstudio.com/items?itemName=HookyQR.beautify) And [Prettier - Code formatter](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode)

> 这插件如果设置 editor.formatOnSave 的话会与 Better Align 对齐或其他有格式化代码功能插件相冲突，建议绑定一个单独的快捷键

Beautify 前端格式化代码插件基本不用什么配置，直接安装使用就已经很好了，支持`javascript, JSON, CSS, Sass, Lass, HTML` 这些，可以配置保存文件时使用，也可以单独配置快捷键使用

不用 Beautify 的话可以用 Prettier - Code formatter，就是这个功能更强大，配置虽然比较麻烦，不过有很强的自定义

**保存文件使用：**

找到配置里的 `editor.formatOnSave` 项打勾就好

或者在配置文件加上：

```
"editor.formatOnSave": true,
```

**Beautify 单独配置快捷键使用：**

```
{
  "key": "cmd+alt+-",
  "command": "HookyQR.beautify",
  "when": "editorFocus"
}
```


###### [HTML CSS Support](https://marketplace.visualstudio.com/items?itemName=ecmel.vscode-html-css)

> 前端必装...用框架的时候非常方便

智能提示CSS类名以及id

###### [Live Server](https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer)

> 我是必备的，用的键盘是 61 键的，按 F5 还需要按组合键........能右键打开，快捷键打开，命令行打开

> 还有个类似的插件 open in browser：用浏览器打开 hmtl 文件，功能没那么多，不过也不限于 html 文件，有了 Live Server 这个就用不上

实时刷新页面插件，有挺多功能，不过最常用的还是保存刷新，其他需要配置

![![image](BDA23F5CE8D245BD95686DB5CFF63704)](http://pic.sigalx.com/pic/![image](BDA23F5CE8D245BD95686DB5CFF63704).png)

> 前端很多功能都随着 VS Code 的更新集成了，没必要去安装一些语法插件，如 HTML Snippets，emmet 之类的

> 像 ESLint 这种插件，用才安装，不用就没必要，还要花额外的时间去配置，同理还有 Vue Node 相关的插件，使用才装

> 当然专业前端肯定少不了，我这种半前端就是可选项了

### PHP 模块

> 在欢迎页面里 Tools and languages 点击 PHP，会就默认安装 [PHP Debug](https://marketplace.visualstudio.com/items?itemName=felixfbecker.php-debug)，[PHP Extension Pack](https://marketplace.visualstudio.com/items?itemName=felixfbecker.php-pack)，[PHP IntelliSense](https://marketplace.visualstudio.com/items?itemName=felixfbecker.php-intellisense) 这三个插件

**开发 PHP 需要加上：**

`"php.validate.executablePath": "你的路径\\php\\php7.3.4nts\\php.exe",`

如果禁用了`PHP Language Features`内置插件，这个就不必要加

不然 VS Code 内置插件`PHP Language Features`会报错：`Cannot validate since no PHP executable is set. Use the setting 'php.validate.executablePath' to configure the PHP executable.`

不禁用插件的话，可以直接禁用此插件的基本功能：`"php.suggest.basic": false, // 禁用 VS Code 自带的 PHP 语法提示，避免功能重复`，适用下面两个插件

###### [PHP IntelliSense](https://marketplace.visualstudio.com/items?itemName=felixfbecker.php-intellisense)(可选)

只支持7+ ，PHP 语法和其他的智能提示，比 VS Code 自带的更加全面，使用的时候需要添加 php.exe 的执行路劲，还建议关闭VS Code 自带的 PHP 语法提示，避免功能重复，也就是没有那么多重复的代码块提示了，属于 php 开发必备的插件了

`"php.executablePath": "你的路径\\php\\php7.3.4nts\\php.exe",`

###### [PHP Intelephense](https://marketplace.visualstudio.com/items?itemName=bmewburn.vscode-intelephense-client)

格式化代码，函数间跳转等功能，指针悬停会有更强大的提示，但是，和内置的 php 插件功能有冲突，官方也是建议禁用PHP Language Features内置插件和第三方类似的插件，如上面这个，如果不习惯可以直接使用 IntelliSense ，就是需要再安装个格式化代码的插件

> 这货还是个收费插件，有兴趣的可以去插件首页看看，一般免费的就够用了

> 以上两个插件同时装的话，也是有冲突的，一般装了下面的就可以了，毕竟下面这个多了个格式化的功能


###### [PHP Extension Pack](https://marketplace.visualstudio.com/items?itemName=felixfbecker.php-pack)(可选)

PHP 扩展包，一些 Debugger，IntelliSense 啦，这个包就包含了 PHP Debug 和 PHP IntelliSense 两个插件了

###### [PHP Debug](https://marketplace.visualstudio.com/items?itemName=felixfbecker.php-debug)

PHP 的本地 && 远程调试插件，使用需要自己配置一些项目

###### [PHP DocBlocker](https://marketplace.visualstudio.com/items?itemName=neilbrayfield.php-docblocker)(可选)

PHP 快速注释插件，注释格式，高亮关键字功能，可以自定义模板

代码量比较多得同学装一个还是很方便的

我自己是没装，写一下就好了，省的装那么多插件 VS Code 加载很慢

## VS Code 其他插件

###### [Polacode-2020](https://marketplace.visualstudio.com/items?itemName=jeff-hykin.polacode-2019)

之前叫 Polacode-2019 ，这不 2020 年了嘛，改名了；根据代码片段快速生成一个图片

需要使用图片分享代码的同学很适用

命令行输入：Polacode 开启，选中代码片段，点击图标就可以生成了

![20200906154625](http://pic.sigalx.com/pic/20200906154625.png)

###### [GitLens](https://marketplace.visualstudio.com/items?itemName=eamodio.gitlens)

显示文件最近的 commit 和作者，显示当前行 commit 信息

###### [Document This](https://marketplace.visualstudio.com/items?itemName=joelday.docthis)

JS,TypeScript 注释文档生成器，类和函数，比自带好用一些，C+A+D直接快速生成注释

###### [vscode-fileheader](https://marketplace.visualstudio.com/items?itemName=mikey.vscode-fileheader)

生成自定义文件头信息，可自由配置

![20200906155107](http://pic.sigalx.com/pic/20200906155107.png)

###### [Image Preview](https://marketplace.visualstudio.com/items?itemName=kisstkondoros.vscode-gutter-preview)

鼠标移到路径里显示图像预览，前端实用

###### [filesize](https://marketplace.visualstudio.com/items?itemName=mkxml.vscode-filesize)

在底部状态栏显示当前文件大小，点击后还可以看到详细创建、修改时间

![20200906155016](http://pic.sigalx.com/pic/20200906155016.png)


## VS Code 奇葩插件

> VS Code 不是编辑器，不是编辑器，不是编辑器，重要的事情说三遍，同理还有 Atom 也不是；所以，你可以用 VS Code 听音乐，看小说，追番，上班摸鱼...
 
###### [GlassIt-VSC](https://marketplace.visualstudio.com/items?itemName=s-nlf-fh.glassit) or [Windows opacity](https://marketplace.visualstudio.com/items?itemName=skacekachna.win-opacity) 窗口透明

两个都是能设置 VS Code 透明的插件，第一个 Win/Linux 都能用，快捷调节透明度，第二个讲明是 win 的，当然也可以搜 mac 或 linux 专用的，就是不知道有没有

**开个透明边写边看电影，它不香吗?**

![![image](15A8F214C3F949788A840E5DF0191EDD)](http://pic.sigalx.com/pic/![image](15A8F214C3F949788A840E5DF0191EDD).png)

###### [Vibrancy](https://marketplace.visualstudio.com/items?itemName=eyhn.vscode-vibrancy) 窗口毛玻璃

和上面那个透明的就不一样了，这个是毛玻璃不透的，装逼利器，支持 Win 和 Mac 系统；不过这种插件和[更换背景](https://note.youdao.com/)差不多，都是修改编辑器里面的文件达到效果，就会出现损坏的提示了；而且每次重启 VS Code 还得运行一次，反正截至到我写这篇文章时，还是这样；我自己的图就不放了，装逼还是得付出代价打，找了张网图你们看看效果吧：

![20200906155751](http://pic.sigalx.com/pic/20200906155751.png)

###### [VSC Netease Music](https://note.youdao.com/https://marketplace.visualstudio.com/items?itemName=nondanee.vsc-netease-music) 听歌

听歌神器来啦！网抑云 Music ，下图感受，我就没配置了，所以老规矩，找了个网图，有兴趣的可以进插件详情查看，对我来说配置稍微有点麻烦，需要下载一个文件，主要是我这里链接不上 /(ㄒoㄒ)/~~，真的不是我懒

![20200906155816](http://pic.sigalx.com/pic/20200906155816.png)


###### [Thief-Book](https://marketplace.visualstudio.com/items?itemName=C-TEAM.thief-book) 看书.小说

看书神器，介绍就写的是摸鱼看书神器；还有老板键，谁能想到你代码下面有一行小说！！！！！！不过编码有问题的话会出现乱码

来，感受一下界面：

![20200906155838](http://pic.sigalx.com/pic/20200906155838.png)

当然，这类的还有很多，我就是觉得这个隐藏得太好了...如功能更强大得：[epub reader](https://marketplace.visualstudio.com/items?itemName=renkun.reader) 和 [z-reader](https://marketplace.visualstudio.com/items?itemName=aooiu.z-reader)

###### [daily anime](https://marketplace.visualstudio.com/items?itemName=deepred.daily-anime) 追番

追番神器，显示更新列表，当然，观看的话还是直接跳到 Bangumi 网的

![20200906155855](http://pic.sigalx.com/pic/20200906155855.png)

==我就想有没有可以追美剧的...要不写一个插件追一下美剧天堂里的更新吧...==

###### [Rainbow Fart](https://marketplace.visualstudio.com/items?itemName=saekiraku.rainbow-fart)

这个...也是挺沙雕的，真的是彩虹屁，会在你写代码的时候，根据你键入的关键字匹配相应的语音，可爱，酥脆的声音陪伴你 Codeing...

想象一下在办公室开启这东西...

还可以自定义语音包，开启的时候会弹出一个网页，需要授权并保存网页在线

![20200906155911](http://pic.sigalx.com/pic/20200906155911.png)

![20200906155921](http://pic.sigalx.com/pic/20200906155921.png)

要演示这个插件需要放视频了，这里就不放了，有兴趣的可以网上搜一下

> 上面这几个追番看书听歌看小说的插件都是很多人推荐的了，下面来点不一样的

###### [韭菜盒子](https://marketplace.visualstudio.com/items?itemName=giscafer.leek-fund)

有股民么？来，这个就是看股票 & 基金实时数据的插件，功能嘛，如下图：

![20200906155941](http://pic.sigalx.com/pic/20200906155941.png)

怎么样，上班摸鱼看股，好像又多了一项技能了呢！

---

> 还有其他奇葩的插件，如鼓励师这些，这种真的就玩玩的，这里不做推荐了，需要可以直接搜一下

**暂时就更新到这里了，以后有发现还会慢慢更新上来**

> END