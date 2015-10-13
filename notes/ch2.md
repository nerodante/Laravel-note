# Laravel ch2

* Routes


* View

### 1.Route

 Dir: _App/Http/routes.php_

``` php
Route::get('/', 'HomeController@index');
```

利用artisan创建controller:（**artisan详细：php artisan list**）

``` php
php artisan make::controller HomeController --plain
```

### 2. Views

Dir : _resources/views_

``` 
return view('home');
// 若模版在home/index下
return view('home.index');
```

模版继承:

views/master:

``` 
<html>
<head>
    <link rel="stylesheet" type="text/css" href="">
    <title></title>
</head>
<body>
    @yield('content')
</body>
</html>
```

views/home/index:

``` 
@extends('master')

@section('content')
	Home index page
@stop
```

加载数据到模版

``` 
return view('admin.profile', $data);
```



### 参考资料

* [Blade 模版](http://www.golaravel.com/laravel/docs/5.1/blade/)
* [Laravel视图](http://www.golaravel.com/laravel/docs/5.1/views/)

