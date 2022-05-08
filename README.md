# macaw_modify
魔改macaw路由
支持带参数闭包函数
```php
Macaw::get("exec",array(
    array("f"),
    function ($f){
        return "hello closure".$f;
    }
));
```
将静态化请求恢复为正常请求
如:
伪静态
http://127.0.0.1/test/a/1/b/2/c/3
正常请求
http://127.0.0.1/test?a=1&b=2&c=3
