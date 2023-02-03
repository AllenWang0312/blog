
### 开发
#### CREATE

create table runoob_test_tbl
    -> (
    -> runoob_author varchar(40) NOT NULL,
    -> runoob_count  INT
    -> );

#### INSERT

INSERT INTO runoob_test_tbl (runoob_author, runoob_count) values ('RUNOOB', 20);


#### LIKE
某个字段包含

SELLECT field1,field2,fieldN
FROM table_name
WHERE field1 like "#COM"
【AND|OR】filed2="somevalue"


#### UNION
组合数据返回

SELLECT field1,field2
FROM table1
UNION ALL
SELLECT * FROM table2


#### ORDER BY field1,[field2] [ASC|DESC]
排序

#### GROUP BY
分组
SELECT name, COUNT(*) FROM   employee_tbl GROUP BY name;
WITH ROLLUP
SELECT name, SUM(singin) as singin_count FROM  employee_tbl GROUP BY name WITH ROLLUP;
coalesce(name, '总数')
 SELECT coalesce(name, '总数'), SUM(singin) as singin_count FROM  employee_tbl GROUP BY name WITH ROLLUP;
 INNER JOIN
 mysql> SELECT a.runoob_id, a.runoob_author, b.runoob_count FROM runoob_tbl a INNER JOIN tcount_tbl b ON a.runoob_author = b.runoob_author;

 等价于

 mysql> SELECT a.runoob_id, a.runoob_author, b.runoob_count FROM runoob_tbl a, tcount_tbl b WHERE a.runoob_author = b.runoob_author;
#### LEFT JOIN
 mysql> SELECT a.runoob_id, a.runoob_author, b.runoob_count FROM runoob_tbl a LEFT JOIN tcount_tbl b ON a.runoob_author = b.runoob_author;
#### RIGHT JOIN
 mysql> SELECT a.runoob_id, a.runoob_author, b.runoob_count FROM runoob_tbl a RIGHT JOIN tcount_tbl b ON a.runoob_author = b.runoob_author;

#### NULL 处理

 IS NULL |IS NOT NULL
 NULL = NULL return false


#### REGEXP
 正则表达式

|---|---|
|模式|描述|
|^|	匹配输入字符串的开始位置。如果设置了 RegExp 对象的 Multiline 属性，^ 也匹配 '\n' 或 '\r' 之后的位置。|
|$|	匹配输入字符串的结束位置。如果设置了RegExp 对象的 Multiline 属性，$ 也匹配 '\n' 或 '\r' 之前的位置。|
|.|	匹配除 "\n" 之外的任何单个字符。要匹配包括 '\n' 在内的任何字符，请使用象 '[.\n]' 的模式。|
|[...]|	字符集合。匹配所包含的任意一个字符。例如， '[abc]' 可以匹配 "plain" 中的 'a'。|
|[^...]|	负值字符集合。匹配未包含的任意字符。例如， '[^abc]' 可以匹配 "plain" 中的'p'。|
|p1|p2|p3|	匹配 p1 或 p2 或 p3。例如，'z|food' 能匹配 "z" 或 "food"。'(z|f)ood' 则匹配 "zood" 或 "food"。|
|*	|匹配前面的子表达式零次或多次。例如，zo* 能匹配 "z" 以及 "zoo"。* 等价于{0,}。|
|+	|匹配前面的子表达式一次或多次。例如，'zo+' 能匹配 "zo" 以及 "zoo"，但不能匹配 "z"。+ 等价于 {1,}。|
|{n}|	n 是一个非负整数。匹配确定的 n 次。例如，'o{2}' 不能匹配 "Bob" 中的 'o'，但是能匹配 "food" 中的两个 o。|
|{n,m}|	m 和 n 均为非负整数，其中n <= m。最少匹配 n 次且最多匹配 m 次。

#### TRANSACTION 事务
- START TRANSACTION | BEGIN
- COMMIT
- ROLLBACK \ROLLBACK WORK 回退
- SAVEPOINT identifier 设置保存点
- RELEASE SAVEPOINT identifier 删除保存点
- ROLLBACK TO identifier 回滚到保存点
- SET TRANSACTION；用来设置事务的隔离级别。InnoDB存储引擎提供事务的隔离级别有READ UNCOMMITTED、READ COMMITTED、REPEATABLE READ和SERIALIZABLE。
- SET AUTOCOMMIT=0 禁止自动提交 1 开启自动提交


### 维护
#### ALTER 修改数据表名或者修改数据表字段
mysql> ALTER TABLE testalter_tbl ALTER i SET DEFAULT 1000;
- DROP   删除字段
  ALTER TABLE testalter_tbl  DROP i;
  mysql> ALTER TABLE testalter_tbl ALTER i DROP DEFAULT;
- ADD 增加字段
  ALTER TABLE testalter_tbl ADD i INT 【FIRST| AFTER c】;
- MODIFY
  mysql> ALTER TABLE testalter_tbl MODIFY c CHAR(10);
  mysql> ALTER TABLE testalter_tbl
      -> MODIFY j BIGINT NOT NULL DEFAULT 100;
- CHANGE
  mysql> ALTER TABLE testalter_tbl CHANGE i j BIGINT;
- RENAME  mysql> ALTER TABLE testalter_tbl RENAME TO alter_tbl;

#### INDEX 索引
创建
CREATE INDEX indexName ON mytable(username(length));
修改
ALTER table tableName ADD INDEX indexName(columnName)
建表添加
CREATE TABLE mytable(
ID INT NOT NULL,
username VARCHAR(16) NOT NULL,
INDEX [indexName] (username(length))
);
删除
DROP INDEX [indexName] ON mytable;
唯一索引

CREATE UNIQUE INDEX indexName ON mytable(username(length))
ALTER table mytable ADD UNIQUE [indexName] (username(length))
CREATE TABLE mytable(
ID INT NOT NULL,
username VARCHAR(16) NOT NULL,
UNIQUE [indexName] (username(length))
);

#### TEMPORARY TABLE 临时表
mysql> CREATE TEMPORARY TABLE SalesSummary (
    -> product_name VARCHAR(50) NOT NULL
    -> , total_sales DECIMAL(12,2) NOT NULL DEFAULT 0.00
    -> , avg_unit_price DECIMAL(7,2) NOT NULL DEFAULT 0.00
    -> , total_units_sold INT UNSIGNED NOT NULL DEFAULT 0
);
 SHOW TABLES 看不到临时表信息
 退出mysql 临时表销毁

CREATE table newname( select * from admin)

#### 处理重复数据

CREATE TABLE person_tbl
(
   first_name CHAR(20) NOT NULL,
   last_name CHAR(20) NOT NULL,
   sex CHAR(10),
   PRIMARY KEY (last_name, first_name)
);
