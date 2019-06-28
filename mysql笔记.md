#####    创建数据库

```
1. CREATE DATABASE  <数据库名>；
```

```
2.  mysqladmin -u root -p create < 数据库名>；
```



##### 删除数据库

```
1. drop database <数据库名>；
```

```
2. mysqladmin -u root -p drop <数据库名>；
```



##### 选择数据库

```
1. use <数据库名>；
```

```
2. mysqli_select_db();
```



##### 清除表内数据

```
truncate  table  <表名>;
```



##### 释放表空间

```
optimize table <表名>;
```



##### UNION操作符

 UNION 操作符用于连接两个以上的 SELECT 语句的结果组合到一个结果集合中。多个 SELECT 语句会删除重复的数据。

语法：

```
SELECT expression1, expression2, ... expression_n
FROM tables
[WHERE conditions]
UNION [ALL | DISTINCT]
SELECT expression1, expression2, ... expression_n
FROM tables
[WHERE conditions];
```



##### ORDER BY 拼音排序

如果字符集采用的是 gbk(汉字编码字符集)，直接在查询语句后边添加 ORDER BY：

```
SELECT  *  FROM  <表名>    ORDER BY <字段>;
```

如果字符集采用的是 utf8(万国码)，需要先对字段进行转码然后排序：

```
SELECT * FROM <表名>  ORDER BY CONVERT( <字段> using gbk);
```



##### GROUP BY 分组

GROUP BY 语句对一个或多个列结果集进行分组。在分组的列上可以使用SUM、AVG、COUNT函数

```
SELECT column_name, function(column_name)
FROM table_name
WHERE column_name operator value
GROUP BY column_name;
```

#####  

##### 使用WITH ROLLUP  （英语翻译：汇总的意思）  注意：要在分组的基础上使用

```
SELECT name, SUM(singin) as singin_count FROM  employee_tbl GROUP BY name WITH ROLLUP;
```



#####  了解一下coalesce()（英语翻译：使...联合）   个人感觉很简单

```
SELECT coalesce(name, '总数'), SUM(singin) as singin_count FROM  employee_tbl GROUP BY name WITH ROLLUP;
```



#####  Mysql连接的使用

多表的操作：

| INNER JOIN（内连接,或等值连接) | 获取两个表中字段匹配关系的记录。               |
| ------------------------------ | ---------------------------------------------- |
| LEFT JOIN（左连接）            | 获取左表所有记录，即使右表没有对应匹配的记录。 |
| RIGHT JOIN（右连接）           | 获取右表所有记录，即使左表没有对应匹配的记录。 |



##### INNER JOIN

```
SELECT a.runoob_id, a.runoob_author, b.runoob_count FROM runoob_tbl a INNER JOIN tcount_tbl b ON a.runoob_author = b.runoob_author;
```

等同于

```
SELECT a.runoob_id, a.runoob_author, b.runoob_count FROM runoob_tbl a , tcount_tbl b WHERE a.runoob_author = b.runoob_author;
```



##### NULL值的处理

NULL 值与任何其它值的比较（即使是 NULL）永远返回 false，即 NULL = NULL 返回false 。

以下实例中你可以看到 = 和 != 运算符是不起作用的：

```
SELECT * FROM runoob_test_tbl WHERE runoob_count = NULL;

SELECT * FROM runoob_test_tbl WHERE runoob_count != NULL;
```

##### 必须使用 **IS NULL** 和 **IS NOT NULL**，

```
SELECT * FROM runoob_test_tbl WHERE runoob_count IS NULL;                                        
SELECT * FROM runoob_test_tbl WHERE runoob_count IS NOT  NULL;
```



##### 正则表达式  regexp   （英语翻译：正则表达式）哈哈哈

mysql中可以使用WHERE  LIKE % 来模糊匹配，MySQL 同样也支持其他正则表达式的匹配，使用 REGEXP 操作符来进行正则表达式匹配。

```
SELECT name FROM person_tbl WHERE name REGEXP '^st';                                //开头
```

查找name字段中以'ok'为结尾的所有数据：

```
SELECT name FROM person_tbl WHERE name REGEXP 'ok$';                                //结尾
```

查找name字段中包含'mar'字符串的所有数据：

```
SELECT name FROM person_tbl WHERE name REGEXP 'mar';                                //包含
```

查找name字段中以元音字符开头或以'ok'字符串结尾的所有数据：

```
SELECT name FROM person_tbl WHERE name REGEXP '^[aeiou]|ok$';           //以..开头 或..结尾
```



#####  Mysql  事务

MySql事务用来处理操作量大，复杂度高的数据。

| 在MySQL中只有使用了Innodb数据库引擎的数据库或表才能使用事务  |
| ------------------------------------------------------------ |
| 事务用来维护数据的完整性，保证成批的SQL语句要么全部执行，要么全部不执行 |
| 事务用来管理 insert、update、delete语句                      |



