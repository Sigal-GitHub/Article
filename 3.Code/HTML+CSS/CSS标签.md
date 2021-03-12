#### 标签选择器 && Id 选择器

```
span {
    color:red;
}

#sigal {
    color:red;
}
```

#### 类选择器

```
.sigal {
    color:red;
}
```

#### 复合选择器

后代选择器：空格隔开

```
.box p {
    color:red;
}

选择类名为 box 的标签的后代 p 标签
```

交集选择器：连起来写

```
li.spec {
    color:red;
}

选择即是 li 标签，也属于 spec 类的标签
```

并集选择器：逗号隔开

```
ul,ol {
    width:100px;
}

选择所有 ul 和 ol 标签
```

#### 伪类选择器

伪类是添加到选择器的描述性词语，指定要选择的元素的特殊状态，超链有4个特殊状态


* a: link   : 链接的默认样式
* a: visited: 已经访问样式
* a: hover  : 鼠标在链接上的样式
* a: active : 点击链接时候的样式

> 爱恨准则

#### 元素关系选择器

子选择器：> 表示

```
div>p {
    color:red;
}

div 的子标签 p
```

相邻兄弟选择器： + 表示

```
img+p {
    color:red;
}

图片后面紧跟着的段落被选中
```

通用兄弟选择器：~ 表示

```
p~span {
    color:red;
}

p 之后的所有同层级 sapn 元素被选中
```

#### 序号选择器

```
: first-child        : 第一个子元素
: last-child         : 最后一个子元素
: nth-child(3)       : 第三个子元素    ---keyi
: nth-of-type(3)     : 第三个某类型子元素
: nth-last-child(3)  : 倒数第三个子元素
: nth-last-of-type(3): 倒数第三个某类型子元素
```
:nth-child() 可以写成 an + b 的形式，表示从 b 开始每 a 个选一个，注意不能写为 b + an

2n + 1 等于 odd，表示奇数；2n 等价于 even，表示偶数

#### 属性选择器

![20210225122711](http://pic.sigalx.com/pic/20210225122711.png)

#### CSS3 新增伪类

![20210225122748](http://pic.sigalx.com/pic/20210225122748.png)

#### 伪元素

```
::before
::after
::selection
::first-line
::first-letter
```

#### 层叠性和选择器权重

权重：

id 权重 > class 权重 > 标签权重

权重的计算：

![20210225190309](http://pic.sigalx.com/pic/20210225190309.png)

!important 提升权重