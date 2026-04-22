<img width="410" height="123" alt="Image" src="https://github.com/user-attachments/assets/7c18abb4-aa56-4bb5-979e-fe11875a6df0" />

这里因为这个php cli 中没有 redis 扩展的问题。

<img width="414" height="94" alt="Image" src="https://github.com/user-attachments/assets/e93aa9de-be76-4f13-815c-69844d02edcd" />

进一步说明，当前项目使用的php不是这个。

我们使用的是宝塔面板，查看项目使用的PHP版本：

<img width="558" height="483" alt="Image" src="https://github.com/user-attachments/assets/51973089-a9e7-4c14-ac9d-05aee1cc4cb0" />

```bash
]# /www/server/php/72/bin/php --version
PHP 7.2.33 (cli) (built: Aug 11 2020 15:38:39) ( NTS )
Copyright (c) 1997-2018 The PHP Group
Zend Engine v3.2.0, Copyright (c) 1998-2018 Zend Technologies
    with Zend OPcache v7.2.33, Copyright (c) 1999-2018, by Zend Technologies
```

改用  `/www/server/php/72/bin/php think xxx`  执行



