```
{
    // 全局配置
    "debug.toolBarLocation": "docked", // 将调试的控制条放在左侧栏顶部
    "window.menuBarVisibility": "toggle", // 隐藏菜单栏 Mac 下比较适用，win10也行，可以按 ALT 显示出来
    "editor.rulers": [80], // 在第81个字符时显示垂直标尺
    // "editor.formatOnSave": true,     // 设置保存时格式化
    //"window.titleBarStyle": "native",     // 让标题栏回到原生的样子，mac linux 下用会美观一些

    // 更改设置时候的显示，Ctrl + , 直接调出 json 文件
    // "workbench.settings.useSplitJSON": true,
    // "workbench.settings.editor": "json",

    // 主题 && 图标
    "workbench.colorTheme": "Panda Syntax",
    "workbench.iconTheme": "material-icon-theme",

    // 字体
    "editor.fontSize": 14, //字体大小，默认14
    "editor.fontWeight": "normal", // 字体粗细
    "editor.fontFamily": "Fira code", // 字体类型
    "editor.fontLigatures": "true", // 是否启用字体连字

    // PicGo
    "picgo.picBed.current": "aliyun", // 配置服务商名称，要配置 PicGo 支持的服务商
    "picgo.picBed.aliyun.area": "oss-cn-shenzhen", // 配置服务器地域
    "picgo.picBed.aliyun.bucket": "sigal-picbed", // 配置 OSS 对象名称
    "picgo.picBed.aliyun.path": "pic/", // 配置需要保持到远程 OSS 对象的文件路径
    "picgo.picBed.aliyun.accessKeyId": "xxx",
    "picgo.picBed.aliyun.accessKeySecret": "xxx",
    "picgo.picBed.aliyun.customUrl": "xxx", // 如果 OSS 绑定了域名，就填绑定的域名

    //Project Manager
    "projectManager.sortList": "Name", // 按名称排序, Saved,Name,Path,Recent

    "php.suggest.basic": false, // 禁用 VS Code 自带的 PHP 语法提示，避免功能重复

    // PHP 智能支持 内置的 PHP Language Features 插件需要配置这个，禁用插件的话就不必要
    "php.validate.executablePath": "D:\\phpstudy\\Extensions\\php\\php7.3.4nts\\php.exe",

    // PHP IntelliSense php 版本是7+
    // "php.executablePath": "D:\\phpstudy\\Extensions\\php\\php7.3.4nts\\php.exe",

    // 设置每种语言默认的格式化插件，就可以直接使用 VS Code 默认快捷 Shift + Alt +F 格式化d，不用自己映射
    "[html]": {
        "editor.defaultFormatter": "vscode.html-language-features"
    },
    "[php]": {
        "editor.defaultFormatter": "bmewburn.vscode-intelephense-client"
    },
    "[jsonc]": {
        "editor.defaultFormatter": "esbenp.prettier-vscode"
    },
    "[css]": {
        "editor.defaultFormatter": "esbenp.prettier-vscode"
    },
    "[less]": {
        "editor.defaultFormatter": "esbenp.prettier-vscode"
    },
    "[javascript]": {
        "editor.defaultFormatter": "esbenp.prettier-vscode"
    },
    "[sess]": {
        "editor.defaultFormatter": "esbenp.prettier-vscode"
    },

    // Prettier 未完成
    "prettier.printWidth": 100, // 超过最大值换行
    "prettier.tabWidth": 4, // 缩进字节数
    "prettier.useTabs": false, // 缩进不使用tab，使用空格
    "prettier.semi": true, // 句尾添加分号
    "prettier.singleQuote": true, // 使用单引号代替双引号
    "prettier.proseWrap": "preserve", // 默认值。因为使用了一些折行敏感型的渲染器（如GitHub comment）而按照markdown文本样式进行折行
    "prettier.arrowParens": "avoid", //  (x) => {} 箭头函数参数只有一个时是否要有小括号。avoid：省略括号
    "prettier.bracketSpacing": true, // 在对象，数组括号与文字之间加空格 "{ foo: bar }"
    "prettier.disableLanguages": ["vue"], // 不格式化vue文件，vue文件的格式化单独设置
    "prettier.endOfLine": "auto", // 结尾是 \n \r \n\r auto
    // "prettier.eslintIntegration": false, //不让prettier使用eslint的代码格式进行校验
    "prettier.htmlWhitespaceSensitivity": "ignore", //设置在 html 中所有空格不敏感，默认是 css
    "prettier.ignorePath": ".prettierignore", // 不使用prettier格式化的文件填写在项目的.prettierignore文件中
    "prettier.jsxBracketSameLine": false, // 在jsx中把'>' 是否单独放一行
    "prettier.jsxSingleQuote": false, // 在jsx中使用单引号代替双引号
    // "prettier.parser": "babylon", // 格式化的解析器，默认是babylon
    "prettier.requireConfig": false, // Require a 'prettierconfig' to format prettier
    // "prettier.stylelintIntegration": false, // 不让prettier使用stylelint的代码格式进行校验
    "prettier.trailingComma": "es5", // 在对象或数组最后一个元素后面是否加逗号（在ES5中加尾逗号）
    // "prettier.tslintIntegration": false, // 不让prettier使用tslint的代码格式进行校验
    // 未完，安装 Eslint 或 Vetur 还需要配置

    // Live Server
    // 打开：Alt + l Alt + o
    // 关闭：ALt + l Alt + c
    // Mac 是 cmd
    "liveServer.settings.donotShowInfoMsg": true, //禁止显示提示信息

    // Todo Tree
    // 默认主题配置
    "todo-tree.highlights.defaultHighlight": {
        "icon": "gift",
        "type": "line", // 显示高亮范围，默认是 tag，tag | line | text | tag-and-comment | text-and-comment | whole-line
        // "foreground": "red", // 显示高亮颜色设置 -- 前景色
        "background": "white", // 显示高亮颜色设置 -- 背景色
        "opacity": 10, //背景透明
        "iconColour": "#EBD6D6", // 显示图标的颜色设置
        "gutterIcon": true // 设置为  true，在文件行数那一列显示 todo 图标
    },
    // 分类主题配置
    "todo-tree.highlights.customHighlight": {
        "TODO": {
            // 在标识处有功能代码待编写，待实现的功能在说明中会简略说明的
            "icon": "tasklist",
            "foreground": "#00FFFF",
            "iconColour": "#00FFFF"
        },
        "FIXME": {
            // 标识处代码需要修正，甚至代码是错误的，不能工作，需要修复，如何修正会在说明中简略说明码
            "icon": "smiley",
            "foreground": "#FF5151",
            "iconColour": "#FF5151"
        },
        "XXX": {
            // 虽然实现了功能，但是实现的方法有待商榷，希望将来能改进，要改进的地方会在说明中简略说明
            "icon": "check",
            "foreground": "#FFFF37",
            "iconColour": "#FFFF37"
        } // 只用这三个
    },

    // Vim
    "vim.easymotion": true, // 开启 EasyMotion 插件，默认不开启
    // <leader><leader> s <char> 搜索字符，上下都有
    // <leader><leader> f <char> 向下查找字符
    // <leader><leader> F <char> 向上查找字符
    // <leader><leader> t <char> 向下跳转到某个字符之前
    // <leader><leader> T <char> 向上跳转到某个字符之前
    // <leader><leader> w 向下跳转到单词首字母
    // <leader><leader> b 向上跳转到单词首字母
    // <leader><leder> l 向下匹配单词开头与结尾字母，_与#作为连接，右边字符也显示
    // <leader><leder> h 向上匹配单词开头与结尾字母，_与#作为连接，右边字符也显示
    // <leader><leader> e 向下跳转到单词尾字母
    // <leader><leader> ge 向上跳转到单词尾字母
    // <leader><leader> j 向下跳转到行首字母
    // <leader><leader> k 向上跳转到行首字母
    // <leader><leader><leader> j 上下文匹配单词开头结尾，会解析驼峰字符 l + h 既视感
    "vim.easymotionMarkerBackgroundColor": "#BF616A", // 设置高亮标记时候的颜色
    // 默认开启了 vim-surround 插件
    // ysw" 光标在首字母的时候使用 " 包裹整个单词
    // ds“ 删除 ”
    // cs"' 将 " 替换成 "
    "vim.useSystemClipboard": true, // 开启系统剪切板
    "vim.useCtrlKeys": true, // 启用Vim ctrl键以覆盖常见的VS Code操作，默认是：true，如 ctrl+f，ctrl+v 失效就关这个，或者在 vim.handleKeys 里单独配置
    "vim.hlsearch": true, // 是否高亮搜索 :noh 取消高亮
    // 插入模式键绑定
    "vim.insertModeKeyBindings": [
        {
            "before": ["f", "j"],
            "after": ["<Esc>"]
        }
    ],
    // 普通模式键绑定
    "vim.normalModeKeyBindingsNonRecursive": [
        {
            "before": [";"],
            "after": [":"]
        },
        // 下两个快捷启用了的话，VS Code 自带的Ctrl + PageUp / Ctrl + PageDown 就失效了
        {
            // 下一个标签页
            "before": ["<Tab>"],
            "after": ["g", "t"]
        },
        {
            // 上一个标签页
            "before": ["<Shift+Tab>"],
            "after": ["g", "T"]
        }
    ],
    "vim.leader": ",", // 设置 <leader> 为 ,
    // 是否开启 Vim 原生快捷键：true | false
    // false 就是不开启，使用 vs code 的快捷
    "vim.handleKeys": {
        // 上面启用了 useCtrlKeys ，所以如果有冲突，需要在这里配置
        "<C-a>": false, // 如注释这句话，并 useCtrlKeys 为 true 时，Ctrl + a 全选不起作用了
        "<C-f>": false,
        "<C-c>": false,
        "<C-b>": false,
        "<C-x>": false,
        "<C-k>": false
    },
    "window.zoomLevel": 0,
    "[json]": {
        "editor.defaultFormatter": "esbenp.prettier-vscode"
    } // 未完；根据使用过程发现的冲突不断添加
}
```

