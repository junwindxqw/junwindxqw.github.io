## composer 正常更新安装依赖的方式

对于PHP的项目，依赖关系文件为  composer.json， 首次部署，执行 composer update 会安装更新依赖，并且生成一个 composer.lock，这个文件是用来锁定依赖版本。避免每个人的依赖版本不一致，要提交 composer.lock 到git版本，其他人部署时，用 composer i 安装依赖，保证大家的依赖版本是一致的。

❌ 没有 lock 文件 → 每个人装的版本都可能不一样 → 项目到处报错

执行 composer install → 严格按照 lock 文件安装（不会升级任何包）
执行 composer update → 才会更新包，并生成新的 lock

composer.json	告诉 Composer 需要哪些依赖	版本范围（如 ^1.0）
composer.lock	告诉 Composer 必须装哪个精确版本	固定版本号（如 1.2.3）+ 哈希

✅ 必须把 composer.lock 提交到 Git 仓库

正确部署项目的命令是：composer install


## 现在一个场景是：我直接复制粘贴的方式来获得 vendor ， 此时要重置一下自动加载脚本

删除复制来的 vendor/composer/installed.php
执行：composer dump-autoload

检查权限
- chmod -R 755 vendor
- chown -R www:www vendor

测试
```php
<?php
require __DIR__ . '/vendor/autoload.php';

// 随便调用一个依赖类，不报错就成功了
var_dump(class_exists('Carbon\Carbon'));
```








