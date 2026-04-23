```
ossfs ttxres /opt/oss_upload \
  -o url=oss-cn-guangzhou-internal.aliyuncs.com \
  -o passwd_file=/etc/passwd-ossfs \
  -o allow_other \
  -o mp_umask=022 \
  -o umask=022
```

- ttxres  Bucket桶
-  /opt/oss_upload  本地要挂载的目录
- oss-cn-guangzhou-internal.aliyuncs.com  OSS 内网访问地址（广州区）
- -o passwd_file=/etc/passwd-ossfs  从指定文件读取密钥（AccessKey）， 文件格式：BucketName:AccessKeyID:AccessKeySecret  不配则自动查找
- -o allow_other   允许所有系统用户访问这个挂载目录
-  -o mp_umask=022 挂载后目录 / 文件权限
- -o umask=022 新创建的文件 / 目录权限