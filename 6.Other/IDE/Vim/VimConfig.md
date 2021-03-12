```
" --------------------------------------------------< 判断是否处于GUI界面 Start >
if has('gui_running')
    let g:isGUI = 1
else
    let g:isGUI = 0
endif
" --------------------------------------------------< 判断是否处于GUI界面  End  >

" --------------------------------------------------< 使用GUI界面时的设置 Start >
if g:isGUI
    "winpos 100 40              " 指定窗口出现的位置，坐标原点在屏幕左上角
    set lines=40 columns=140    " 指定窗口大小，lines 为高度，columns 为宽度
    set guioptions+=c           " 使用字符提示框
    set guioptions-=m           " 隐藏菜单栏
    set guioptions-=T           " 隐藏工具栏
    set guioptions-=L           " 隐藏左侧滚动条
    set guioptions-=r           " 隐藏右侧滚动条
    set guioptions-=b           " 隐藏底部滚动条
    set showtabline=0           " 隐藏Tab栏
endif
" --------------------------------------------------< 使用GUI界面时的设置  End  >

" -------------------------------------------------------------< 自动加载 Start >
" vimrc文件修改之后自动加载, windows
" autocmd! bufwritepost _vimrc source %

" vimrc 文件修改之后自动加载，linux
autocmd! bufwritepost .vimrc source %
" -------------------------------------------------------------< 自动加载  End  >

" -------------------------------------------------------------< 智能配置 Start >
set t_Co=256                            " 开启 256 色支持
set laststatus=2                        " 启动状态栏信息
set cmdheight=2                         " 设置命令行的高度为 2，默认为 1
set cursorline                          " 突出显示当前行
" set nowrap                            " 设置不自动换行
set ruler                               " 右下角显示光标位置的状态行
set showcmd                             " 显示未完成的命令
set showmatch                           " 高亮匹配括号
set showmode                            " 显示你所处于的模式
set scrolloff=4                         " 在上下移动光标时，光标的上方或者下方至少会保留显示的行数
set smartindent                         " 启用智能对齐方式
set autoindent                          " 自动对齐
set ai!                                 " 设置自动缩进
set hidden                              " 允许在有未保存的修改时切换缓冲区，此时的修改由 vim 负责保存
set shortmess=atI                       " 启动的时候不显示那个援助乌干达儿童的提示
set wildmenu                            " 增强模式中的命令行自动完成操作
set autoread                            " 当文件在外部被修改的时候，自动更新该文件
set list                                " 显示特殊字符，(转下)
set listchars=tab:\~\ ,trail:.          " 其中Tab使用高亮~代替，尾部空白使用高亮点号代替
" 打开自动定位到最后编辑的位置，需要确认 .viminfo 当前用户可写
if has("autocmd")
    au BufReadPost * if line("'\"") > 1 && line("'\"") <= line("$") | exe "normal! g'\"" | endif
endif
" 当某一行输入注释，禁止下一行自动输入注释
autocmd FileType * setlocal formatoptions-=c formatoptions-=r formatoptions-=o
" -------------------------------------------------------------< 智能配置  End  >

" -------------------------------------------------------------< 编码设置 Start >
set encoding=utf-8                      " 设置 gvim 内部编码，默认不更改
set fileencoding=utf-8                  " 设置当前文件编码，可以更改，如：gbk（同cp936）
" 设置支持打开的文件的编码
set fileencodings=ucs-bom,utf-8,gbk,cp936,latin-1
" 设置新（当前）文件的 <EOL> 格式，可以更改，如：dos（windows系统常用）
set fileformat=unix
set fileformats=unix,dos,mac            " 给出文件的 <EOL> 格式类型
" -------------------------------------------------------------< 编码设置  End  >

" -------------------------------------------------------------< 行号配置 Start >
set number                              " 显示行号
" 相对行号: 行号变成相对，可以用 nj/nk 进行跳转
set relativenumber number
au FocusLost * :set norelativenumber number
au FocusGained * :set relativenumber
" 插入模式下用绝对行号, 普通模式下用相对
autocmd InsertEnter * :set norelativenumber number
autocmd InsertLeave * :set relativenumber
" -------------------------------------------------------------< 行号配置  End  >

" -------------------------------------------------------------< 搜索配置 Start >
set hlsearch                            " 高亮搜索
set incsearch                           " 在输入要搜索的文字时，实时匹配
" set noincsearch                       " 取消实时匹配
set ignorecase                          " 搜索模式里忽略大小写
set nowrapscan                          " 搜索到文件两端时不重新搜索" 搜索到文件两端时不重新搜索
" -------------------------------------------------------------< 搜索配置  End  >

" -------------------------------------------------------------< 备份配置 Start >
" 备份到另一个位置，防止误删，目前是取消备份
" set backup
" set backupext=.bak
" set backupdir=/tmp/vimbak/
" 保存文件前建立备份，保存成功后删除备份
" set writebackup
set nobackup                            " 设置无备份文件
set noswapfile                          " 设置无临时文件
set noundofile                          " 设置无 un 文件
" -------------------------------------------------------------< 备份配置  End  >

" -------------------------------------------------------------< 折叠配置 Start >
set foldenable                          " 允许启用折叠
" set foldmethod=manual                 " 手动折叠
set foldmethod=indent                   " indent 折叠方式
" set foldmethod=marker                 " marker 折叠方式
set foldlevelstart=99                   " 默认系统不折叠
" 常规模式下用空格键来开关光标行所在折叠（注：zR 展开所有折叠，zM 关闭所有折叠）
nnoremap <space> @=((foldclosed(line('.')) < 0) ? 'zc' : 'zo')<CR>
" -------------------------------------------------------------< 折叠配置  End  >

" -------------------------------------------------------------< 缩进配置 Start >
set backspace=2                         " 设置退格键可用
set expandtab                           " 将 Tab 转换为空格
set tabstop=4                           " 设置 Tab 的宽度
set shiftwidth=4                        " 换行时自动缩进宽度
set softtabstop=4                       " 按退格键一次可以删掉 4 个空格
set shiftround                          " 用“<”和“>”缩进时使用 shiftWidth 的倍数
set smarttab                            " 按一次退格键就删除一个 shiftwidth 宽度
" 具体编辑文件类型的一般设置，比如不要 tab 等
autocmd FileType python,php set tabstop=4 shiftwidth=4 cc=81 expandtab ai
autocmd FileType ruby,html,htm,xml,javascript,css set tabstop=2 shiftwidth=2 softtabstop=2 expandtab ai
autocmd BufRead,BufNewFile *.md,*.mkd,*.markdown set filetype=markdown.mkd
autocmd BufRead,BufNewFile *.part set filetype=html
" disable showmatch when use > in php
au BufWinEnter *.php set mps-=<:>
" -------------------------------------------------------------< 缩进配置  End  >

" -------------------------------------------------------------< 语法配置 Start >
syntax enable
syntax on
filetype indent on
filetype plugin on
filetype plugin indent on
" -------------------------------------------------------------< 语法配置  End  >

" -------------------------------------------------------------< 其他配置 Start >
" 设置标记一列的背景颜色和数字一行颜色一致
hi! link SignColumn   LineNr
hi! link ShowMarksHLl DiffAdd
hi! link ShowMarksHLu DiffChange

" 让Vim的补全菜单行为与一般IDE一致(参考VimTip1228)
set completeopt=longest,menu

" for error highlight，防止错误整行标红导致看不清
highlight clear SpellBad
highlight SpellBad term=standout ctermfg=1 term=underline cterm=underline
highlight clear SpellCap
highlight SpellCap term=underline cterm=underline
highlight clear SpellRare
highlight SpellRare term=underline cterm=underline
highlight clear SpellLocal
highlight SpellLocal term=underline cterm=underline
" ---------------------------------------------------------------< 其他配置 End >

" ----------------------------------------------------------< 自定义快捷键 Start >
let mapleader=','
let g:mapleader=','
inoremap fj <Esc>                      " 替换 Esc
nnoremap ; :
vnoremap < <gv                         " 缩进后再次选中区域
vnoremap > >gv                         " 缩进后再次选中区域

vmap <leader>c "+y                     " <leader>c 复制至公共剪贴板
nmap <leader>a <esc>ggVG"+y<esc>       " <leader>a 复制所有至公共剪贴板
" <leader>v 从公共剪贴板黏贴
imap <leader>v <esc>"+p                " 插入模式下黏贴
nmap <leader>v "+p                     " 普通模式下黏贴
vmap <leader>v "+p                     " 可视模式下黏贴，并替换选区

nmap cS :%s/\s\+$//g<cr>:noh<cr>       " 常规模式下输入 cS 清除行尾空格
nmap cM :%s/<c-v><c-m>$//g<cr>:noh<cr> " 常规模式下输入 cM 清除行尾 ^M 符号
nmap cT <esc>:retab<cr>                " 一键替换全部 Tab 为空格
" ----------------------------------------------------------< 自定义快捷键  End  >

" -------------------------------------------------------------< 习惯配置 Start >
" set mouse-=a                          " 不启用鼠标
" set mouse=a                           " 启用鼠标
" set mousehide                         " 键入的时候隐藏鼠标指针
" set cursorcolumn                      " 突出显示当前列
set cc=80                               " 在 80 行高亮一列，针对某些编程语言
set history=2000                        " 设置 vim 记住的历史数

" 禁用常规模式下的方向键
" noremap <Up> <Nop>
" noremap <Down> <Nop>
" noremap <Left> <Nop>
" noremap <Right> <Nop>

" 禁用插入模式下的方向键
" imap <Up> <Nop>
" imap <Down> <Nop>
" imap <Left> <Nop>
" imap <Right> <Nop>

" 去掉输入错误的提示声音
set novisualbell
set noerrorbells
set t_vb=
set tm=500

" F1 废弃这个键,防止调出系统帮助
" I can type :help on my own, thanks.  Protect your fat fingers from the evils of <F1>
noremap <F1> <Esc>"

" 退出vim后，内容显示在终端屏幕, 可以用于查看和复制, 如果不需要可以关掉
set t_ti= t_te=
" -------------------------------------------------------------< 习惯配置  End  >

" -----------------------------------------------------< 引号括号的自动匹配 Start >
:inoremap ( ()<ESC>i
:inoremap ) <c-r>=ClosePair(')')<CR>
" :inoremap < <><ESC>i
" :inoremap > <c-r>=ClosePair('>')<CR>
:inoremap { {}<ESC>i
:inoremap } <c-r>=ClosePair('}')<CR>
:inoremap [ []<ESC>i
:inoremap ] <c-r>=ClosePair(']')<CR>
:inoremap " ""<ESC>i
:inoremap ' ''<ESC>i
:inoremap ` ``<ESC>i
function! ClosePair(char) 
    if getline('.')[col('.') - 1] == a:char
        return "\<Right>"
    else
        return a:char
    endif
