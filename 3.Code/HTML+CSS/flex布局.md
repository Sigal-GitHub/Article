[toc]

#### 前言

CSS3 的新盒模型 -- Flexbox

发展：

    2009 - display: box;
    2011 - display:flexbox;
    2012 - display: flex;

#### Flex 布局

该模型的好处：

    使用该模型能轻松的创建自适应浏览器窗口的流动布局或自适应字体大小的弹性布局。

传统的盒模型基于 HTML 文档流在垂直方向上排列盒子，而弹性盒模型可以定义盒子的排列顺序。

Flex 由`伸缩容器`和`伸缩项目`组成，也可以说父容器和子容器。

伸缩容器中每一个子元素都是一个伸缩项目，可以是任意数量的。

伸缩容器外和伸缩项目内的一切元素都不受影响。

伸缩项目沿着伸缩容器内的一个伸缩行定位，通常每个伸缩容器只有一个伸缩行。

![20201204031305](http://pic.sigalx.com/pic/20201204031305.png)

如上图

基本上，伸缩项目是沿着主轴(main axis)，从主轴起点(main-start)到主轴终点(main-end)或沿着侧轴(cross axis)，从侧轴起点(cross-start)到侧轴终点(cross-end)排列。

-   主轴(main axis)：伸缩容器的主轴，伸缩项目主要是沿着这条轴进行排列布局的。此属性受到(justify-content)属性的影响。
-   主轴起点(main-start) 和 主轴终点(main-end)：伸缩项目放置在伸缩容器内从主轴起点到主轴终点的方向。
-   主轴尺寸(main size)：伸缩项目在主轴方向的宽度或高度就是主轴的尺寸，伸缩项目主要的大小属性要么是宽度，要么是高度，由哪个对着主轴方向决定。
-   侧轴(cross axis)：垂直于主轴，它的方向主要取决于主轴。
-   侧轴起点(cross-start) 和 侧轴终点(cross-end)：伸缩行的配置从容器的侧轴起点边开始，到侧轴终点边结束。
-   侧轴尺寸(cross size)：伸缩项目在侧轴方向的宽度或高度就是项目的侧轴长度，伸缩项目的侧轴长度属性是 width 或 height，由哪一个对着侧轴方向决定。

#### 定义 Flex

定义 Flex ： `display: flex | inline-flex;`

分别生成一个块状或行内的 flex 容器盒子。简单说来，如果你使用块元素如 div，你就可以使用 flex，而如果你使用行内元素，你可以使用 inline-flex。

> 定义了 Flex，CSS 中的 columns 属性在伸缩容器上没有效果，同时 float，clear 和 vertical-align 属性在伸缩项目上也没有效果。

#### 伸缩容器属性

-   flex-direction
-   flex-wrap
-   flex-flow
-   justify-content
-   align-items
-   align-content

###### flex-direction：定义伸缩方向

`flex-direction: row | row-reverse | column | column-reverse`

-   row：默认值
-   row-reverse: 方向与 row 相反
-   column: 竖直向下排列
-   column-reverse： 方向与 column 相反

###### flex-wrap：定义行数

`flex-wrap: nowrap | wrap | wrap-reverse;`

-   nowrap : 默认值，单行显示
-   wrap : 多行显示
-   wrap-reverse: 多行显示，方向相反

###### flex-flow：flex-direction 和 flex-wrap 的简写形式

`flex-flow: flex-direction | flex-wrap;`

前面两个属性的集合，默认值为: row nowrap

###### justify-content：定义项目在主轴的对齐方式

`justify-content: flex-start | flex-end | center | space-between | space-around;`

-   flex-start : 居左对齐
-   flex-end : 居右对齐
-   center : 居中对齐
-   space-between: 平均分布在行里，两边不留空间
-   space-around : 平均分布在行里，两边留一半空间

###### align-items: 定义项目在侧轴的对齐方式

`align-items: flex-start | flex-end | center | baseline | stretch;`

-   flex-start: 顶端对齐
-   flex-end : 底部对齐
-   center : 居中对齐
-   baseline : 根据基线对齐
-   stretch : 默认值，拉伸填满整个容器

###### align-content: 定义多行的对齐方式

类似 justify-content, 如果伸缩项目只有一行，那么该属性将不起作用

`align-content: flex-start | flex-end | center | space-between | space-around | stretch;`

#### 伸缩项目属性

###### order: 显示位置

`order:<integer>`

控制项目在容器中出现的顺序

###### flex-grow: 扩展空间

`flex-grow:<number>` 负值也行，默认值是 1

设置此属性的话，伸缩项目会占满整个伸缩容器。伸缩容器设置的对齐方式就会失效

如：

```css
.son1 {
    flex-grow: 1;
}
.son2 {
    flex-grow: 2;
}
```

son2 所占空间是 son1 的 2 倍

###### flex-shrink: 收缩空间

`flex-shrink:<number>` 负值也行，默认值是 1

与 flex-grow 功能相反，超出部分将按比例收缩

如：（菜鸟教程）

```
flex-shrink的默认值为1，如果没有显示定义该属性，将会自动按照默认值1在所有因子相加之后计算比率来进行空间收缩。

本例中A、B、C 显式定义了 flex-shrink 为 1，D、E 定义了 flex-shrink 为 2，所以计算出来总共将剩余空间分成了 7 份，其中 A、B、C 占 1 份，D、E 占 2 份，即1:1:1:2:2

我们可以看到父容器定义为 500px，子项被定义为 120px，子项相加之后即为 600 px，超出父容器 100px。那么超出的 100px 需要被 A、B、C、D、E 消化 通过收缩因子，所以加权综合可得 100*1+100*1+100*1+100*2+100*2=700px。

于是我们可以计算 A、B、C、D、E 将被移除的溢出量是多少：
A 被移除溢出量：(100*1/700)*100，即约等于14px
B 被移除溢出量：(100*1/700)*100，即约等于14px
C 被移除溢出量：(100*1/700)*100，即约等于14px
D 被移除溢出量：(100*2/700)*100，即约等于28px
E 被移除溢出量：(100*2/700)*100，即约等于28px
最后A、B、C、D、E的实际宽度分别为：120-14=106px, 120-14=106px, 120-14=106px, 120-28=92px,120-28=92px，此外，这个宽度是包含边框的。
```

###### flex-basis: 伸缩比例

`flex-basis:<length> | auto` 负值不合法，默认auto

// TODO: 需要深入

###### flex 复合

flex 是 flex-grow，flex-shrink，flex-basis 三个属性的复合属性，默认值是：0 1 auto

`flex: none | [<'flex-grow'>,<'flex-shrink'> || <'flex-basis'>]`

第二第三参数是可选

###### align-self: 对齐方式

与 align-items 的属性值一样

> margin:auto;在 flex 中具有强大的功能，一个定义为 auto 的 margin 会合并剩余的空间，它可以用来把伸缩项目挤到其他位置
