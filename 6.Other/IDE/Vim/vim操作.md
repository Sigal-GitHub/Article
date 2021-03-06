## Vim常用操作

#### 编辑

```
在光标当前位置输入 i      I 行首输入
在光标当前位置的下一格输入 a    A 行末输入
在光标当前位置所在行的下一行开始输入 o
在光标当前位置所在行的上一行开始输入 O
进入编辑模式后，vim左下角出现 – INSERT –，此时可以像在普通编辑器里一样开始写代码了。因为键盘输入直接被写在了当前的文件里，所以vim命令此刻都“失效”了。
退出编辑模式的命令 ESC
除了O/o，插入命令(A,a,I,i)接受数值参数，如：5Ihello，然后按ESE键。会在行首输入5个连接的hello
```

#### 移动

```
直接移动到当前所在行的头部 0 (数字零) 或者 ^
直接移动到当前所在行的尾部 $    &&    3$：移动到3行后的行尾
光标跳转到目标行 数字gg，如跳到第74行,则输入 74gg
光标跳转到文件头部 gg    &&    光标跳转到文件尾部 G    &&    33G：跳转到33行   此时按"可以返回到原来行
nG跳转后，可使用``（两个反斜）回到上一次的位置，''(两个单引号)功能一样，不过只是回到前次位置所在行的开头，而不是确定的位置上
跳转到上一个编辑处 ctrl o    &&    跳转到下一个编辑处 ctrl i
+：移到下一行的行首    &&    -： 移到上一行的行首
跳到下一个单词的开头 w    &&    跳到前一个单词的开头 b    &&    e/E: 到单词的结尾
W/B    只区分空格和换行，不区分符号跳转
nb:向前移动n个单词    &&    nw：向后移动n个单词
跳转到行内某个字母(行内查找) f 所要查找的内容，如跳到当前光标所在行的a字母所在处: fa
然后按;(分号)跳转到下一个a，按,(逗号)跳转到上一个a
# 到与当前单词相同的上一个单词上    &&    * 到与当前单词相同的下一个单词上
' 移动到上一次的修改行
%: 移动到与制匹配的括号上去（），{}，[]，<>等
fx 向右跳到本行字符x处（x可以是任何字符）    &&    Fx 向左跳到本行字符x处（x可以是任何字符）
tx 和 fx 相同，区别是跳到字符x前    &&    Tx 和 Fx 相同，区别是跳到字符x后
zz:将当前行滚动于屏幕中间，方便查看上下文  zt置顶，zb置尾
H、M、L分别移动到屏幕的顶部、中间和尾部    &&    nH、nL 移动到距离屏幕顶部和顶部n行的位置
n|：移动到当前行的第n列    &&    Enter：到下一行的第一个字符
```

#### 窗口命令(大小调整命令只在打开多个窗口时生效)

```
增加窗口宽度 ctrl w > 或者ctrl w 数字 > 。加入数字后可以快速增加宽度
减小窗口宽度 ctrl w < 或者ctrl w 数字 < 。加入数字后可以快速减小宽度
增加窗口高度 ctrl w + 或者ctrl w 数字 + 。加入数字后可以快速增加高度
减小窗口高度 ctrl w - 或者ctrl w 数字 - 。加入数字后可以快速增加高度
跳转到上窗口 ctrl w k    &&    跳转到下窗口 ctrl w j
跳转到左窗口 ctrl w h    &&    跳转到右窗口 ctrl w l
在竖直方向打开新窗口 vsp <所要打开的文件路径>    &&    在水平方向打开新窗口 sp  <所要打开的文件路径>
```




#### 查找 

```
/ 需要查找的内容(默认向下查找)    &&    ?/ 向上查找
例如要查找单词hello，则输入/hello ,再按回车键
查找当前光标所在位置的单词 gd
在查找到的结果中快速移动光标:    上移 n    &&    下移 N
* ：查找下一个光标所在单词    &&    #是查找上一个
取消查找内容高亮 :noh
```

#### 复制黏贴删除撤销替换

```
复制当前光标所在行 yy
yaw 复制单词,光标在单词任意位置  &&  ynw 复制N个单词  &&  ynj 向下复制n行
ynk 向上复制n行         &&    ynl 向后复制n个字符
剪切当前光标所在行 dd    &&    D 删除到行尾 
dw:删除一个单词（光标后部分）不如：daw实用(删除一整个单词)
d4w：删除4个单词    &&    d$:删除当前光标到行尾    &&    d^：删除当前光标至行首
d换成c效果是一样的，只是操作完会变成insert模式
dnw：删除N个单词    &&    dnj: 向下删除n行    &&    dnk: 向上删除n行
d/it：向后删除到it之前的位置（不删it）    &&    d?it：向前删除到it之前的位置（删除it）
dfi：向右删除第一个i的位置（包括i)        &&    dti：同dfi，只是不包括i
剪切当前光标选中的字符 x 删除3个字符就是3x    &&    剪切并进入INSERT模式 s
U：会恢复一整行原先的面貌，即最原始的样子
P：粘贴至光标前    &&    p：粘贴至光标后    &&    3P：粘贴3次
J:删除换行符，使下一行并上来    &&    nJ:连接后面的n行（从本行算起）
caw:改写单词 c 相当于 d 变为编辑模式
u:撤销上一次操作    &&    U:撤销当前行的所有修改    &&    ctrl+r:对撤消的撤消
D：d$ 的简写，同样的，C：c$的简写    &&    Y：相当于yy，不同于D与C的操作方法
s:删除一个字符，并进入编辑模式       &&    S：删除一整行，进入编辑模式，相当于cc
ns:删除后面n个字符，并进入编辑模式
r:替换当前字符，但不会进入insert模式    &&    3r:把后面3个字符替换掉
替换光标当前位置字符 r 然后输入要替换的字母。 例如，要替换"hello world"中的d为o，则先将光标移动到d，然后按r，然后再o

vim中Nyy可以复制光标后的N行。有时我们不容易得出行数，这时可以用做标记的方法来制定复制范围： 
　　1. 在开始行上输入ma作一个标记a 
　　2. 移动到结束行，输入y'a会复制当前行到标记a之间的文本。d'a会删除。 
或者是v进入可视模式，再13G跳转到相应行，y即可
:10,20y    回车即可，相应的删除也是如此     :10,20d     （此方法比上面两种方法更简单）

:10,20 m 30    把10行到20行的内容，剪切到30行之后
:10,20 co 30   把10行到20行的内容，复制到30行之后

~:更改字母的大小写，同时光标进入到下一个字符    &&    n~:把后面n个字母的大小写状态改变。
```










