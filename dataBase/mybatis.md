## 一级缓存与二级缓存

> 参考资料
>
> - [Mybatis的一级缓存和二级缓存的理解和区别](https://blog.csdn.net/llziseweiqiu/article/details/79413130)
> - [MyBatis （五）一级缓存和二级缓存的区别](https://blog.csdn.net/qq_41541619/article/details/79967172)

- 数据的查询执行的流程：二级缓存-> 一级缓存 -> 数据库

| 区别     | 一级缓存       | 二级缓存          |
| -------- | -------------- | ----------------- |
| 作用域   | 一个sqlSession | mapper的namespace |
| 开启情况 | 默认开启       | 需手动开启        |

- SqlSession执行了DML操作（增删改），并且提交到数据库，MyBatis则会清空SqlSession中的一级缓存，这样做的目的是为了保证缓存中存储的是最新的信息，避免出现脏读现象。

