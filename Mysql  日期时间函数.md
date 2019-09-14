###  Mysql  日期时间函数

| NOW()       | 当前日期和时间                                  |
| ----------- | ----------------------------------------------- |
| 例子：      | SELECT NOW();                                   |
| CURDATE     | 当前日期                                        |
| 例子：      | SELECT CURDATE();                               |
| CURTIME     | 当前时间                                        |
| 例子：      | SELECT CURTIME();                               |
| DATE_ADD()  | 日期变化                                        |
| 例子：      | SELECT DATE_ADD('1999-02-18',INTERVAL  1 YEAR); |
|             | SELECT DATE_ADD('1999-02-18',INTERVAL -1 YEAR); |
| DATEDIFF    | 日期差值                                        |
| 例子：      | SELECT DATEDIFF('1999-02-18','1999-02-19');     |
| DATE_FORMAT | 日期格式化                                      |
| 例子：      | SELECT  DATE_FORMAT('199-02-18','%m/%d%Y');     |



