##### Mysql 日期函数笔记

| 函数                | 描述                                        | 实例                                               |
| ------------------- | ------------------------------------------- | -------------------------------------------------- |
| ADDDATE(d,n)        | 给定的日期d加上n天数                        | SELECT    ADDDATE('2017-11-11 ',INTERVAL  1  DAY ) |
| SUBDATE(d,n)        | 给定的日期d减去n天数                        | SELECT    SUBDATE('2017-11-11 ',  1  DAY )         |
| DATE_SUB(d,n)       | 给定的日期d减去n天数                        | SELECT DATE_SUB('2017-02-18',INTERVAL 1     DAY）  |
| CURDATE()           | 返回当前日期                                | SELECT    CURDATE()                                |
| CURRENT_DATE()      | 返回当前日期                                | SELECT    CURRENT_DATE()                           |
| DATE()              | 从日期或日期时间表达式中提取日期值          | SELECT DATE("2017-06-15")                          |
| CURRENT_TIMESTAMP() | 返回当前日期和时间                          | SELECT    CURRENT_TIMESTAMP()                      |
| LOCALTIME()         | 返回当前日期和时间                          | SELECT LOCALTIME()                                 |
| LOCALTIMESTAMP()    | 返回当前日期和时间                          | SELECT LOCALTIMESTAMP()                            |
| NOW()               | 返回当前日期和时间                          | SELECT NOW();                                      |
| SYSDATE()           | 返回当前日期和时间                          | SELECT SYSDATE()                                   |
| DATEDIFF(d1,d2)     | 计算d1-d2的相差天数                         | SELECT DATEDIFF('2017-02-15','2017-02-18')         |
| DATE_FORMAT(d,f)    | 按表达式f的要求显示日期d                    | DATE_FORMAT('2017-02-18','%Y%M%D')                 |
| DAY(d)              | 返回天数                                    | SELECT DAY(2019-02-18);                            |
| DAYNAME(d)          | 返回星期几如Monday,Tuesday                  | SELECT DAYNAME('2019-02-18')                       |
| DAYOFMONTH(d)       | 返回本月第几天                              | SELECT DAYOFMONTH('2019-02-18')                    |
| DAYOFWEEK(d)        | 返回星期几，1 星期日，2 星期一，以此类推    | SELECT DAYOFWEEK('2019-02-18')                     |
| DAYOFYEAR(d)        | 返回本年的第几天                            | SELECT  DAYOFYEAR('2019-02-18')                    |
| LAST_DAY(d)         | 返回日期中那一月的最后一天                  | SELECT LAST_DAY('2018-02-18');                     |
| HOUR(t)             | 返回日期中的小时值                          | SELECT HOUR('2019-02-18 03:20')                    |
| MINUTE(t)           | 返回分钟值                                  | SELECT  MINUTE('2019-02-18 11:11:11')              |
| MONTH(t)            | 返回月份值                                  | SELECT  MONTH('2019-02-18')                        |
| QUARTER(d)          | 返回日期d是第几季节  1-4                    | SELECT QUARTER('2019-02-18')                       |
| SECOND()            | 返回秒钟值                                  | SELECT  SECOND('2019-02-18 11:12:14')              |
| WEEKDAY(t)          | 日期 d 是星期几，0 表示星期一，1 表示星期二 | SELECT WEEKDAY(‘2019-02-18’)                       |
| YEAR(t)             | 返回年份                                    | SELECT YEAR("2017-06-15");                         |









































