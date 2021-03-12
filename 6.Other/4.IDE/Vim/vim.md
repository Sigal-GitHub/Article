#### 自定义配置快捷 
```vim
<leader>       : 修改成","
fj             : 替换Esc
<space>        : 开关光标行所在折叠
zR             : 展开所有折叠    &&    zM             : 关闭所有折叠
<leader>ui     : 显示/隐藏菜单栏，工具条，滚动条
H和L           : 分别替换^,$
ctrl + j/k/h/l : 进行窗口跳转,不需要ctrl+w+j/k/h/l
';'修改成':'   : 一键进入命令行模式，不需要按shift
ctrl + t       : 新建teb
cM             : 清除行尾 ^M 符号    &&    cS             : 清楚行尾空格
<F3>           : 插入文件头
ctrl + j/k/h/l   进行上下左右窗口跳转,不需要ctrl+w+jkhl
```
####  自定义插件快捷
```vim
<F2>           : 呼出nerdtree
<F4>           : 开启Goyo同时全屏
:Goyo          : 只开启Goyo
ctrl + g/G     : 只开启Goyo
<Leader>t      : 窗口置顶
ctrl + up/down : 增加/减少透明度
: ll           : 开启limelight    &&    : ll!          : 关闭limelight
```
#### 目前有的插件
```vim
Plugin 'VundleVim/Vundle.vim'                           " 让Vundle管理Vundle需要安装这个
Plugin 'scrooloose/nerdtree'                            " 目录树，必备
Plugin 'vim-airline/vim-airline'                        " 状态栏
Plugin 'Yggdroot/indentLine'                            " 对齐线
Plugin 'junegunn/goyo.vim'                              " 禅意插件1
Plugin 'junegunn/limelight.vim'                         " 禅意插件2
Plugin 'leonid-shevtsov/gvimfullscreen_win32'           " 全屏插件，需要gvimfullscreen.dll
Plugin 'kien/ctrlp.vim'                                 " 查找插件
Plugin 'mattn/emmet-vim'                                " 前端神器
Plugin 'godlygeek/tabular'                              " 快速对齐插件
"Plugin 'tpope/vim-surround'                            " 轻松添加两边的符号
Plugin 'tpope/vim-commentary'                           " 快速注释
"Plugin 'terryma/vim-multiple-cursors'                  " 多光标同时编辑，原生命令也行，不过这个简化了
Plugin 'luochen1990/rainbow'                            " 彩虹括号，装逼用
Plugin 'gregsexton/MatchTag'                            " 高亮两个配对的tag
Plugin 'pangloss/vim-javascript'                        " JS高亮提示
```

