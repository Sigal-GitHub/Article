[toc]

## 分类模块的开发

路由：

使用 ThinkPHP6.0 资源路由 `Route::resource('category', 'category');`

控制器：

`app\admin\controller\Category;`

#### 添加分类

验证数据：(如果使用 LayUI 的话，前端验证很简单，在 input 里添加相应的代码)

- 是否有重复的分类
- 不能是特殊符号
- 不能超过多少字

数据提交的方式：**POST**

流程：

```
    // 先获取 POST 提交过来的数据；trim 清除两边的空格
    $category = $request->param('', '', 'trim');
    // 验证数据 -> 使用 TP6 的验证器
    try {
        validate(ValidateCategory::class)->scene('add')->check($category);
    } catch (ValidateException $e) {
        // 验证失败 输出错误信息
        return outputMsg('fail', $e->getError());
    }
    // 写入到数据库
```

#### 显示分类 -> 无限级分类

#### 删除分类

#### 批量删除

#### 排序分类