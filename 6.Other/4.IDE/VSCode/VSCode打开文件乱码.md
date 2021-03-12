> VS Code默认是使用utf8编码格式的，有些html文件是gbk格式,这时打开就会乱码

#### 解决方法：

1. 如下图，VS Code 右下角点击编码

![20210101013156](http://pic.sigalx.com/pic/20210101013156.png)

2. 选择第一个 重新以新编码打开 Reopen with Encoding

![20210101013056](http://pic.sigalx.com/pic/20210101013056.png)

3. 搜索当前文件的编码，vs code 会自动检测当前文件编码，当前文件编码会排第一，一般都是gbk或gb2312

![20210101013333](http://pic.sigalx.com/pic/20210101013333.png)

4. 显示就变正常了

5. 再参照第一步，点击第二步的第二个选项 save with Encoding 将文件重新以utf8保存

6. 如果html文件设置了charset，别忘了改成utf-8


#### 另一种方式：

修改配置

`"files.autoGuessEncoding": true,`

VS Code会自动以文件的编码打开，但是这样做会导致整个项目部分文件的编码不一样。反而增加了不可预估的错误，不推荐。