事务必须满足四个条件（ACID）原子性（Atomicity,或称不可分割性）、一致性（Consistency）、隔离性（Lsolation,又称独立性）、持久性（Durability.

| 原子性 | 事务（transaction）中的所有操作，要么全部完成，要么全部不完成，不会结束在中间的某个环节。事务在执行过程中发生错误，会被回滚（Rollback）到事务的开始前的状态，就像这个事务从来没有执行过一样。 |
| ------ | :----------------------------------------------------------- |
| 一致性 | 在事务开始之前和事务结束以后，数据库的完整性没有破坏。这表示写入的资料必须完全符合所有的预设规定，这包含资料的精准度，串联性以及后续数据库可以自发性地完成预定的工作。 |
| 隔离性 | 数据库允许多个事务同时对数据进行读写和修改的能力，隔离性可以防止多个事务并发执行时由于交叉执行而导致数据的不一致。事务隔离级别分为不同级别，包括读未提交（Read uncommitted）、读提交（read committed ） 可重复读（repeatable read）和串行化（Serializable） |
| 持久性 | 事务处理结束后，对数据的修改就是永久的，即便系统故障也不会丢失。 |



> PS:      在 MySql命令行的默认设置下，事务都是自动提交的，即执行SQL语句就会马上执行COMMIT操作，因此要显示地开启一个事务必须使用BEGIN(begin)或START TRANSACTION(start  transaction ),或者执行命令SET AUTOCOMMIT=0,用来禁止使用当前会的自动提交。



##### 事务控制语句：

* BEGIN 或 START TRANSACTION 显式地开启一个事务
* COMMIT 也可以使用COMMIT WORK ，二者等价，COMMIT会提交事务，并使已对数据库进行的所有修改成为永久性的。
* ROLLBACK 也可以使用ROLLBACK WORK ，二者等价，回滚会结束用户的事务，并撤销正在进行的所有未提交的修改。
* SAVEPOINT 允许在事务中创建一个保留点，一个事务中可以有多个。
* RELEASE SAVEPOINT 删除一个事务的保存点，当没有指定保存点，会抛出一个异常。
* ROLLBACK TO 把事务回滚到标记点。
* SET TRANSACTION 用来设置事务的隔离级别， InnoDB存储引擎提供事务的隔离级别有READ UNCOMMITTED（read uncommitted） ,READ COMMITTED(read committed) REPEATABLE READ (repeatable read)和SERLALIZABLE(serlalizable)



##### MySql  事务处理主要有两种方法

| BEGIN                            | 开启一个事务      |
| :------------------------------- | :---------------- |
| ROLLBACK                         | 事务回滚          |
| COMMIT                           | 事务确认          |
| SAVEPOINT savapoint_name         | 声明一个savepoint |
| ROLLBACK TO savepoint_name       | 回滚到savepoint   |
| RELEASE SAVEPOINT savepoint_name | 删除保留点        |
| SET  AUTOCOMMIT = 0              | 禁止自动提交      |
| SET  AUTOCOMMIT = 1              | 开启自动提交      |

#####  Mysql ALTER 命令

删除字段

```
ALTER TABLE <表名>  DROP <字段>;                                                  //删除字段
```

添加字段     --- 并定义数据类型  ---`必须定义数据类型`

```
ALTER TABLE <表名> ADD  <字段> int [NOT NULL | NULL | DEFAULT | COMMENT ];        //添加字段
```

还可以指定新增字段的位置，FIRST(设定位第一列)， AFTER (设定位与某个字段之后)

```
ALTER TABLE <表名> ADD <新增字段>  INT  FIRST                                  //添加到第一列 
```

``` 
AKTER TABLE <表名>  ADD <新增字段>  INT AFTER  <已有字段>                 //添加到指定的字段之后
```

添加主键、自增

```
ALTER TABLE <表名> ADD <新增字段> <类型> ,ADD PRIMARY KEY (字段名);                     //主键
```

``` 
AKTER TABLE <表名>  ADD <新增字段>  <类型> AUTO_INCREMENT, ADD PRIMARY KEY(字段名)  //主键自增
```



修改字段类型、名称 、注释

```
ALTER TABLE  <表名> MODIFY <字段> <类型> COMMENT '注释'                    //修改字段类型、注释
```

```
ALTER TABLE <表名> CHANGE <字段>  <新字段名>  <类型>                              //修改字段名
```



修改字段默认值

```
ALTER TABLE <表名> ALTER <字段> SET DEFAULT 1000;                            //修改字段默认值
```

```
ALTER TABLE <表名> ALTER <字段> DROP DEFAULT;                                //删除字段默认值
```



修改表信息

```
ALTER TABLE <表名>  ENGINE = MYISAM;                                            //修改表类型
```

