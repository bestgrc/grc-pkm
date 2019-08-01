这是接触到的第一个java8中的特性。

使用lamada表达式



java.util.Iterator

forEachRemaining



```java
default void forEachRemaining(Consumer<? super E> action) {
    Objects.requireNonNull(action);
    while (hasNext())
        action.accept(next());
}
```


看到这个方法之后，有了一些在程序中用lamada表达式的想法。