endfunc
" -------------------------------------------------------< 引号括号的自动匹配 End >

" ----------------------------------------------------------< 插件配置前置 Start >
set nocompatible                                      " 禁用 Vi 兼容模式
filetype off                                          " 禁止文件检测
" ----------------------------------------------------------< 插件配置前置  End  >

" ----------------------------------------------------< Vim-plug 插件配置 Start >
call plug#begin('$HOME/vimfiles/plugged')

" ------------------专注简洁模式插件---------------------
Plug 'junegunn/goyo.vim'                              " 禅意插件1   开启 Zen 模式
Plug 'junegunn/limelight.vim'                         " 禅意插件2   开启段落高亮模式，其他代码的黑白
Plug 'leonid-shevtsov/gvimfullscreen_win32'           " 全屏插件，需要将gvimfullscreen.dll复制到具有gvim.exe的目录中
" ----------------------其他插件-----------------------
Plug 'scrooloose/nerdtree'                            " 侧边文件树
Plug 'vim-airline/vim-airline'                        " 状态栏
Plug 'Yggdroot/indentLine'                            " 对齐线
Plug 'junegunn/seoul256.vim'                          " 配色
Plug 'kien/ctrlp.vim'                                 " 查找插件
Plug 'mattn/emmet-vim'                                " 前端神器
Plug 'godlygeek/tabular'                              " 快速对齐插件
Plug 'tpope/vim-surround'                             " 轻松添加两边的符号
Plug 'tpope/vim-commentary'                           " 快速注释
"Plug 'terryma/vim-multiple-cursors'                  " 多个光标同时编辑，原生命令也行，不过这个简化了
Plug 'luochen1990/rainbow'                            " 彩虹括号
Plug 'gregsexton/MatchTag'                            " 高亮两个配对的tag

