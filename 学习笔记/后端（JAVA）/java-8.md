java8中的特性：Option使用、Stream使用、函数式编程理解、lamda表达式



## Optional类的使用：

## 构造

Optional.of（）

Optional.ofNullable

Optional.empty     制造一空的option

### 获取

ifPresent





<https://blog.csdn.net/l_sail/article/details/78868673>

java8 的optional 是用来防止NPE影响程序运行?

在什么情况下使用它？

在返回值可能为`null`的函数中，Optional应该用做其返回类型。

1)Optional应该只用处理返回值,而不应该作为类的字段或者方法的参数.因为这样会造成额外的复杂度.

2)使用Option应该避免直接适应构造器和get,而应该使用isElse的系列方法避免频繁的非空判断



 	@notNull			提前判断非空，方便定位问题。

​	Object.requirednotnull







## 什么是lambda?

lambda表达式是一段可以传递的代码，它的核心思想是将面向对象中的传递数据变成传递行为。



## 基础语法

```
`expression = (variable) -> action`
```

- variable: 这是一个变量,一个占位符。像x,y,z,可以是多个变量；
- action: 这里我称它为action, 这是我们实现的代码逻辑部分,它可以是一行代码也可以是一个代码片段。



## 函数式接口

函数式接口是只有一个方法的接口，用作lambda表达式的类型。

@FunctionalInterface



有一个双冒号操作符。就是java中的方法引用，方法引用的格式是类名：：方法名。

lamda表达式的意义在于简化本来需要写匿名内部类函数重载的地方。



java7特性：

try-with-resources  自动关闭资源

捕获多个异常		减少代码冗余

处理反射异常

使用File类 快速操作文件。创建移动删除等等。





1. Java8新特性--Lambda表达式](https://www.cnblogs.com/kexianting/p/8588987.html)

2. 后来又看了java新版本的特性

   [跟上java8：你忽略的新特性](<htt[ps://blog.csdn.net/lz710117239/article/details/77943739>)