# Lumen 开发RESTful api



### 1.自定义框架的错误信息

_app\Exception\handle.php_

``` php
public function render($request, Exception $e)
{
	// 这里可以自定义错误消息格式
    return response()->json(array('error_code' => $e->getStatusCode()));
    // 这是默认的错误消息返回
    return parent::render($request, $e);
}
```

> 这样，返回的错误可以自定义为JSON，不必像默认那样返回一个错误的页面

### 2.建立Api认证中间件

_app\Http\Middleware_ 下建立中间件,创建handle方法

``` php
<?php
namespace App\Http\Middleware;

use Closure;
use Illuminate\Http\Request;

class ApiAuth
{
    public function handle(Request $request, Closure $next)
    {
        return $next($request);
    }
}
```

然后在_bootstrap/app.php_添加

``` php
$app->routeMiddleware([
    'ApiAuth' =>'App\Http\Middleware\ApiAuth',
]);
```



#  dingo api

- 安装


- 使用JWT

### 1.安装dingo api

- composer 安装，然后执行 _composer update_

``` José
// composer.json增加
"dingo/api": "1.0.*@dev",
```

- 在 _bootstrap/app.php_ 增加

``` php
$app->register(Dingo\Api\Provider\LumenServiceProvider::class);
```

由于Lumen 关闭了很多功能，有些地方还需要做些额外的修改。

- 把Eloquent 打开

``` php
$app->withEloquent();
```





## 参考资料

* [Lumen 中间件](http://lumen.laravel-china.org/docs/middleware)
<<<<<<< HEAD
* [Dingo api](https://github.com/dingo/api/wiki)
=======
>>>>>>> fcb3333a6cfbdf450a30b986f52202aa30c3144f
