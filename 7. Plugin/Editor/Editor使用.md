## Editor 的使用

传送门----[官网](https://github.com/pandao/editor.md)

#### 编辑器的引入

```html
<!-- 官方 -->
<link rel="stylesheet" href="editor.md/css/editormd.min.css" />
<div id="editor">
    <!-- Tips: Editor.md can auto append a `<textarea>` tag -->
    <textarea style="display:none;">### Hello Editor.md !</textarea>
</div>
<script src="jquery.min.js"></script>
<script src="editor.md/editormd.min.js"></script>
<script type="text/javascript">
    $(function () {
        var editor = editormd('editor', {
            // width: "100%",
            // height: "100%",
            // markdown: "xxxx",     // dynamic set Markdown text
            path: 'editor.md/lib/', // Autoload modules mode, codemirror, marked... dependents libs path
        });
    });
</script>
```

个人使用：

```html
<!-- 个人 -->
<link rel="stylesheet" href="__ADMIN__/plugins/editor/css/editormd.min.css" media="all" />
<div class="layui-form-item layui-form-text">
    <div id="editor" class="layui-input-block">
        <textarea name="content" style="display:none;"></textarea>
    </div>
</div>
<script src="http://libs.baidu.com/jquery/2.0.0/jquery.min.js"></script>
<script src="__ADMIN__/plugins/editor/editormd.min.js"></script>
<script>
    $(function () {
        editormd('editor', {
            // width: "100%",
            height: '600px',
            // markdown: "xxxx",     // dynamic set Markdown text
            path: '__ADMIN__/plugins/editor/lib/', // Autoload modules mode, codemirror, marked... dependents libs path

            // saveHTMLToTextarea: true,
            imageUpload: true,
            imageFormats: ['jpg', 'jpeg', 'gif', 'png', 'bmp', 'webp'],
            imageUploadURL: '/article/uploadimg', // 后端地址
            // saveHTMLToTextarea: true,
            emoji: true,
            taskList: true,
            tocm: true, // Using [TOCM]
            tex: true, // 开启科学公式TeX语言支持，默认关闭
            flowChart: true, // 开启流程图支持，默认关闭
            sequenceDiagram: true, // 开启时序/序列图支持，默认关闭,
        });
    });
</script>
```

#### 前端显示保存的 md 代码

```html
<link rel="stylesheet" href="__ADMIN__/plugins/editor/css/editormd.min.css" media="all" />

<div class="news_infos" id="article">
    <textarea style="display:none;">{$article.content}</textarea>
</div>

<script src="http://libs.baidu.com/jquery/2.0.0/jquery.min.js"></script>
<script src="__ADMIN__/plugins/editor/editormd.min.js"></script>
<script src="__ADMIN__/plugins/editor/lib/marked.min.js"></script>
<script src="__ADMIN__/plugins/editor/lib/prettify.min.js"></script>

<script type="text/javascript">
    var testEditor;
    $(function () {
        testEditor = editormd.markdownToHTML('article', {
            //注意：这里是上面DIV的id
            htmlDecode: 'style,script,iframe',
            emoji: true,
            toc: true,
            tocm: true,
            tocDropdown: false,
            taskList: true,
            htmlDecode: true,
            tex: true, // 默认不解析
            flowChart: true, // 默认不解析
            sequenceDiagram: true, // 默认不解析
            codeFold: true,
        });
    });
</script>
```
