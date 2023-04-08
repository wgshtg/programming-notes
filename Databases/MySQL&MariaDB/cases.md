# MySQL & MariaDB 常見配置與使用情境

## 查詢資料庫大小

```sql
SELECT
    table_schema AS "Database",
    SUM(data_length + index_length) / 1024 / 1024 AS "Size (MB)"
FROM
    information_schema.TABLES
GROUP BY
    table_schema;
/* output
+--------------------+-------------+
| Database           | Size (MB)   |
+--------------------+-------------+
| information_schema |  0.20312500 |
| mysql              | 10.92187500 |
| sys                |  0.03125000 |
+--------------------+-------------+
*/
```

## 查詢特定資料庫的所有資料表大小

```sql
SELECT
    TABLE_NAME AS `Table`,
    ROUND((DATA_LENGTH + INDEX_LENGTH) / 1024 / 1024) AS `Size (MB)`
FROM
    information_schema.TABLES
WHERE
    TABLE_SCHEMA = "{db-name}"
ORDER BY
    (DATA_LENGTH + INDEX_LENGTH) DESC;

/*
+---------------------------+-----------+
| Table                     | Size (MB) |
+---------------------------+-----------+
| time_zone_transition      |         7 |
| help_topic                |         2 |
| time_zone_transition_type |         1 |
| proc                      |         0 |
| .....                     |       ... |
| general_log               |         0 |
| slow_log                  |         0 |
| user                      |      NULL |
+---------------------------+-----------+
*/
```

