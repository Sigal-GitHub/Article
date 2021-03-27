## HTML5语义化

##### HTML5新增的语义化结构标签

名称 | 说明
-: | :-:
header | 表示页面中的内容区块，或者整个页面的标题
footer | 表示整个页面或页面中的一个内容块注脚，一般来说它会包含创作者的姓名，创作日期以及创作者联系信息
section | 表示页面中的一个内容区块，如章节，页眉，页脚或页面中的其他部分。它可以与h1-h6等元素组合使用，标识文档结构
article | 表示页面中的一块以上下文不相关的独立内容，如博客中的一篇文章或报纸中的一篇文章
aside | 表示article标签的内容之外的，与article标签的内容相关的辅助信息
nav | 表示页面中导航链接的部分
main | 表示网页中的主要内容。主要内容区域指与网页标题或应用程序中本页面主要功能直接相关或进行扩展的内容
figure | 表示一段独立的流内容，一般表示文档主体流内容中的一个独立单元。可以使用figcaption标签为figure标签组添加标题

## 为什么要语义化HTML结构？
1. 使文档结构更加的清晰明确，容易阅读
2. 可以简化HTML的页面设计，明确的语义化更适合搜索引擎检索和抓取

## article标签
article标签用来表示文档，页面中的独立的，完整的，可以独自被外部引用的内容，它可以是一篇博客或者报刊文章，一篇论坛的帖子，一段用户的评论或者独立的插件等等。另外，一个article标签通常有它自己的标题，一般放在header标签里面，有时候还有自己的footer，当article标签嵌套使用的时候，内部的article标签内容必须和外部的内容相关。并且article支持HTML5全局属性。

###### 使用article设计页面：
```
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>新闻</title>
</head>
<body>
  <aritcle>
    <header>
      <h1>新闻标题</h1>
      <time pubdate="pubdate">0000-00-00 00:00</time>
    </header>
    <p>新闻内容</p>
    <footer>新闻尾部，版权，链接等</footer>
  </aritcle>
</body>
</html>
```
此例子是一篇新闻的例子，整个例子的内容比较独立，所以使用article标签。

article标签可以嵌套使用，里层的内容原则上需要与外层的内容相关联。

###### 在上面代码的基础上使用article标签嵌套

```
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>新闻</title>
</head>
<body>
  <aritcle>
    <header>
      <h1>新闻标题</h1>
      <time pubdate="pubdate">0000-00-00 00:00</time>
    </header>
    <p>新闻内容</p>
    <footer>新闻尾部，版权，链接等</footer>
    <section>
      <h2>评论</h2>
      <article>
        <header>
          <h3>用户名称</h3>
          <time pubdate="pubdate">评论发布时间0000-00-00 00:00</time>
        </header>
        <p>用户评论内容块</p>
      </article><!-- 第一个用户评论完毕 -->
      <article>
        <header>
          <h3>用户名称</h3>
          <time pubdate="pubdate">评论发布时间0000-00-00 00:00</time>
        </header>
        <p>用户评论内容块</p>
      </article><!-- 第二个用户评论完毕 -->
    </section>
  </aritcle>
</body>
</html>
```

此例子比上述例子更完整，添加了评论内容。

使用section标签区分文章与评论部分，而评论里面每个评论又相对的独立，所以每个评论使用article标签包裹，标题与评论内容分别用header标签和p标签包裹。也可以使用article标签表示插件，作用是使得插件看起来好像内嵌在网页一样。

## section标签
section标签用于对网站或者应用程序中页面上的内容进行分区，但section标签并非一个普通的容器，当一个容器需要被直接定义样式或者通过脚本定义行为的时候，推荐使用div，而非section。
> div关注结构的独立性，而section关注内容的独立性，section包含的内容可以单独存储到数据库中或者输出到word文档中。

###### 使用section标签定义内容块

```
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>section</title>
</head>
<body>
  <section>
    <h1>此内容块的标题</h1>
    <ol>
      <li>
        <h3>分类标题1</h3>
        <span>分类内容1</span>
      </li>
      <li>
        <h3>分类标题2</h3>
        <span>分类内容2</span>
      </li>
      <li>
        <h3>分类标题3</h3>
        <span>分类内容3</span>
      </li>
      <li>
        <h3>分类标题4</h3>
        <span>分类内容4</span>
      </li>
    </ol>
  </section>
</body>
</html>
```

section标签需要包含一个hn标签，一般不用包含header或者footer。通常使用section为那些有标题的内容进行分段。section的作用是对内容分块处理，如对文章分段等，相邻的section标签的内容，应该是相关的，而不是像article那样独立的。

