String 的底层实现就是一个char型数组。

很多地方会强调它是final类

实现接口：java.io.Serializable, Comparable<String>, CharSequence

其中 CharSequence 是第一次见，实现类有：[CharBuffer](https://docs.oracle.com/javase/8/docs/api/java/nio/CharBuffer.html), [Segment](https://docs.oracle.com/javase/8/docs/api/javax/swing/text/Segment.html), [String](https://docs.oracle.com/javase/8/docs/api/java/lang/String.html), [StringBuffer](https://docs.oracle.com/javase/8/docs/api/java/lang/StringBuffer.html), [StringBuilder](https://docs.oracle.com/javase/8/docs/api/java/lang/StringBuilder.html)





由于 char型数据只能存放16位的数据，所以长度上有一定限制，引入

Basic Multilingual Plane (BMP) 的概念





使用位运算提高性能。

```java
public static boolean isBmpCodePoint(int codePoint) {
    return codePoint >>> 16 == 0;
    // Optimized form of:
    //     codePoint >= MIN_VALUE && codePoint <= MAX_VALUE
    // We consistently use logical shift (>>>) to facilitate
    // additional runtime optimizations.
}
```



java 加减乘除的实现。

不知道java是怎么实现的，网上有个人的编程实现方法。

加：异或求当前位，与求进位。

减：a-b=a+（-b）=a+（~（b-1））=a+~b+1

乘：位运算与加法

除：很纯，多次减法，计数。



scan，break  scan

