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