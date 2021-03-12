## Tab, Buffer, Window 操作

#### Tab 操作

```
:tabe filename        新建tab    &&    :tabc        关闭当前的 tab
:tabo       关闭所有其他的 tab    &&    :tabs        查看所有打开的 tab
:tabp       前一个tab            &&    :tabn        后一个 tab
自定：
gt     下一个tab    &&    gT      上一个tab
ngt        快速切换到n号tab
```

#### Buffer 操作

```
:ls         查看buffer
:e b        在vim中使用:edit打开一个文件b，这时vim内容换成文件b的内容
:b1 & :b2   切换buffer，根据buffer排序
:bn/p       下/上一个buffer
:bd 1       删除buffer
```

#### Window 操作

```
//新建一个上下排列的window(水平分割)
:split a //:sp
//新建一个左右排列的window(垂直分割)
:vsplit a //:vsp
PS: window能直接:q退出,buffer退出的话整个窗口都会消失.
    window里也能用buffer操作方式操作
```

- 在window之间切换可以使用Ctrl + w + h/j/k/l（向左、下、上、右切换）或者Ctrl + w + w（在窗口间切换）
- 如果要调整window的大小，分窗口是水平分隔还是垂直分隔两种情况：

> 如果是水平分隔可以使用:nwinc +/-把当前激活窗口高度增加、减少n个字符高度，比如:10winc +
>
> 如果是垂直分隔可以使用:nwinc >/<把当前激活窗口宽度增加、减少n个字符宽度，比如:5winc >