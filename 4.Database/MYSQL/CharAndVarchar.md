关于字符串 char 和 varchar 的选择

char

定长 最多 255 字符 末尾的空格会被默认删除

何时选用 char 类型储存？

1 数据长度近似 如手机号 身份证 MD5 加密后的值

2 短字符串 相对 varchar 可以节约一个储存长度的空间

3 频繁更新的字段 相对于 varchar 不会产生长度变化也就不会产生存储碎片

varchar

varchar 类型与 char 类型不同 为变长字符串

在字符长度不超过 255 时 使用一个字节存储长度

超过 255 时用两个字节存储长度

每行的 varchar 总和不得超过 65535 字节 如果想存储更长的字符串建议选用 text 格式

既然 varchar 是变长的 而且不超过 255 字符时都是用一个字节来存储长度 那么是不是意味着 varchar(4) 与 varchar(100) 在存储四个字符长度的内容 比如 "abcd"时是完全一样的呢？

mysql 在查询时对于 varchar 字段在内存中是采用固定宽度而不是储存时的变长宽度 尤其是查询时创建的隐形临时表 所以在选择字段属性时还是适可而止 根据自己的业务来选择最合适的并且最小的长度 从而来提高查询速度 减少数据库服务器的开销

何时选用 varchar 列来储存？

1 字符串列最大长度比平均长度大很多的列 充分发挥变长的特点

2 字符串列较少被更新的列 因为 innodb 引擎一个存储页为 16k 频繁的更新变长字段可能导致存储页的分裂 产生存储碎片

3 多字节字符集 如 utf-8

<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<style>
table{
border-collapse: collapse;
width: 100%;
}
th, td{
text-align: left;
padding: 8px;
}
tr:nth-child(even){
background-color: #fafafa;
}
th{
background-color: #7799AA;
color: white;
}
</style>
</head>
<body>
<table>
<tr><th>bookmark_id</th><th>bookmark_name</th><th>bookmark_pid</th><th>bookmark_type</th><th>bookmark_link</th></tr>
<tr><td>1</td><td>123</td><td>0</td><td>0</td><td>123</td></tr>
<tr><td>2</td><td>LayUI</td><td>0</td><td>0</td><td>https://www.layui.com/doc/element/form.html</td></tr>
<tr><td>3</td><td>百度翻译</td><td>0</td><td>0</td><td>https://fanyi.baidu.com/</td></tr>
<tr><td>4</td><td>Sigal</td><td>0</td><td>1</td><td></td></tr>
<tr><td>5</td><td>Mac</td><td>0</td><td>1</td><td></td></tr>
<tr><td>6</td><td>抖音</td><td>0</td><td>1</td><td></td></tr>
<tr><td>7</td><td>狗狗</td><td>4</td><td>1</td><td></td></tr>
<tr><td>8</td><td>baidu</td><td>7</td><td>0</td><td>https://www.baidu.com</td></tr>
</table>
</body>
</html>