而能否使用seciton或者article来代替div使用？不能，div的用处就是用来布局网页，划分区域，而HTML5添加section和article等标签，让div的工作更加专业，div用来布局大块内容，在不同的内容块中，按需求添加article或section等标签，并显示其中的内容。因此，使用section时候需要注意以下问题：
	1. 不要将section当作设置样式的页面容器，对此类操作应该使用div标签实现。
	2. 如果article，aside，nav标签更符合使用条件，就不要使用section。
	3. 不要为没有标题的内容块使用section标签。

## nav标签
nav是一个可以用作页面导航的链接组，其中的导航元素链接到其他页面或者当前页面的其他部分，并不是所有的链接组都要被放进nav里面，只需要将主要的，基本的链接组放进nav即可。一个页面可以拥有多个nav，作为页面整体或不同部分的导航。

具体来说，nav可以用于一下的场合：

    1.传统的导航条
    2.侧边栏导航
    3.页内导航
    4.翻页操作

需要注意的是：在HTML5中不要使用menu来代替nav，menu主要使用在一系列的交互命令菜单上，比如使用在web应用程序中。

## aside标签
aside标签用来表示当前页面或文章的附属信息部分，它可以包含与当前页面或主要内容相关的引用，侧边栏，广告，导航条，以及其他类似的有别于主要内容的部分。

aside主要有一下两种使用方法：

	1.作为主要内容的附属信息部分，包含在article中，其中的内容可以是与当前文章有关的参考，名词解释等。
	2.作为页面或站点全局的附属信息部分，在article外使用，最典型的就是侧边栏，其中的内容可以是友情链接，博客中的其他文章列表，广告单元等。

例子：
```
方法1：
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>aside使用方法1</title>
</head>
  <header>页面标题</header>
  <article>
    <h1>文章标题</h1>
    <p>文章内容</p>
    <aside>
      <h1>该文章的名词解释标题</h1>
      <dl>
        <dt>名词1</dt>
        <dd>名词解释1</dd>
      </dl>
      <dl>
        <dt>名词2</dt>
        <dd>名词解释2</dd>
      </dl>
    </aside>
  </article>
</body>
</html>

方法2：
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>aside使用方法2</title>
</head>
  <aside>
    <nav>
      <h1>友情链接</h1>
      <ul>
        <li><a href="">网站1</a></li>
        <li><a href="">网站2</a></li>
        <li><a href="">网站3</a></li>
      </ul>
    </nav>
  </aside>
</body>
</html>
```

## main标签
main标签表示网页中的主要内容，指与网页标题或应用程序中本页主要功能直接相关或进行扩展的内容，该区域应该为每一个网页中特有的内容，不能包裹整个网站的导航条，版权信息，网站logo，公共搜索等整个网站内部的共有内容。每个网页只能防止一个main标签，不能将main标签放置在任何nav，article，section，aside，footer，header标签内。

例如：

```
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>main使用例子</title>
</head>
  <header>
    <nav>网页导航</nav>
  </header>
  <main>
    <h1>科技新闻</h1>
    <nav>
      <ul>
        <li><a href="">互联网</a></li>
        <li><a href="">自媒体</a></li>
        <li><a href="">创新科技</a></li>
      </ul>
    </nav>
    <h2>互联网</h2>
    <h3>互联网副标题</h3>
    <p>互联网内容</p>

    <h2>自媒体</h2>
    <h3>自媒体副标题</h3>
    <p>自媒体内容</p>

    <h2>创新科技</h2>
    <h3>创新科技副标题</h3>
    <p>创新科技内容</p>
  </main>
  <footer>版权信息</footer>
</body>
</html>
```
上面例子主要使用main包裹页面的主要区域，更利于网页内容的语义区分，同时搜索引擎也能主动抓取主要的信息，避免被辅助性文字的干扰。

## header标签
header标签是一种具有引导和导航作用的结构标签。通常用来放置整个页面或页面内的一个内容区块的标题，但也可以包含其他内容，如网页logo，搜索表单，数据表格等。（hgroup,table,form,nav,h1~h6）

## hgroup标题组标签
hgroup可以为标题或者子标题进行分组，通常它与h1~h6组合使用。如果文章只有一个标题，则不需要使用hgroup。

## footer标签
footer标签可以作为内容块的注脚，也可以作为整个页面的注脚，注脚信息有很多种，如作者，相关阅读，版权信息等。footer与header类似，可以在article，section中添加。

## address标签
address用来在文档中定义联系信息，包括文档作者，文档编辑者，电子邮箱，真实地址，电话号码等，还可以描述与文档相关的联系人的所有联系信息。

## time标签
time标签用来无歧义的，明确的对机器的日期和时间进行编码，并且让人易读的方式来展现。可以使用time来定义发布日期，如文章的发布，网站的发布等，还可以表示其他用途的时间，如通知，约会等。