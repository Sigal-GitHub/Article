## 链接数据库

例子:

```php
$db = 'mysql';               // 数据库类型
$dbName = 'tp_blog';         // 数据库名
$host = '127.0.0.1';         // host
$userName = 'root';
$password = '666666';
$dsn = "$db:host=$host;dbname=$dbName";   // 数据源名称

try{
    $pdo = new PDO($dsn,$userName,$password);
    echo '数据库链接成功';
} catch (Exception $e) {
    echo $e->getMessage();
    die();
}
```
