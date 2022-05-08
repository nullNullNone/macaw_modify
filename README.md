# macaw_modify 魔改macaw路由
### 支持带参数闭包函数
```php
Macaw::get("exec",array(
    array("f"),
    function ($f){
        return "hello closure".$f;
    }
));
```
### 将静态化请求恢复为正常请求
如:
伪静态
http://127.0.0.1/test/a/1/b/2/c/3
正常请求
http://127.0.0.1/test?a=1&b=2&c=3

##### 路由示例
```php
<?php

use NoahBuscher\Macaw\Macaw;
Macaw::get("exec",array(
    array("f"),
    function ($f){
        return "hello closure".$f;
    }
));

Macaw::get('heads', 'app\\Controllers\\demo@head');
Macaw::get('/', 'app\\Controllers\\demo@index');
Macaw::get('page', 'app\\Controllers\\demo@picfortext');
Macaw::get('/adm5', 'app\\Controllers\\demo@Admin5read');
Macaw::get('/sleep', 'app\\Controllers\\sleep@index');
Macaw::get('/Pen', 'app\\Mapp\\phpsec\\Filters@index');
Macaw::post('/Pen/addlash', 'app\\Mapp\\phpsec\\Filters@addlash');
Macaw::get('/Pen/checkMail', 'app\\Mapp\\phpsec\\Filters@checkMail');

echo Macaw::dispatchbyq();

```
