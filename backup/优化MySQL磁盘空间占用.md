首先说一下，我的MySQL是阿里云RDS，库数据本身占用300G多，然后我在控制台查询到总体占用510G多。
容量溢出，导致MySQL表被锁了。
后台报错日志为：
```
The MySQL server is running with the LOCK_WRITE_GROWTH option so it cannot execute this statement
```

SQL 查到的 300G = 表数据 + 索引
多出来的200多G 是 ：  日志 + 碎片 + 临时空间

1. Binlog 日志，占比最大
    写入越多、更新越多，binlog 就越大
2. 表碎片 + 空闲空间
    大量 DELETE 之后，MySQL 不会马上把空间还给系统，这些空闲空间依然占着磁盘。
    执行下面的命令优化
    ```sql
    OPTIMIZE TABLE `表名称`;   // 或下面的
    ALTER TABLE `表名称` FORCE;
    ```
3. undo log 回滚日志
    InnoDB 用来保证事务、MVCC 多版本，实例越忙、事务越长，undo 越大
4. 系统表空间 ibdata1
    包含事务信息、undo 等
5. 临时文件、慢查询日志、错误日志
    sort/group by 产生的临时表，慢查询日志，错误日志

清理：
1. 清理 binlog
阿里云 RDS 控制台 → 备份恢复 → Binlog 管理
点：一键上传 Binlog
上传后本地 binlog 会自动删除，磁盘瞬间下降。

2. OPTIMIZE 大表，回收碎片
```sql
ALTER TABLE 表名 FORCE;
```
3. 查看并清理慢查询日志 / 错误日志
控制台 → 日志管理 → 日志备份
4. 等待 undo 自动回收（不需要操作）
业务低峰期会自动收缩，不需要干预。








