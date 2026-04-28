首次部署，执行 composer update 会安装更新依赖，并且生成一个 composer.lock，这个文件是用来锁定依赖版本。
提交 composer.lock 到git版本
后续部署执行 composer i ，保证依赖一致

如果是直接复制过来的依赖库
删除 vendor/composer/installed.php
composer dump-autoload