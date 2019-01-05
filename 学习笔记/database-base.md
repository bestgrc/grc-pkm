# 数据库基础

## jdbc与odbc

> 参考资料
>
> - [jdbc和odbc](https://www.cnblogs.com/yunfeioliver/p/8012166.html)

JDBC（Java Data Base Connectivity）是一种用于执行SQL语句的Java API，Java十三个规范之一。

ODBC（Open Database Connectivity）是Microsoft提出的数据库访问接口标准。它定义了访问数据库API的一个规范。

### 共性

- 都提供了一套访问数据库的api，具有平台无关性。

### 区别

|      | jdbc         | odbc               |
| ---- | ------------ | ------------------ |
| 语言 | java         | c                  |
|      | 简单，易上手 | 复杂，代码量大     |
|      | 移植性更好   | 装一次需求配置一次 |

> JDBC驱动程序中有一类叫作JDBC-ODBC桥接启动程序,连接两种方式，但是基本不用。



## 常用数据库端口号

- oracle 1521
- mysql 3306
- sql server 1433
- db2 5000
- postgre 5432

