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

