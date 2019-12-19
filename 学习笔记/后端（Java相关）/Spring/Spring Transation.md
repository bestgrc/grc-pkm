# Spring 事务管理

1. 编码式 
2. 声明式
   1. 配置文件
   2. @Transactional注解

编码式需要手动编写事务的实现代码，属于定制化事务，不常用。这里主要记录如何调用spring的api，使用配置文件及注解方式实现事务。

# 注解方式

@Transational 可申明在类或者方法上



# 配置文件





Spring对事务控制的支持统一在TransactionDefinition类中描述，该类有以下   几个重要的接口方法：

1. int getPropagationBehavior()：事务的传播行为
2. int getIsolationLevel()：事务的隔离级别
3. int getTimeout()：事务的过期时间
4. boolean isReadOnly()：事务的读写特性

除了事务的传播行为外，事务的其他特性Spring是借助底层资源的功能来完成的，Spring无非只充当个代理的角色。但是事务的传播行为却是Spring凭借自身的框架提供的功能 ;



Spring事务传播属性:
1.propagation-required: 支持当前事务,如果有就加入当前事务中;如果当前方法没有事务,就新建一个事务;
2.propagation-supports: 支持当前事务,如果有就加入当前事务中;如果当前方法没有事务,就以非事务的方式执行;
3.propagation-mandatory: 支持当前事务,如果有就加入当前事务中;如果当前没有事务,就抛出异常;
4.propagation-requires_new: 新建事务,如果当前存在事务,就把当前事务挂起;如果当前方法没有事务,就新建事务;
5.propagation-not-supported: 以非事务方式执行,如果当前方法存在事务就挂起当前事务;如果当前方法不存在事务,就以非事务方式执行;
6.propagation-never: 以非事务方式执行,如果当前方法存在事务就抛出异常;如果当前方法不存在事务,就以非事务方式执行;
7.propagation-nested: 如果当前方法有事务,则在嵌套事务内执行;如果当前方法没有事务,则与required操作类似;
前六个策略类似于EJB CMT，第七个（PROPAGATION_NESTED）是Spring所提供的一个特殊变量。
它要求事务管理器或者使用JDBC 3.0 Savepoint API提供嵌套事务行为（如Spring的DataSourceTransactionManager）



参考资料：

[Spring事务管理嵌套事务详解 : 同一个类中，一个方法调用另外一个有事务的方法](https://blog.csdn.net/levae1024/article/details/82998386)



```
学习事务的帖子
https://www.cnblogs.com/dennyzhangdd/p/9602673.html
http://www.linkedkeeper.com/1045.html
```



