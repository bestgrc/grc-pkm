# 数据库优化

- 参考资料
  - [数据库优化一般思路(个人经验之谈)](https://blog.csdn.net/zhoupan301415/article/details/78257783)

## 1 建立索引

- 成本低，见效快

- 适用数据库规模在几十万到几百万之间

## 2 分库分表分区

### 2.1 分库

- 分开查询库和系统库(增删改比较频繁的表)分开

### 2.2 分表

1. 分出历史表或者归档表，用来存放历史数据
2. 根据查询条件分表
3. 使用软件分表 （如mycat）

> tips：数据量在千万到亿级时需要使用，针对大表

### 2.3 分区

- 设定好分区规则，数据在插入时会被自动插入指定区

> tips：不能抗高并发

## 3 选择数据库引擎

- mysql中比较常用的数据库引擎有两种，一种是innodb、一种是myisam 

|       innodb       |          myisam          |
| :----------------: | :----------------------: |
|       行级锁       |          表级锁          |
| 适用于频繁修改的表 | 适用于一次插入，多次查询 |

>   参考资料:
>
>   -   [Mysql常用的三种数据库引擎比较](https://blog.csdn.net/T146lLa128XX0x/article/details/78737290)

**InnoDB**：支持事务处理，支持外键，支持崩溃修复能力和并发控制。如果需要对事务的完整性要求比较高（比如银行），要求实现并发控制（比如售票），那选择InnoDB有很大的优势。如果需要频繁的更新、删除操作的数据库，也可以选择InnoDB，因为支持事务的提交（commit）和回滚（rollback）。 

**MyISAM**：插入数据快，空间和内存使用比较低。如果表主要是用于插入新记录和读出记录，那么选择MyISAM能实现处理高效率。如果应用的完整性、并发性要求比较低，也可以使用。

**MEMORY**：所有的数据都在内存中，数据的处理速度快，但是安全性不高。如果需要很快的读写速度，对数据的安全性要求较低，可以选择MEMOEY。它对表的大小有要求，不能建立太大的表。所以，这类数据库只使用在相对较小的数据库表。

注意，同一个数据库也可以使用多种存储引擎的表。如果一个表要求比较高的事务处理，可以选择InnoDB。这个数据库中可以将查询要求比较高的表选择MyISAM存储。如果该数据库需要一个用于查询的临时表，可以选择MEMORY存储引擎。



## 4 预处理

### 4.1 实时数据

- 通过对对业务的抽象，可以放在缓存里面，提升系统运行效率

### 4.2 历史数据

- 对时效性不高的复杂关联分析报表，设定定时任务在半夜执行，放入结果表，第二天看结果表。或者放入solr或者elastisearch中。

## 5 模糊查询优化

like  “%str%” 不支持索引， "str%"号是支持索引的

### 5.1 允许前匹配

- 是数据库快速定位到数据，在结果集中再进行like匹配

### 5.2 不允许前匹配

- 采用solr或者elastisearch来进行模糊匹配

## 6 读写分离

- 参考资料
  - [【mysql 读写分离】10分钟了解读写分离的作用](https://blog.csdn.net/u013421629/article/details/78793966)

| Q    | A                                                            |
| ---- | ------------------------------------------------------------ |
| what | 让主数据库处理事务性增、改、删操作,从数据库处理SELECT查询操作。 |
| why  | 解决数据库的写入，影响查询效率的问题                         |
| when | 更新少，查询多的情况                                         |



# mybatis

### SqlMapConfig.xml

#### SqlMapConfig.xml中配置的内容和顺序如下：

properties（属性）

settings（全局配置参数）

typeAliases（类型别名）

typeHandlers（类型处理器）

objectFactory（对象工厂）

plugins（插件）

environments（环境集合属性对象）

​	environment（环境子属性对象）

​		transactionManager（事务管理）

​		dataSource（数据源）

mappers（映射器）



## Result Maps collection already contains value for ...解决方案

>   参考资料：
>
>   -   [关于mybatis启动报Result Maps collection already contains value for ...的问题总结](https://blog.csdn.net/nocol123/article/details/73928925)

1、当同一个xml映射文件内存在两个相同的id（即两个sql语句的id相同）时会报此错

解决：查询sql语句的id值修改



### Mybatis update 返回值

1.  **默认情况下**，mybatis 的 update 操作的返回值是 matched 的记录数，并不是受影响的记录数。

1.  boolean updateXxxx(Map<String, Object> paramsMap);

    Mybatis是根据查询到的记录数进行转换的(1表示为true,0表示为false) 。然而，如果查询到多条记录(大于1)，则返回的布尔值为false



# 杂项

## 数据库分页

1.  mysql ： limit
2.  oracle ： where中使用rownum
3.  mysql ： top

## SQL中的join

| INNER JOIN | LEFT /RIGHT [OUTER] JOIN     | FULL [OUTER] JOIN | CROSS JOIN |
| ---------- | ---------------------------- | ----------------- | ---------- |
| 交集       | 左/右表完全集，右/左的关联集 | 并集              | 笛卡尔乘积 |


