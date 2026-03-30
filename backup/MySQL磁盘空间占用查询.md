各个库占用空间：
```sql
SELECT 
  table_schema AS 数据库名,
  ROUND(SUM(data_length + index_length) / 1024 / 1024 / 1024, 2) AS 占用_G
FROM information_schema.TABLES
GROUP BY table_schema
ORDER BY 占用_G DESC;
```

某个库下，表占用空间大小，按大到小排列：
```sql
SELECT
  table_name AS 表名,
  ROUND((data_length + index_length) / 1024 / 1024 / 1024, 2) AS 总占用_G,
  ROUND(data_length / 1024 / 1024 / 1024, 2) AS 数据_G,
  ROUND(index_length / 1024 / 1024 / 1024, 2) AS 索引_G,
  table_rows AS 行数
FROM information_schema.TABLES
WHERE table_schema = '我的库名称'
  AND table_type = 'BASE TABLE'
ORDER BY (data_length + index_length) DESC;
```

某个库下，表索引占用空间大小，从大到小排列：
```sql
SELECT
  table_name AS 表名,
  ROUND(index_length / 1024 / 1024 / 1024, 2) AS 索引占用_G,
  ROUND(data_length / 1024 / 1024 / 1024, 2) AS 数据占用_G,
  ROUND((data_length + index_length) / 1024 / 1024 / 1024, 2) AS 总占用_G
FROM information_schema.TABLES
WHERE table_schema = 'xxxxxxxx'  -- 你的库名
  AND table_type = 'BASE TABLE'
ORDER BY index_length DESC;  -- 按索引大小排序
```








