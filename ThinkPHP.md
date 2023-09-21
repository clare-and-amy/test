# ThinkPHP 常用操作
## 子查询
### 普通子查询
```php
$subQuery = Db::table('think_user')
    ->field('id,name')
    ->where('id', '>', 10)
    ->fetchSql(true)
    ->select();

// SELECT `id`,`name` FROM `think_user` WHERE `id` > 10 

// 说白了这里就是生成一个sql语句，同时也支持curd
```

```php
$subQuery = Db::table('think_user')
    ->field('id,name')
    ->where('id', '>', 10)
    ->buildSql();

// $subQuery = Db::table('think_user')->field('id,name')->where('id', '>', 10)->buildSql();

// 利用子查询构建新的查询（注意下面的别名）
Db::table($subQuery . ' a')
    ->where('a.name', 'like', 'thinkphp')
    ->order('id', 'desc')
    ->select();

// SELECT * FROM ( SELECT `id`,`name` FROM `think_user` WHERE `id` > 10 ) a WHERE a.name LIKE 'thinkphp' ORDER BY `id` desc
```

### 利用闭包构建子查询
> IN/NOT IN和EXISTS/NOT EXISTS之类的查询可以直接使用闭包作为子查询

```php
Db::table('think_user')
    ->where('id', 'IN', function ($query) {
        $query->table('think_profile')->where('status', 1)->field('id');
    })
    ->select();

// SELECT * FROM `think_user` WHERE `id` IN ( SELECT `id` FROM `think_profile` WHERE `status` = 1 )
```


