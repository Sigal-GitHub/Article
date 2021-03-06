> Sass 和 Less 都是 CSS 预处理器

好处：

-   添加了原生 CSS 没有的功能
-   使 CSS 更加整洁并且更加可维护
-   有丰富的工具类，如函数等
-   让开发者能有能力生成更复杂的 CSS 样式

#### Sass

特色：

-   完全兼容 CSS3
-   在 CSS 基础上增加变量，嵌套，混合等功能
-   通过函数进行颜色值与属性值的运算
-   提供控制指令等高级功能
-   自定义输出格式

两个后缀，两套语法：.sass .scss

两个都是 Sass，scss 更新，更接近 css，推荐使用

sass 通过缩进语法写，没有大括号什么的

scss 是新语法格式，外形更像 css 的原生写法

#### Sass 安装

Sass 基于 Ruby

先安装 Ruby，要添加到环境变量

#### Sass 编译

1. 命令行编译

略

2. 工具编译

略

3. 自动化编译（常用）

Grunt Gulp webpack

4. VSCode 插件编译（常用）

Easy Sass 插件

5. 常见的编译错误
    - 文件名不能使用中文字符
    - 不支持 GBK 编码，应该将文件设置成 utf-8

#### Sass 使用

在 CSS 属性的基础上，Sass 提供了一些名为 SassScript 的新功能

SassScript 可作用于任何属性，允许属性使用变量，算数运算等额外功能

##### 一. 嵌套规则

-   选择器嵌套

Sass 允许将一套 css 样式嵌套进另一套样式中，内层的样式将它外层的选择器作为父选择器

> 在 Sass 中的嵌套并不是无限的，因为嵌套的层级越深，编译出来的 css 代码层级就越深

-   属性嵌套

适用 CSS 有一些属性前缀相同，只是后缀不一样的属性，如 border，padding，font 等

如：

```scss
header {
    border: {
        top: 1px solid red;
    }
    background-color: blue;

    nav a {
        color: gray;
        &:hover {
            color: red;
        }
    }
}
```

使用 & 代表父选择器，就是当前的上级元素

##### 二. 注释

Sass 支持标准的 CSS 多行注释和单行注释，但单行注释不会被输出到编译后的 css 文件中

##### 三. 变量

-   变量的定义

    通过 $ 符号定义变量：`$width: 100px;`

-   变量的调用

    ```css
    div {
        width: $width;
    }
    ```

-   默认变量

    在变量的后面加上`!default`就是默认变量

    如果此变量在之前有值，则不会被重新赋值，用之前的值

    如果没有值或者为空，这个变量就是默认的值

-   变量的作用域

    Sass 中变量支持块级作用域，嵌套规则内定义的变量只能用在嵌套呢，就是局部变量

    不在嵌套规则内定义的变量则在任何地方都可以使用，也就是全局变量

    可以通过`!global`将局部变量改为全局变量

##### 四. 数据类型

1. 数字 1,2,10px
2. 字符串 有引号字符串和无引号字符串
3. 颜色 blue,#ffffff,rgba(0,0,0,1)
4. 布尔 true,false
5. 空 null
6. 数组 list，用空格或者都好隔开
7. maps 相当与 js 中的 object

如定义颜色的数组类型

`$color: #ccc blue #000;`

##### 五. 运算

-   数字运算

加减乘除

需要注意除法的作用：

除法中的运算需要用括号括起来，因为 / 符号在 css 中有其他意义，如`font: (10px/2)`，就需要加括号

如果有变量或者函数参与，则不会报错，如`width: $width/2; ` or `width: round(4)/2;`

如果这个/用于另一个算数表达式的一部分，则可以不加括号，如`width: 100px+200px/2`

如果要使用 css 的 / 怎么做？可以使用#{}插入

如：输出就是 `font: 16px/700;`

```css
div {
    $font-size:16px;
    $font-weight: 700;
    font:#{$font-size}/#{$font-weight};
}
```

减法的区别：

![20210328022129](http://pic.sigalx.com/pic/20210328022129.png)

> 运算需要单位相同


> 颜色也是可以计算的，但颜色是分段计算，如#010203 + #040506 = #040709,只能运算16进制的，如果是rgb的，则会转换成16进制再算

> 加号可以用来做字符串的拼接，字符串有没有引号取决与第一个字符串，第一个有引号，结果就有，反之

##### 六. 插值语句

使用 #{} 插值语句可以在选择器或者属性名中使用变量

```scss
$name: "box";
$attrname: "border";
p.#{$name} {
    #{$attrname}: 1px solid red;
}
```

##### 七. @-Rules 概念

> Sass 支持所有的 css3 中的 @ 规则，以及一些 sass 专属的规则，也被称作“指令（directives）”