call plug#end()
" ----------------------------------------------------< Vim-plug 插件配置  End  >

" ---------------------------------------------------< 专注简洁模式插件配置 Start >
let g:goyo_width = 90
" let g:goyo_margin_top = 3
" let g:goyo_margin_bottom = 3

" 开启全屏
nmap <F11> :call libcallnr("gvimfullscreen.dll", "ToggleFullScreen", 0)<CR>

" 只开启goyo
map <C-g> :Goyo<CR>

" limelight
" 在开启 Goyo 的时候自动开启 Limelight
autocmd! User GoyoEnter Limelight
autocmd! User GoyoLeave Limelight!

" 这里只用于窗口透明与置顶
" 需要vimtweak.dll文件，将之拷贝在gvim.exe文件夹下
" 常规模式下 Ctrl + Up（上方向键） 增加不透明度，Ctrl + Down（下方向键） 减少不透明度，<Leader>t 窗口置顶与否切换
if (g:isGUI)
    let g:Current_Alpha = 255
    let g:Top_Most = 0
    func! Alpha_add()
        let g:Current_Alpha = g:Current_Alpha + 10
        if g:Current_Alpha > 255
            let g:Current_Alpha = 255
        endif
        call libcallnr("vimtweak.dll","SetAlpha",g:Current_Alpha)
    endfunc
    func! Alpha_sub()
        let g:Current_Alpha = g:Current_Alpha - 10
        if g:Current_Alpha < 155
            let g:Current_Alpha = 155
        endif
        call libcallnr("vimtweak.dll","SetAlpha",g:Current_Alpha)
    endfunc
    func! Top_window()
        if  g:Top_Most == 0
            call libcallnr("vimtweak.dll","EnableTopMost",1)
            let g:Top_Most = 1
        else
            call libcallnr("vimtweak.dll","EnableTopMost",0)
            let g:Top_Most = 0
        endif
    endfunc

    " 快捷键设置
    map <c-up> :call Alpha_add()<CR>
    map <c-down> :call Alpha_sub()<CR>
    map <leader>t :call Top_window()<CR>
