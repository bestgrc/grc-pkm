# java进阶

## java的13个规范

1. JDBC——Java Database Connectivity
2. JSP——Java Server Pages
3. Servlet
4. XML——Extensible Markup Language
5. JavaMail
6. JAF——JavaBeans Activation Framework
7. EJB——Enterprise JavaBean
8. JNDI——Java Name and DirectoryInterface
9. RMI——Remote Method Invoke
10.  JavaIDL/CORBA
11. JMS——Java Message Service
12. JTA——Java Transaction Architecture
13. JTS——Java Transaction Service



### EJB

一直提到EJB的概念，就去了解了一下。

> 参考资料
>
> - [EJB到底是什么？](https://www.cnblogs.com/strugglion/p/6027318.html)
> - [EJB](http://www.baike.com/wiki/EJB)

| 概念     | 把已经编写好的类打包放在服务器上执行。（区别于在客户端上运行。） |
| -------- | ------------------------------------------------------------ |
| 技术基础 | 远程方法调用（RMI）（技术基础：对象的序列化；远程过程调用（RPC）） |

组成：

1. SessionBean
2. Entity Bean
3. MessageDriven Bean

EJB似乎是一个老技术，更多的人开始用spring。看了一堆别人的博客还有百度百科，也没实际搞懂它。或许要有实际开发经验，才能理解这个技术更替的意义吧。





## 圈复杂度

> 参考资料
>
> - [圈复杂度详解](https://blog.csdn.net/itxiaodong/article/details/69938970)

### 1. 定义

​	圈复杂度是用来衡量一个模块**判定结构**的复杂程度

> - 数量上表现为独立现行路径条数
> - 建议 V（G） <= 10

### 2. 计算

公式1：V（G）= E（路径数量） - N（节点数量） + 2

公式2：V（G）= 区域数 = 判定节点数 + 1

> 计算工具：SourceMonitor



## 泛型通配符

> 参考资料
>
> - [泛型通配符详解](https://p3c.alibaba.com/plugin/eclipse/update)

1. 无边界的通配符(Unbounded Wildcards): <?>
2. 固定上边界的通配符(Upper Bounded Wildcards): <? extends E>
3. 固定下边界的通配符(Lower Bounded Wildcards): <? super E>



> **集合泛型间不具有继承关系**
>
> 例如list<Object> 与 list<Integer>



> ### PECS（Producer Extends, Consumer Super）
>
> 参数化类型表示一个生产者，就使用<? extends T>；
>
> 如果它表示一个消费者，就使用<? super T>



> ### 数组的协变
>
> - 本质:就是向上转型
>
> - 产生问题:编译时检查不出错误的赋值，而运行时报ArrayStoreException异常。
>
> 参考资料：
>
> - [java 数组协变](https://www.cnblogs.com/hxy520/p/5725619.html)
> - [java中，数组为什么要设计为协变](https://zhidao.baidu.com/question/373185490288625524.html)
> - [数组是协变的，具体化的](https://blog.csdn.net/zjq2008wd/article/details/8788310)