#### 宏录制

```
:ab && :abbr (定义的宏只能作用在插入模式下) 定义后点击非字符按键发生作用

如果你要重复键入一个短语或一个句子, 也有一种快捷的方法。Vim有一种记录宏的机制。你键入"qa"开始把一段宏记录入寄存器变量`a'中。
按下来你可以象平常一样键入你要的操作, 只是这些操作都会被Vim记录进它命名为`a'的宏中, 再次再下"q"键, 就结束了宏`a'的录制。当你要重复执行你刚才记录的那些操作时只要使用"@a"命令。共有26个可用的寄存器供你记录宏。 使用宏你可以重复多个不同的操作。而不仅仅是插入文本了。如果你要进行某种重复的操作, 也可以使用

:ab hw hello world  用一个缩写字符串代替一个长的字符串，此处用 hw 代替 hello world
:ab 不带参数，直接列出定义了的缩略词  &&  取消定义 :unab hw

:map (定义的宏可以作用在所有模式下)

:map lv 0v$ 
解析：0代表光标移至行首，v就是visual模式（该模式下可以通过hjkl来选中文本），$代表行尾，这样一来，在normal模式输入lv就能选中光标所在行了

:map 列出所有已定义的映射命令
:unmap lv 取消lv映射的命令
:mapclear  清空所有映射

注意：
默认情况下，map命令是作用在normal模式下的
如果是想在virsual模式下新建某个命令的宏，可以使用:vmap，举例：:vmap d <esc>dd就可以在virsual模式下把光标所在行删除。<esc>是纯粹的5个原始字符，意思是回到normal模式。
默认情况下，map是采用递归映射的，比如a映射成b，:map a b，然后c 又映射成了a，:map c a ，那么最终c也会自动映射成b，等同于:map c b，您现在可以试一试a,b,c的效果都是光标向前移动一个单词的长度。如果要不想使用递归，那么就要用:noremap

:map <C-a> <Esc>ggVG   实现类似于Widnows下的Ctrl+a全选 
:inoremap ( ()<esc>i   插入模式下输入'('后自动补全')'，同理还可以实现'['，'{'
```

#### 其他操作

```
ctrl+u\d  向上\下滚动半屏    &&    ctrl+e\y  向上\下滚动一行    &&    ctrl+b\f  向上\下滚动一屏
% 匹配到相应括号处
将光标放在 { 处，然后输入v%就可以把大括号中内容选定
Ctrl + G        显示当前位置
ctrl + n        自动补全 ctrl + p 也一样
Ctrl + o        临时变成命令模式（一次而已）
：e!:           放弃更改，然后相当于重新打开
：help:         帮助，可用ZZ退出帮助窗口
如果光标放在第一个s上，想删除到“(”为止，则输入dt(就可以了，t(的作用是跳到下一个"("前
Ctrl+z:暂停vi,回到Unix提示符，再输入fg即可回到vi   -----linux
缩进：  选择后使用  >> && << 
:3<< 把下面3行（包括本行），向左移动一段距离    &&    :20,30>> 把20行到30行向右移动一段距离
重复执行命令或者重复上一次操作：.
相换两个相邻字母的位置：xp
```





#### 一些命令行例子
```
:s/str1/str2/g   替换当前行的 str1为 str2    &&    :%s/str1/str2/g   替换每一行的 str1为 str2
:10,20s/str1/str2/g 替换从行10到行20之间的str1为tr2
:10,$s/str1/str2/g  替换从行10到最后一行之间的str1为str2

:10,$ w test2.cpp   取行10到最后一行内容，保存到test2.cpp
:r class/User.hpp   读取文件中的内容，插入到当前行的后面

删除包含keyword字符串的行： :g/keyword/d    &&    删除空行：:%s/^\n$//g
```
#### Visual模式

```
v：进入Visual模式    &&    V:进入可视行模式，比如 Vjjd 删除3行    &&    Ctrl+v：可视块模式
进入模式后：选中后按y复制，按x或者d剪切

可视块模式常常用于快速注释代码:
光标移动到需要注释的代码的第一行的开头: ctrl v
j命令下移至需要注释代码的最后一行，I命令，然后输入//，再ESC
(注意，需要过n秒才会生效)
快速缩进多行代码（操作同上，不过// 换成空格）
```