```
alter table <表名> comment '系统信息表';                                         //修改表注释
```

```
ALTER TABLE <表名> RENAME TO  <新名称>;                                           //修改表名 
```

```
alter table <表名> drop foreign key keyName;                                     //删除外键
```



##### MySql 索引

索引作用：提高检索速度，使sql语句高速运行。

| 单列索引 | 即一个索引只包含单个列，一个表可以有多个单列索引 |
| -------- | ------------------------------------------------ |
| 组合索引 | 即一个索引包含多个列                             |

创建索引时，你需要确保该索引是应用在SQL 查询语句的条件(一般作为 WHERE 子句的条件)。

1. 创建索引：

```
CREATE INDEX indexName ON tableName(colunmName(length)); 
```

如果是CHAR，VARCHAR类型，length可以小于字段实际长度；如果是BLOB和TEXT类型，必须指定 length。

2. 修改表结构（添加索引）

```
ALTER table tableName ADD INDEX indexName(columnName)
```

3.  创建表的时候直接指定

```
CREATE TABLE mytable(  
 
ID INT NOT NULL,   
 
username VARCHAR(16) NOT NULL,  
 
INDEX [indexName] (username(length))  
 
);  
```



```DROP INDEX [indexName] ON mytable;
DROP INDEX [indexName] ON mytable;                                               //删除索引
```



##### MySql  临时表

在我们需要保存一些临时数据时是非常有用的，临时表只在当前连接可见，当关闭连接时，MySql会自动删除表并释放所有空间。

MySql临时表只在当前连接可见，如果你使用PHP脚本来创建MySql临时表，那每当PHP脚本执行完后，临时表也自动销毁。

创建临时表：

```
 CREATE TEMPORARY TABLE   <表名>
```

删除临时表：

```
DROP  TABLE  <表名>
```



#####  MySql 复制表

如何完整的复制MySql数据表

* 使用SHOW CREATE TABLE 命令获取创建数据表的（CREATE TABLE）语句，包含元数据的结构，索引等。
* 复制表的内容 INSERT INTO .....    SELECT 



```
SHOW CREATE TABLE tablename ;                                   //查看表的结构
```

```
CREATE TABLE tablename  LIKE  tablename   ;                       //复制表结构
```

```
INSERT INTO tablename SELECT * FROM tablename;                    //复制表内容 
```

```
CREATE TABLE tablename AS
(
    SELECT username, password FROM tablename
)                                                          //复制表中的某些字段
```



```
CREATE TABLE tablename AS
(  
    SELECT id, username AS uname, password AS pass FROM tablename 
)                                                            //修改新建表的字段
```



```
CREATE TABLE tablename AS
(
    SELECT * FROM tablename WHERE LEFT(username,1) = 's'
)                                                             //拷贝一部分数据
```



```
CREATE TABLE tablename
(
    id INTEGER NOT NULL AUTO_INCREMENT PRIMARY KEY
)
AS
(
    SELECT * FROM tablename
)                                               //创建表的同时定义表中的字段信息:
```



##### MySql序列

如果你删除了数据表中的多条记录，并希望对剩下数据的AUTO_INCREMENT列进行重新排列，那么你可以通过删除自增的列，然后重新添加来实现，小心使用。

```
 ALTER TABLE tablename DROP id;
 ALTER TABLE tablename  ADD id INT UNSIGNED NOT NULL AUTO_INCREMENT FIRST, ADD PRIMARY KEY (id);
```

设置序列的开始值

```
ALTER TABLE t AUTO_INCREMENT = 100;
```

##### MySql处理重复的数据

```
INSERT IGNORE INTO tablename  ....                                   //ignore（忽略的意思）
```



删除重复的数据:

```
CREATE TABLE tmp SELECT  *  GROUP BY (last_name, first_name, sex);

DROP TABLE person_tbl;

ALTER TABLE tmp RENAME TO person_tbl;
```



##### MySql 注入

所谓SQL注入，就是通过把SQL命令插入到Web表单递交或输入域名或页面请求的查询字符串，最终达到欺骗服务器执行恶意的行为

例如：

```
// 设定$name 中插入了我们不需要的SQL语句
$name = "Qadir'; DELETE FROM users;";
mysqli_query($conn, "SELECT * FROM users WHERE name='{$name}'");
```

在PHP中的 mysqli_query() 是不允许执行多个 SQL 语句的，但是在 SQLite 和 PostgreSQL 是可以同时执行多条SQL语句的，所以我们对这些用户的数据需要进行严格的验证。



| get_magic_quotes_gpc() | 检测是否进行双层转义          |
| ---------------------- | ----------------------------- |
| addslashes             | 对（‘ 、“ 、\、NULL）进行转义 |
| stripslashes           | 反引用一个引用字符串。        |
























