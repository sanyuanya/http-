###  Mysql字符函数

| CONCAT()  | 字符连接                                                     |
| :-------- | :----------------------------------------------------------- |
| 例子：    | SELECT CONCAT('A','B','C');                                  |
| CONCAT_WS | 使用指定分隔符进行字符连接                                   |
| 例子：    | SELECT CONCAT_WS('-','A','B','C');                           |
| FORMAT    | 数字格式化                                                   |
| 例子：    | SELECT  FORMAT(1234.56,1);                                   |
| LOWER     | 转化为小写                                                   |
| 例子：    | SELECT LOWER('Mysql');                                       |
| UPPER     | 转化为大写                                                   |
| 例子：    | SELECT UPPER('mysql');                                       |
| LEFT      | 获取左侧字符                                                 |
| 例子：    | SELECT LEFT('mysql',2);                                      |
| RIGHT     | 获取右侧字符                                                 |
| 例子：    | SELECT RIGHT('mysql',3);                                     |
| LEGTH     | 获取字符串的长度                                             |
| 例子：    | SELECT LENGTH('mysql');                                      |
| LTRIM     | 删除前导空格                                                 |
| 例子：    | SELECT LTRIM('   Mysql');                                    |
| RTRIM     | 删除后导空格                                                 |
| 例子：    | SELECT RTRIM('Mysql    ');                                   |
| TRIM      | 删除前导/后导指定字符                                        |
| 例子：    | SELECT TRIM(LEADING '?'  FROM  '?????Mysql');     //删除前导 |
|           | SELECT TRIM(TRAILING'?'  FROM  '?????Mysql???'); //删除后导  |
|           | SELECT TRIM(BOTH '?'  FROM  '?????Mysql???');      //删除所有 |
| REPLACE   | 替换                                                         |
| 例子：    | SELECT REPLACE('mysql','m','M');                             |
| SUBSTRING | 字符截取                                                     |
| 例子：    | SELECT SUBSTRING('Mysql',1,2);                               |
| LIKE      | 字符模糊匹配                                                 |
| 例子：    | SELECT  'tom%' LIKE  '%1%%' ESCAPE '1';                      |



