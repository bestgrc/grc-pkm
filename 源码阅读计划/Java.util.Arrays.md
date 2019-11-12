### java.util.Arrays学习记录

| 方法               | 用途             |
| ------------------ | ---------------- |
| binarySearch       | 二分查找         |
| copyOf/copyOfRange | 复制（深拷贝）   |
| equals             | 内容的比较       |
| fill               | 填充数组         |
| hashCode           | 基于内容的哈希值 |
| sort               | 升序排序         |
| toString           | 输出             |

> 常见哈希值算法:
>
> 1：Object类的hashCode.返回对象的内存地址经过处理后的结构，由于每个对象的内存地址都不一样，所以哈希码也不一样。
> 2：String类的hashCode.根据String类包含的字符串的内容，根据一种特殊算法返回哈希码，只要字符串内容相同，返回的哈希码也相同。
>
> 3：Integer类，返回的哈希码就是Integer对象里所包含的那个整数的数值，例如Integer i1=new Integer(100),i1.hashCode的值就是100 
>
> [参考资料](https://blog.csdn.net/diqye2011/article/details/7641406 )



