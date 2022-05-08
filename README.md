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

### 引出返回值 方便统一响应
```php
//emptyparm method
if (empty($ReMethodParams)){
    return Container::run($controler,$method);
}
```
原有dispatch方法魔改
```php
private static $res = null;
......
self::$res =  call_user_func_array(self::$callbacks[$pos], $matched);
......
public static function Result(){
      self::dispatch();
      return self::$res;
  }
```
# 依赖声明
需要使用wazsmwazsm大佬的IOC库,和noahbuscher大佬的Macaw路由库,特此感谢
### wazsmwazsm
项目地址 
```url
https://github.com/wazsmwazsm/IOCContainer
```

安装方法
```bash
composer require wazsmwazsm/ioc-container
```

### Macaw
项目地址
```url
https://github.com/noahbuscher/macaw
```

安装方法
```json
require: {
    "noahbuscher/macaw": "dev-master"
}
```
```bash
cpmposer install
```