新备份

```
{
    // 全局配置
    "debug.toolBarLocation": "docked", // 将调试的控制条放在左侧栏顶部
    "window.menuBarVisibility": "toggle", // 隐藏菜单栏 Mac 下比较适用，win10也行，可以按 ALT 显示出来
    "editor.rulers": [80], // 在第81个字符时显示垂直标尺
    // "editor.formatOnSave": true,     // 设置保存时格式化
    //"window.titleBarStyle": "native",     // 让标题栏回到原生的样子，mac linux 下用会美观一些

    // 更改设置时候的显示，Ctrl + , 直接调出 json 文件
    // "workbench.settings.useSplitJSON": true,
    // "workbench.settings.editor": "json",

    // 主题 && 图标
    "workbench.colorTheme": "Bear Theme",
    "workbench.iconTheme": "Monokai Pro Icons",

    // 字体
    "editor.fontSize": 14, //字体大小，默认14
    "editor.fontWeight": "normal", // 字体粗细
    "editor.fontFamily": "Fira code", // 字体类型
    "editor.fontLigatures": "true", // 是否启用字体连字

    // PicGo
    "picgo.picBed.current": "aliyun", // 配置服务商名称，要配置 PicGo 支持的服务商
    "picgo.picBed.aliyun.area": "oss-cn-shenzhen", // 配置服务器地域
    "picgo.picBed.aliyun.bucket": "sigal-picbed", // 配置 OSS 对象名称
    "picgo.picBed.aliyun.path": "pic/", // 配置需要保持到远程 OSS 对象的文件路径
    "picgo.picBed.aliyun.accessKeyId": "LTAI4GKDXWXBCfmCjLLWTBzY",
    "picgo.picBed.aliyun.accessKeySecret": "cmvOQyGk5cSroLluZ8ofEDHIONcRyp",
    "picgo.picBed.aliyun.customUrl": "http://pic.sigalx.com", // 如果 OSS 绑定了域名，就填绑定的域名

    // json如果格式正确还提示ts的冒号错误，就关闭这个
    "javascript.validate.enable": false,
    //Project Manager
    "projectManager.sortList": "Name", // 按名称排序, Saved,Name,Path,Recent

    "php.suggest.basic": false, // 禁用 VS Code 自带的 PHP 语法提示，避免功能重复

    // PHP 智能支持 内置的 PHP Language Features 插件需要配置这个，禁用插件的话就不必要
    "php.validate.executablePath": "D:\\phpstudy_pro\\Extensions\\php\\php7.3.4nts\\php.exe",

    // PHP IntelliSense php 版本是7+
    // "php.executablePath": "D:\\phpstudy_pro\\Extensions\\php\\php7.3.4nts\\php.exe",

    // 设置每种语言默认的格式化插件，就可以直接使用 VS Code 默认快捷 Shift + Alt +F 格式化d，不用自己映射
    "[html]": {
        "editor.defaultFormatter": "vscode.html-language-features"
    },
    "[php]": {
        "editor.defaultFormatter": "bmewburn.vscode-intelephense-client"
    },
    "[jsonc]": {
        "editor.defaultFormatter": "esbenp.prettier-vscode"
    },
    "[css]": {
        "editor.defaultFormatter": "esbenp.prettier-vscode"
    },
    "[less]": {
        "editor.defaultFormatter": "esbenp.prettier-vscode"
    },
    "[javascript]": {
        "editor.defaultFormatter": "esbenp.prettier-vscode"
    },
    "[sess]": {
        "editor.defaultFormatter": "esbenp.prettier-vscode"
    },

    // Prettier 未完成
    "prettier.printWidth": 100, // 超过最大值换行
    "prettier.tabWidth": 4, // 缩进字节数
    "prettier.useTabs": false, // 缩进不使用tab，使用空格
    "prettier.semi": true, // 句尾添加分号
    "prettier.singleQuote": true, // 使用单引号代替双引号
    "prettier.proseWrap": "preserve", // 默认值。因为使用了一些折行敏感型的渲染器（如GitHub comment）而按照markdown文本样式进行折行
    "prettier.arrowParens": "avoid", //  (x) => {} 箭头函数参数只有一个时是否要有小括号。avoid：省略括号
    "prettier.bracketSpacing": true, // 在对象，数组括号与文字之间加空格 "{ foo: bar }"
    "prettier.disableLanguages": ["vue"], // 不格式化vue文件，vue文件的格式化单独设置
    "prettier.endOfLine": "auto", // 结尾是 \n \r \n\r auto
    // "prettier.eslintIntegration": false, //不让prettier使用eslint的代码格式进行校验
    "prettier.htmlWhitespaceSensitivity": "ignore", //设置在 html 中所有空格不敏感，默认是 css
    "prettier.ignorePath": ".prettierignore", // 不使用prettier格式化的文件填写在项目的.prettierignore文件中
    "prettier.jsxBracketSameLine": false, // 在jsx中把'>' 是否单独放一行
    "prettier.jsxSingleQuote": false, // 在jsx中使用单引号代替双引号
    // "prettier.parser": "babylon", // 格式化的解析器，默认是babylon
    "prettier.requireConfig": false, // Require a 'prettierconfig' to format prettier
    // "prettier.stylelintIntegration": false, // 不让prettier使用stylelint的代码格式进行校验
    "prettier.trailingComma": "es5", // 在对象或数组最后一个元素后面是否加逗号（在ES5中加尾逗号）
    // "prettier.tslintIntegration": false, // 不让prettier使用tslint的代码格式进行校验
    // 未完，安装 Eslint 或 Vetur 还需要配置

    // Live Server
    // 打开：Alt + l Alt + o
    // 关闭：ALt + l Alt + c
    // Mac 是 cmd
    "liveServer.settings.donotShowInfoMsg": true, //禁止显示提示信息

    // Todo Tree
    "todo-tree.tree.showScanModeButton": false,
    // 默认主题配置
    "todo-tree.highlights.defaultHighlight": {
        "icon": "gift",
        "type": "line", // 显示高亮范围，默认是 tag，tag | line | text | tag-and-comment | text-and-comment | whole-line
        // "foreground": "red", // 显示高亮颜色设置 -- 前景色
        "background": "grey", // 显示高亮颜色设置 -- 背景色
        "opacity": 10, //背景透明
        "iconColour": "#EBD6D6", // 显示图标的颜色设置
        "gutterIcon": true // 设置为  true，在文件行数那一列显示 todo 图标
    },
    // 分类主题配置
    "todo-tree.highlights.customHighlight": {
        "TODO": {
            // 在标识处有功能代码待编写，待实现的功能在说明中会简略说明的
            "icon": "tasklist",
            "foreground": "#00FFFF",
            "iconColour": "#00FFFF"
        },
        "FIXME": {
            // 标识处代码需要修正，甚至代码是错误的，不能工作，需要修复，如何修正会在说明中简略说明码
            "icon": "smiley",
            "foreground": "#FF5151",
            "iconColour": "#FF5151"
        },
        "XXX": {
            // 虽然实现了功能，但是实现的方法有待商榷，希望将来能改进，要改进的地方会在说明中简略说明
            "icon": "check",
            "foreground": "#FFFF37",
            "iconColour": "#FFFF37"
        } // 只用这三个
    },

    // Vim
    "vim.easymotion": true, // 开启 EasyMotion 插件，默认不开启
    // <leader><leader> s <char> 搜索字符，上下都有
    // <leader><leader> f <char> 向下查找字符
    // <leader><leader> F <char> 向上查找字符
    // <leader><leader> t <char> 向下跳转到某个字符之前
    // <leader><leader> T <char> 向上跳转到某个字符之前
    // <leader><leader> w 向下跳转到单词首字母
    // <leader><leader> b 向上跳转到单词首字母
    // <leader><leder> l 向下匹配单词开头与结尾字母，_与#作为连接，右边字符也显示
    // <leader><leder> h 向上匹配单词开头与结尾字母，_与#作为连接，右边字符也显示
    // <leader><leader> e 向下跳转到单词尾字母
    // <leader><leader> ge 向上跳转到单词尾字母
    // <leader><leader> j 向下跳转到行首字母
    // <leader><leader> k 向上跳转到行首字母
    // <leader><leader><leader> j 上下文匹配单词开头结尾，会解析驼峰字符 l + h 既视感
    "vim.easymotionMarkerBackgroundColor": "#BF616A", // 设置高亮标记时候的颜色
    // 默认开启了 vim-surround 插件
    // ysw" 光标在首字母的时候使用 " 包裹整个单词
    // ds“ 删除 ”
    // cs"' 将 " 替换成 "
    "vim.useSystemClipboard": true, // 开启系统剪切板
    "vim.useCtrlKeys": true, // 启用Vim ctrl键以覆盖常见的VS Code操作，默认是：true，如 ctrl+f，ctrl+v 失效就关这个，或者在 vim.handleKeys 里单独配置
    "vim.hlsearch": true, // 是否高亮搜索 :noh 取消高亮
    // 插入模式键绑定
    "vim.insertModeKeyBindings": [
        {
            "before": ["v", "v"],
            "after": ["<Esc>"]
        }
    ],
    // 普通模式键绑定
    "vim.normalModeKeyBindingsNonRecursive": [
        {
            "before": [";"],
            "after": [":"]
        },
        // 下两个快捷启用了的话，VS Code 自带的Ctrl + PageUp / Ctrl + PageDown 就失效了
        {
            // 下一个标签页
            "before": ["<Tab>"],
            "after": ["g", "t"]
        },
        {
            // 上一个标签页
            "before": ["<Shift+Tab>"],
            "after": ["g", "T"]
        }
    ],
    "vim.leader": ",", // 设置 <leader> 为 ,
    // 是否开启 Vim 原生快捷键：true | false
    // false 就是不开启，使用 vs code 的快捷
    "vim.handleKeys": {
        // 上面启用了 useCtrlKeys ，所以如果有冲突，需要在这里配置
        "<C-a>": false, // 如注释这句话，并 useCtrlKeys 为 true 时，Ctrl + a 全选不起作用了
        "<C-f>": false,
        "<C-c>": false,
        "<C-b>": false,
        "<C-x>": false,
        "<C-k>": false
    },
    "window.zoomLevel"          : 0,       // 未完；根据使用过程发现的冲突不断添加
    "presentationMode.zoomLevel": 4,
    "glassit.alpha"             : 255,
    "editor.minimap.enabled"    : false,   // 关闭 minimap 预览
    // "editor.lineHighlightBackground": "#1E1E1EAA",
    "powermode.enabled": true,
    // "powermode.presets": "clippy",
    // "powermode.presets": fireworks,
    // 取消注释斜体
    "editor.tokenColorCustomizations": {
        "textMateRules": [
            {
                "name": "Comment",
                "scope": [
                    "comment",
                    "comment.block",
                    "comment.block.documentation",
                    "comment.line",
                    "comment.line.double-slash",
                    "punctuation.definition.comment"
                ],
                "settings": {
                    "fontStyle": ""
                    //斜体 "fontStyle": "italic",
                    //斜体下划线 "fontStyle": "italic underline",
                    //斜体粗体下划线 "fontStyle": "italic bold underline",
                }
            }
        ]
    }
}


// Place your key bindings in this file to override the defaults
[
    {
        "key": "ctrl+Alt+=",
        "command": "wwm.aligncode",
        "when": "editorTextFocus && !editorReadonly"
    }
]

```
