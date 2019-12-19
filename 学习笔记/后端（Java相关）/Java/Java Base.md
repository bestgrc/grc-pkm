## 一 配置环境变量

1.  新建->变量名"JAVA_HOME"，

    变量值"C:\Java\jdk1.8.0_05"（即JDK的安装路径） 

2.  编辑->变量名"Path"，在原变量值的最后面加上“;%JAVA_HOME%\bin;%JAVA_HOME%\jre\bin” 

3.  新建->变量名“CLASSPATH”,变量值“.;%JAVA_HOME%\lib;%JAVA_HOME%\lib\dt.jar;%JAVA_HOME%\lib\tools.jar”

### java配置环境变量以及原因

>   参考资料
>
>   -   [JAVA为什么要配置环境变量，怎样配置](https://www.cnblogs.com/zhangpengshou/p/4232204.html)
>   -   [Java环境变量中classpath是必须配置吗](https://zhidao.baidu.com/question/1605930365893725827.html)

| 环境变量  | 内容            | 原因                   |
| --------- | --------------- | ---------------------- |
| JAVA_HOME | JDK的安装目录   | 便于其他环境变量的引用 |
| CLASSPATH | %JAVA_HOME%\lib | 指定标准类库路径       |
| path      | %JAVA_HOME%\bin | 指定可执行文件的路径   |



### jre和jdk区别 

>   参考资料
>
>   -   [JDK and JRE File Structure](https://docs.oracle.com/javase/6/docs/technotes/tools/windows/jdkfiles.html)

-   jre：java运行时环境，包含java虚拟机和java核心类库。
-   jdk：java开发工具包，包含jre和一些java小工具。

![jdk](../picture/%E9%9D%A2%E8%AF%95%E9%A2%98/jdk.PNG)





## 二 编辑和运行java程序

### java程序的过程编译运行过程：

1. .java源文件 		 	使用javac.exe进行**编译**
2. .class字节码文件  		使用java虚拟机 java.exe进行**加载**
3. 实际程序

>    java虚拟机执行应用程序三大特点
>
>   1.  动态性
>   2.  异常处理
>   3.  多线程



## 三 java面向对象
> 面向对象与面向过程的区别：划分问题的方法是看“功能”还是看“步骤”

### 面向对象三大特征

#### 1 封装

将实现细节隐藏于方法体内，对外只暴露出入参及返回值。

在java中的体现：

1. 形式

- 将接口从具体的实施细节中分离出来，即实现了"是什么"与"怎样做"两个模块的分离。
  2. 优点	
- 代码的组织以及可读性获得改善
- 易于扩展

#### 2 继承

子类继承父类的成员变量以及方法。

#### 3 多态

多态是同一个行为具有多个不同表现形式或形态的能力。

多态就是同一个接口/父类，使用不同的实例而执行不同操作

参考资料：

[Java 多态](https://www.runoob.com/java/java-polymorphism.html)



### 面向对象设计七大原则
1. 单一职责原则（Single Responsibility Principle）：每一个类应该专注于做一件事情。
2. 里氏替换原则（Liskov Substitution Principle）：超类存在的地方，子类是可以替换的。
3. 依赖倒置原则（Dependence Inversion Principle）：实现尽量依赖抽象，不依赖具体实现。
4. 接口隔离原则（Interface Segregation Principle）：应当为客户端提供尽可能小的单独的接口，而不是提供大的总的接口。
5. 迪米特法则（Law Of Demeter）：又叫最少知识原则，一个软件实体应当尽可能少的与其他实体发生相互作用。
6. 开闭原则（Open Close Principle）：面向扩展开放，面向修改关闭。
7. 组合/聚合复用原则（Composite/Aggregate Reuse Principle CARP）：尽量使用组合/聚合达到复用，尽量少用继承。原则： 一个类中有另一个类的对象。



## 四 java数据类型

### 基本数据类型

### 引用数据类型

1.  一切类
2.  数组
3.  接口

## 五 this的三种用法

1.  调用本类中属性
2.  调用构造方法 （只能放在构造方法第一行）
3.  标识当前对象



## 六 static的作用

>   参考资料：
>
>   -   [java中static作用详解](https://zhidao.baidu.com/question/294516388.html)

static表示“全局”或者“静态”的意思，用来修饰成员变量和成员方法，也可以形成静态static代码块，但是Java语言中没有全局变量的概念。

被static修饰的成员变量和成员方法独立于该类的任何对象。也就是说，它不依赖类特定的实例，被类的所有实例共享。

只要这个类被加载，Java虚拟机就能根据类名在运行时数据区的方法区内定找到他们。因此，static对象可以在它的任何对象创建之前访问，无需引用任何对象。

用public修饰的static成员变量和成员方法本质是全局变量和全局方法，当声明它类的对象市，不生成static变量的副本，而是类的所有实例共享同一个static变量。

static变量前可以有private修饰，表示这个变量可以在类的静态代码块中，或者类的其他静态成员方法中使用（当然也可以在非静态成员方法中使用--废话），但是不能在其他类中通过类名来直接引用，这一点很重要。实际上你需要搞明白，private是访问权限限定，static表示不要实例化就可以使用，这样就容易理解多了。static前面加上其它访问权限关键字的效果也以此类推。



## 七 接口和抽象类的区别

**设计层面：抽象类是对一种事物的抽象，即对类抽象，而接口是对行为的抽象。**

>   参考资料
>
>   -   [Java抽象类与接口的区别](http://www.importnew.com/12399.html)

-   抽象类是对**类**的抽象，用来捕捉子类的通用特性；<br>接口是对**动作**的抽象，是抽象方法的集合。

| **参数**           | **抽象类**                                                   | **接口**                                                     |
| ------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| 默认的方法实现     | 它可以有默认的方法实现                                       | 接口完全是抽象的。它根本不存在方法的实现                     |
| 实现               | 子类使用**extends**关键字来继承抽象类。如果子类不是抽象类的话，它需要提供抽象类中所有声明的方法的实现。 | 子类使用关键字**implements**来实现接口。它需要提供接口中所有声明的方法的实现 |
| 构造器             | 抽象类可以有构造器                                           | 接口不能有构造器                                             |
| 与正常Java类的区别 | 除了你不能实例化抽象类之外，它和普通Java类没有任何区别       | 接口是完全不同的类型                                         |
| 访问修饰符         | 抽象方法可以有**public**、**protected**和**default**这些修饰符 | 接口方法默认修饰符是**public**。你不可以使用其它修饰符。     |
| main方法           | 抽象方法可以有main方法并且我们可以运行它                     | 接口没有main方法，因此我们不能运行它。                       |
| 多继承             | 抽象方法可以继承一个类和实现多个接口                         | 接口只可以继承一个或多个其它接口                             |
| 速度               | 它比接口速度要快                                             | 接口是稍微有点慢的，因为它需要时间去寻找在类中实现的方法。   |
| 添加新方法         | 如果你往抽象类中添加新的方法，你可以给它提供默认的实现。因此你不需要改变你现在的代码。 | 如果你往接口中添加方法，那么你必须改变实现该接口的类。       |



知识地图：

·标识符、类、接口、继承、重写、重载、装箱、拆箱、枚举、流程控制、异常、循环、字符串、IO、泛型、Option使用、Stream使用、函数式编程理解、lamda表达式



# 标识符与关键字

标识符是程序员自行定义的特殊字符串：由字母、数字、下划线、$组成 ，不能以数字开头

![1573515412863](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\1573515412863.png)

注意：

　　　　1.true、false、null不是关键字是字面量

　　　　2.特殊关键字（保留字）：goto,const

## 参考资料：

[Java标识符和关键字（static，final，abstract，interface）](https://www.cnblogs.com/wengbm/p/8067906.html)





# 重写/重载

都是多态的表现形式

重写：子类重写父类的方法

重载：同名方法，可以不同入参及返回值



详细信息：

[Java 重写(Override)与重载(Overload)](https://www.runoob.com/java/java-override-overload.html)



# 装箱/拆箱

- 基本数据类型与包装类之间的转换,本质上是调用包装类中的方法
- 在进行比较、运算等操作时会进行该操作
- 装箱：例如：Integer.valueOf()
- 拆箱：IntegerObject.intvalue()

基本类型初始化会自动拥有初始值

封装类未初始化即为null

## 参考资料

[详解Java的自动装箱与拆箱(Autoboxing and unboxing)](https://www.cnblogs.com/wang-yaz/p/8516151.html)



# 枚举类

为了安全性和便捷性

有机会可以用用EnumMap/EnumSet

## 参考资料

[深入理解Java枚举类型(enum)](https://www.cnblogs.com/alter888/p/9163612.html)



# 流程控制

复合语句 {}

条件语句 if-else/switch

循环语句 while/do...while/for

跳转语句 break / continue / return

## 参考资料

[Java入门篇（三）——Java流程控制](https://www.cnblogs.com/adamjwh/p/8329496.html)

# 异常



# IO



## 实例

### IO:string写入txt文件

```java
File file = new File("e:\\temp.txt");
OutputStream out=null;
String outPutString="";

byte b[] = outPutString.getBytes();
try {
out.write(b);
} catch (IOException e) {
// TODO Auto-generated catch block
e.printStackTrace();
}
```

> 注意换行是\r\n





# 泛型

- **泛型的本质是参数化类型**，也就是所操作的数据类型被指定为一个参数。

- 解决滥用Object变量然后强转为具体类的操作问题

- 具有更好的安全性与可读性
- 可用于类、方法、接口
- 只存在于编译阶段及之前。

[java 泛型详解-绝对是对泛型方法讲解最详细的，没有之一](https://www.cnblogs.com/coprince/p/8603492.html)



https://github.com/Snailclimb/JavaGuide/blob/master/docs/essential-content-for-interview/MostCommonJavaInterviewQuestions/%E7%AC%AC%E4%B8%80%E5%91%A8%EF%BC%882018-8-7%EF%BC%89.md>中关于hashcode与equals

1. 如果两个对象相等，则hashcode一定也是相同的
2. 两个对象相等,对两个对象分别调用equals方法都返回true
3. 两个对象有相同的hashcode值，它们也不一定是相等的
4. **因此，equals方法被覆盖过，则hashCode方法也必须被覆盖**
5. hashCode()的默认行为是对堆上的对象产生独特值。如果没有重写hashCode()，则该class的两个对象无论如何都不会相等（即使这两个对象指向相同的数据）

这篇文章以hashset的例子作为总结的方式，我觉得不具有普遍意义。



## 内部类的定义及作用

- 将一个类的定义放在另一个类的内部
- 它不单是一种代码隐藏机制，它了解外围类，并能与之通信，使用内部类写出的代码更加优雅而清晰。
- 在单独一个类里表达一个控制框架应用的全部实施细节，从而完整地封装与那个实施有关的所有东西。



## 特点：

- 它体现了一种代码的隐藏机制和访问控制机制，内部类与所在外部类有一定的关系，往往只有该外部类调用此内部类，所以没有必要专门用一个Java文件存放这个类。

- 它包含有一个对外部类的this指针，从而可以访问外部类的所有元素，包括所有public/private的成员和方法

  

## 内部类的分类

- 成员内部类
  - 当某个类除了他的外部类，不会被其他类使用时，使用成员内部类。
- 局部内部类
  - 定义在一个方法或者一个作用域里面。
- 静态内部类
- 匿名内部类
  - 接口或者抽象类都可以被实现为匿名内部类。 
  - 哪里定义，哪里使用，无法在其他地方调用。
  - 省略一个类的书写
  - 在编写事件监听的代码时匿名内部类不但方便，而且使代码更加容易维护。



- 常见的使用内部类实现多线程

```
public class Demo {  
    public static void main(String[] args) {  
        Thread t = new Thread() {  
            public void run() {  
                for (int i = 1; i <= 5; i++) {  
                    System.out.print(i + " ");  
                }  
            }  
        };  
        t.start();  
    }  
}  
```

```
public class Demo {  
    public static void main(String[] args) {  
        Runnable r = new Runnable() {  
            public void run() {  
                for (int i = 1; i <= 5; i++) {  
                    System.out.print(i + " ");  
                }  
            }  
        };  
        Thread t = new Thread(r);  
        t.start();  
    }  
}  
```

## 小tips

- 编译后每个内部类也会生成各自的二进制.class文件

## 参考资料：

https://blog.csdn.net/xiaoliuliu2050/article/details/62062881

https://www.iteye.com/blog/bingyingao-1265377





# 路径问题

## 问题描述

window和linux系统文件路径格式不一致问题.

window的绝对路径开头多一个"/"

```java
// 生成CSV文件路径
	String filePath = null;
	String os = System.getProperty("os.name");  
	if(os.toLowerCase().startsWith("win")){  
										filePath=Thread.currentThread().getContextClassLoader().getResource("").getPath().substring(1) + fileName;
	}else {
filePath="/"+Thread.currentThread().getContextClassLoader().getResource("").getPath().substring(1) + fileName;}
```

## 解决方案

1. 根据系统信息判断一下当前操作系统.
2. 使用相对路径.



将Vector<Vector<String>>对象拷贝入List<List<String>> 直接用集合的addAll方法.

```
Vector<Vector<String>> vectors
// 省略 vector的构造
List<List<String>> contents = new ArrayList<>();
contents.addAll(vectors);
```



调用接口

```
HttpClientUtils.get
```



## Integer

 public static void main(String[]arg){
​        Integer a=1;
​        Integer b=2;
​        Integer c=3;
​        Integer d=3;
​        Integer e=321;
​        Integer f=321;
​        Long g=3L;
​        System.out.println(c==d); // true 初始化调用Inetger.valueof, 使用缓存(-128~127)的引用,使用对象相同
​        System.out.println(e==f); // false new对象
​        System.out.println(c==(a+b));	//true a+b向下转型,c也向下转型
​        System.out.println(c.equals(a+b)); // true equals比较基本类型数值
​        System.out.println(g==(a+b)); // ture 向下转型
​        System.out.println(g.equals(a+b)); // false Long.equals 非Long,则返回false