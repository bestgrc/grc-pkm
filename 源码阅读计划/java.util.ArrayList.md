底层是一个数组。



## 二、一个java的bug？？？

c.toArray might (incorrectly) not return Object[] (see 6260652)





### 三、GC的使用

protected void removeRange(int fromIndex, int toIndex) {
​        modCount++;
​        int numMoved = size - toIndex;
​        System.arraycopy(elementData, toIndex, elementData, fromIndex,
​                         numMoved);

```java
    // clear to let GC do its work
    int newSize = size - (toIndex-fromIndex);
    for (int i = newSize; i < size; i++) {
        elementData[i] = null;
    }
    size = newSize;
}
```
正真的删除操作是gc在做，程序里只需要置空即可



## 四、modCount

记录修改次数，操作前与操作后进行记录以保证没有被修改。

保证操作时没有被修改。



## 五、Objects.requireNonNull()

我理解的这个方法的意义就是便于抛出空指针时进行定位。底层源码里面经常出现，而开发者在业务中不必使用这个方法，可以根据业务判断可能的空指针异常，自定义业务异常



## 六、内部类：迭代器、子串

private class Itr implements Iterator<E>

private class SubList extends AbstractList<E> implements RandomAccess  用作调用sublist方法时返回一个类似于视图的东西，也就是一段浅拷贝。



## 七、有最大长度的限制

​    private static final int MAX_ARRAY_SIZE = Integer.MAX_VALUE - 8;

每次扩容，扩到原本的1.5倍



## 八、序列化问题

在new一个ArrayList对象时，默认是开辟一个长度为10的对象数组，如果只存入几个对象（不到默认的10个），如果采用默认序列化，则会将其余为null也序列化到文件中。

如果声明为transient类型，就能让虚拟机不会自行处理我们的这个数组，这才有了ArrayList的write/readObject方法。通过这种方式避免了浪费资源去存储没有的数据。

作者：柳岩是个大菜鸟 
来源：CSDN 
原文：https://blog.csdn.net/liuyancainiao/article/details/80051353 



可以使用foreach方法lamda表达式对其进行遍历操作。



## 九、ArrayListSpliterator

并行遍历迭代器。







自己看完这部分源码，对比javaGuide中的解析，其实自己已经注意到了绝大部分里面注意到的点。