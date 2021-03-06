## 视图
webman默认使用的是php原生语法作为模版，在打开`opcache`后具有最好的性能。除了php原生模版，webman还提供了[Twig](https://twig.symfony.com/doc/3.x/) `Blade` `think-template` 模版引擎，其中推荐`Twig`，在易用性、扩展性及性能上是比较优秀的一款视图模版引擎。

## 开启opcache
使用视图时，强烈建议开启`opcache.enable`和`opcache.enable_cli` 两个选项，以便模版引擎达到最好性能。


## 安装Twig

`composer require twig/twig`

修改配置`config/view.php`为
```php
<?php
use support\view\Twig;

return [
    'handler' => Twig::class
];
```

## 安装Blade

`composer require jenssegers/blade`

修改配置`config/view.php`为
```php
<?php
use support\view\Blade;

return [
    'handler' => Blade::class
];
```

## 安装think-template

`composer require topthink/think-template`

修改配置`config/view.php`为
```php
<?php
use support\view\ThinkPHP;

return [
    'handler' => ThinkPHP::class
];
```

## 原生PHP模版引擎例子
创建文件 `app/controller/User.php` 如下

```php
<?php
namespace app\controller;

use support\Request;

class User
{
    public function hello(Request $request)
    {
        return view('user/hello', ['name' => 'webman']);
    }
}
```

新建文件 `app/view/user/hello.html` 如下

```html
<!doctype html>
<html>
<head>
    <meta charset="utf-8">
    <title>webman</title>
</head>
<body>
hello <?=htmlspecialchars($name)?>
</body>
</html>
```

## Twig模版引擎例子

修改配置`config/view.php`为
```php
<?php
use support\view\Twig;

return [
    'handler' => Twig::class
];
```

`app/controller/User.php` 如下

```php
<?php
namespace app\controller;

use support\Request;

class User
{
    public function hello(Request $request)
    {
        return view('user/hello', ['name' => 'webman']);
    }
}
```

文件 `app/view/user/hello.html` 如下

```html
<!doctype html>
<html>
<head>
    <meta charset="utf-8">
    <title>webman</title>
</head>
<body>
hello {{name}}
</body>
</html>
```
