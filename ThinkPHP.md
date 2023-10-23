# ThinkPHP 常用操作
## 按条件批量更新
```php
app(RedPacket::class)->where('type',1)
    ->where('user_id', $userId)
    ->where('round_num',1)
    ->where('activity_id', $activityId)
    ->update(['amount' => $amount1]);
```
## incr
注意必要少update
```php
app(User::class)->where('id', $userId)
    ->inc('estimate_recommend', (float) $amount)
    ->update();
```

## 关联查询
```php
$users = app(User::class)->alias('u')
    ->leftJoin('red_packet r', "r.source_user_id = u.id and r.activity_id =  {$activityId} and r.status > 0 and r.type = 1")
    ->field('u.id,u.register_time,u.nickname,u.face, count(r.id) as order_count')
    ->whereOr('u.id', $userId)
    ->whereOr(function (Query $query) use ($userId) {
        $query->where('u.lv1_user_id', $userId)
            ->where('u.power_lv', 0);
    })
    ->group('u.id')
    ->order('order_count','desc')
    ->paginate(config('app.common_page_size'));
```
注意 [加where变成inner join情况](https://blog.csdn.net/Asa_Prince/article/details/84302544)


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


