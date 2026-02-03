```php
error_reporting(E_ALL);

$a = false;
if (empty($a)) {
    var_dump(111);  // 执行到这个分支
} else {
    var_dump(222);
}

var_dump(empty($a));  // bool(true)
```