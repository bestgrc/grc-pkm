## 一、基本信息

String 的底层实现就是一个char型数组。

很多地方会强调它是final类

实现接口：java.io.Serializable, Comparable<String>, CharSequence

其中 CharSequence 是第一次见，实现类有：[CharBuffer](https://docs.oracle.com/javase/8/docs/api/java/nio/CharBuffer.html), [Segment（未保护的String，不常用吧）](https://docs.oracle.com/javase/8/docs/api/javax/swing/text/Segment.html), [String](https://docs.oracle.com/javase/8/docs/api/java/lang/String.html), [StringBuffer](https://docs.oracle.com/javase/8/docs/api/java/lang/StringBuffer.html), [StringBuilder](https://docs.oracle.com/javase/8/docs/api/java/lang/StringBuilder.html)

|              | String         | StringBuffer | StringBuilder |
| ------------ | -------------- | ------------ | ------------- |
| 是否可变     | 不可变字符序列 | 可变字符序列 | 可变字符序列  |
| 是否线程安全 | 安全           | 安全         | 不安全        |



## 二、Basic Multilingual Plane (BMP) 

char可以存放16位的数据，可以标志65,536个不同的字符，

而unicode编码已经收录了一万出头的数据，六万以内的数字为BMP，否则为。。。，它是拆分开来放在一个char型数组里。

java底层对于字符进行处理的时候会区分这两种



## 三、StringBuilder.toString()

-   构造方法中有一个是通过stringBuilder来构造string,和stringbuilder的tostring方法相比,两者底层都是调用的Arrays.copyof()方法,但是官方在注释里这么说,推荐使用stringBuilder的toString方法.

```
Obtaining a string from a string builder via the {@code toString} method is likely to run faster and is generally preferred.
```



## 四、使用位运算提高性能。

```java
public static boolean isBmpCodePoint(int codePoint) {
    return codePoint >>> 16 == 0;
    // Optimized form of:
    //     codePoint >= MIN_VALUE && codePoint <= MAX_VALUE
    // We consistently use logical shift (>>>) to facilitate
    // additional runtime optimizations.
}
```

-   java 加减乘除的实现。

不知道java是怎么实现的，网上有个人的编程实现方法。

加：异或求当前位，与求进位。

减：a-b=a+（-b）=a+（~（b-1））=a+~b+1

乘：位运算与加法

除：很纯，多次减法，计数。



## 五、break与continue的高级用法

-   scan，break  scan 源码中有这样的操作

    ```java
    /* Now check if there are any characters that need to be changed. */
            scan: {
                for (firstUpper = 0 ; firstUpper < len; ) {
                    char c = value[firstUpper];
                    if ((c >= Character.MIN_HIGH_SURROGATE)
                            && (c <= Character.MAX_HIGH_SURROGATE)) {
                        int supplChar = codePointAt(firstUpper);
                        if (supplChar != Character.toLowerCase(supplChar)) {
                            break scan;
                        }
                        firstUpper += Character.charCount(supplChar);
                    } else {
                        if (c != Character.toLowerCase(c)) {
                            break scan;
                        }
                        firstUpper++;
                    }
                }
                return this;
            }
    ```

-   自定义的多重循环代码块，一个break或continue可作用于整个代码块



## 六、indexOf与lastIndexOf在java中的算法。

toUpperCase

与toLowerCase也值得细读。但是我觉得这块等源码阅读量大了之后再回过头来钻把。



这篇文章看起来很不错的样子。

[Java-String.intern的深入研究](https://www.cnblogs.com/Kidezyq/p/8040338.html)

