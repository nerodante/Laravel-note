# Laravel ch3



* 数据填充与迁移



### 1.artisan migration

* 创建songs表：

*php artisan make:migration create_table_songs —create="songs"*

``` shell
// 回滚上一次迁移
php artisan migrate:rollback
// 回滚所有迁移
php artisan migrate:reset
```



> `--table` 和 `--create` 参数可以用来指定数据表名称，以及迁移文件是否要建立新的数据表。

迁移文件会在databases/migrations/下生成，文件名包含时间戳记录

添加字段：

``` php
$table->increments('id');
$table->string('title');
$table->text('lyric');
$table->timestamps();
```

### 2. tinker

_php artisan tinker_

``` php
DB::table('songs')->insert(['title' => 'Fall', 'created_at'=> new DateTime, 'updated_at'=>new DateTime ]);
```



### 参考资料

* [Laravel migration](http://laravel-china.org/docs/5.0/migrations)
* [Laravel 结构生成器](http://laravel-china.org/docs/5.0/schema)
  
  ​