endif
" ---------------------------------------------------< 专注简洁模式插件配置  End  >

" -----------------------------------------------< 设置着色模式和字体,带插件 Start >
" 设置着色模式和字体,带插件
set guifont=Fira_Code:h12
let g:seoul256_background = 233
colo seoul256
" -----------------------------------------------< 设置着色模式和字体,带插件  End  >


" ------------------------------------------------------------< NERDTree Start >
map <F2> :NERDTree<CR>
map <C-F2> :NERDTreeFind<CR>
"自动开启
" autocmd vimenter * NERDTree
" 显示行号
let NERDTreeShowLineNumbers=1
let NERDTreeAutoCenter=1
" 是否显示隐藏文件
let NERDTreeShowHidden=1
"只剩下nerd窗口的时候关闭
autocmd bufenter * if (winnr("$") == 1 && exists("b:NERDTree") && b:NERDTree.isTabTree()) | q | endif
" 设置宽度
let NERDTreeWinSize=30
" 在终端启动vim时，共享NERDTree
"let g:nerdtree_tabs_open_on_console_startup=1
" 忽略一下文件的显示
"let NERDTreeIgnore=['\.pyc','\~$','\.swp']
" ------------------------------------------------------------< NERDTree  End  >

" ----------------------------------------------------------< indentLine Start >
if g:isGUI
    let g:indentLine_char = "┊"
    let g:indentLine_first_char = "┊"
endif
" ----------------------------------------------------------< indentLine  End  >
```