###   Mysql数值函数

| CEIL                      | 进一取整                          |
| ------------------------- | --------------------------------- |
| 例子:                     | SELECT  CEIL(3.07);               |
| FLOOR                     | 舍一取整                          |
| 例子：                    | SEELCT  FLOOR(3.07);              |
| DIV                       | 整数除法                          |
| 例子：                    | SELECT 3 DIV  5;                  |
| MOD                       | 取余数                            |
| 例子：                    | SELECT 3  MOD 5;                  |
| POWER                     | 幂运算  /次方                     |
| 例子：                    | SELECT POWER(3,3);                |
| ROUND                     | 四舍五入                          |
| 例子：                    | SELECT ROUND(3.4);                |
| TRUNCATE                  | 数字截取                          |
| 例子：                    | SELECT TRUNCATE(125.34,2);        |
| [NOT] BETWEEN ... AND ... | [不]在范围之内                    |
| 例子：                    | SELECT 15  BETWEEN  1 AND 20;     |
|                           | SELECT 15 NOT BETWEEN  1 AND  14; |
| [NOT]  IN                 | [不]在列出值范围内                |
| 例子：                    | SELECT  10  IN(10,11,12);         |
|                           | SELECT 10 NOT IN(11,12,13);       |
| IS [NOT] NULL             | [不]为空                          |
| 例子：                    | SELECT NULL  IS NULL;             |
|                           | SELECT ' ' IS NOT NULL;           |

