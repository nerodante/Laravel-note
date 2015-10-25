# Lumen 开发RESful api



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



## 参考资料

* [Lumen 中间件](http://lumen.laravel-china.org/docs/middleware)