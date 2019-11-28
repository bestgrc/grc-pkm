

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

我在工作中是不喜欢一个方法太长，似乎是有点强迫症，如果有三个和三个以上的if-else连在一起，就想要把它抽成一个方法。

会用到两次以上的方法块也会想要给抽出来。





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



## i/o操作

1.  自动关闭流：

    ​	创建流的语句写在try(){}的小括号里

2.  关闭流，省去try-catch

    ​	IOUtils.closeQuietly();



Tomcat VM arguments

-Dcatalina.base="E:\apache-tomcat-7.0.91" 

-Dcatalina.home="E:\apache-tomcat-7.0.91" 

-Dwtp.deploy="E:\apache-tomcat-7.0.91\webapps" 

-Djava.endorsed.dirs="E:\apache-tomcat-7.0.91\endorsed" 

-Djava.library.path="C:\Users\huayu\AppData\Local\MyEclipse 2017 CI\binary\com.sun.java.jdk8.win32.x86_64_1.8.0.v112\bin;E:\apache-tomcat-7.0.91\bin"
-DappconfigServerUrl=http://172.16.33.3:8180/appconfig 

-Dcorp=default

> -d 代表 启动参数



java中的private修饰的变量和方法，可以在非本类中，以反射的方式访问。但通常情况下编程中使用不到，大多在框架中封装好。反射提供了一种更灵活的访问变量的方式，使用需谨慎。



## 线程

## 九 线程

### 线程五种状态

1. 新建
2. 就绪
3. 运行
4. 阻塞
5. 终止

### Thread.State类申明的六种线程状态

|        状态         |     名称      |
| :-----------------: | :-----------: |
|       1. 新建       |      new      |
|       2 运行        |   runnable    |
|       3 阻塞        |    blocked    |
| 4 等待 (时间不确定) |    waiting    |
| 5 等待（时间确定）  | timed_waiting |
|       6 终止        |  terminated   |

> 改变状态的方法
>
> - start()启动
> - sleep()睡眠
> - interrupt()中断

### 两种线程对象实现方法

1. 继承Thread类
2. 实现runnable接口

> 线程对象由Thread类或其子类申明，执行run（）方法实现具体方法

### 优先级

1-10 越大越优，默认为5

> main线程优先于其他线程执行。

### 定时器

Timer



### 线程间的竞争与互斥

#### 临界区调度原则

1. 无空等待
2. 有空让进
3. 择一而入
4. 算法可行

#### 资源竞争两大问题

1. 死锁
2. 饥饿

> 在多线程系统中，多个线程之间有**同步**和**互斥**两种关系。

#### 线程互斥实现:synchronized()

#### 线程同步

- 协作之间互相等待对方消息或信号的协作关系
- PV操作：

1. P:测试信号量状态
2. V改变信号量状态

- java线程通信方法：wait()、notify()等



------

### 多线程

#### 多线程解决的问题：

- 程序中需要执行耗时任务时。如数据库读写，io操作
- 程序中需要等待的任务。用户输入，文件读取。进行io操作时单线程程序的cpu是空闲的
- 目的：提高cpu利用率

### 进程与线程关系

进程包含线程
实现runnable接口优于继承thread接口，因为可以共享资源



### 线程池

### 解决的问题：

- 并发线程数量多，线程执行时间短，频繁创建和销毁线程消耗资源系统效率低下。

### 优势：

- 使线程得到复用



### 线程间竞争

#### 竞争的概念

多个线程访问同一资源，则线程间存在竞争关系。一个线程通过操作系统分配得到该资源，其他线程不得不等待。

#### 竞争引发的问题

##### 1. 死锁

一组线程都获得了部分资源，还想得到其他线程所占用的资源，所有线程都陷入死锁。

##### 2. 饥饿

一个线程由于其他线程总是优先于它而被无线拖延。



### 线程间互斥

#### 互斥的概念

若干线程要使用同一共享资源时，任何时刻最多允许一个线程去使用，其他要使用该资源的线程必须等待，直到战友资源的线程释放该资源。（互斥是解决线程间竞争关系的手段）

> 临界资源：共享变量代表的资源
>
> 临界区：并发线程中与共享变量有关的程序段



### 线程同步

#### 同步的概念

协作线程间互相等待对方消息或信号的协调关系

> 互斥是一种特殊的同步

#### 线程同步机制

通过信号量和pv操作实现

p：测试信号量状态

v：改变信号量状态

>  pv操作互斥执行，且执行时不能被打断



### 线程池

#### 常见线程池

-   Executors.newCacheThreadPool()：可缓存线程池

-   Executors.newFixedThreadPool(int n)：可重用固定个数

-   Executors.newScheduledThreadPool(int n) ：定时及周期性任务

-   Executors.newSingleThreadExecutor()：单线程的线程池

#### 常见缓冲队列

-   ArrayBlockingQueue（int i）
-   LinkedBlockingQueue（int i）
-   PriorityBlockingQueue（int i）根据Comparator决定顺序
-   SynchronizedQueue（）放和取交替

参考资料：

<https://blog.csdn.net/hnd978142833/article/details/80253784>



### synchronize用法

始终明确这个关键词锁的对象是什么，都是对临界资源上锁

对象锁（代码块调用形式）

1.  对单个对象加锁

```java
synchronized(对象){

代码块

}
```

2.  对当前对象加锁

```java
synchronized(this){

代码块

}
```

3.  对某个类加锁

```java
synchronized(xxxx.class){

代码块

}
```

类锁

1.  加在方法上（对该类的该方法上锁，上锁的同时，其他线程可以访问该类的其他方法。）
2.  加在类上 （对该类上锁）





## JVM

### TLAB

#### what

- Thread Local Allocation Buffer，线程本地分配缓存区

- 这是一个线程专用的内存分配区域。



#### why

new对象，给对象分配堆内存时，指针碰撞并发，引起内存分配错误，内存分配的效率较低。引入TLAB就是为了解决这个痛点。



#### how

线程初始化时，申请一块指定大小的内存，只给当前线程使用，这样每个线程都单独拥有一个空间，如果需要分配内存，就在自己的空间上分配，这样就不存在竞争的情况，可以大大提升分配效率。

> TLAB空间的内存非常小，缺省情况下仅占有整个Eden空间的1%



#### 缺陷

- 固定大小，只要内存稍大，就放不下。
- 剩余空间利用问题



#### 参考资料：

[浅析java中的TLAB](https://www.jianshu.com/p/8be816cbb5ed)



### 



## 内联

### what is 内联

JVM将方法进行处理，将方法调用替换为方法本身。

### why 内联

- 去除函数调用时产生的开销，提升运行效率。
- 以空间换时间

### when 内联

JVM会自己看情况用



## 调用python代码

只是简单的执行代码，还未涉及传参。

```java
ProcessBuilder pb = new ProcessBuilder(
        "E:\\downloads\\php.exe",
        "C:\\Users\\dell\\Desktop\\demo\\php\\accepted.php");
Process worker = pb.start();

StringBuilder result = new StringBuilder();
final BufferedReader reader = new BufferedReader(new InputStreamReader(worker.getInputStream()));
try {
    String line;
    while ((line = reader.readLine()) != null) {
        System.out.println("!!!"+line);
        result.append(line);
    }
} catch (IOException e) {
    e.printStackTrace();
}
worker.waitFor();
int exit = worker.exitValue();
if (exit != 0) {
    throw new IOException("failed to execute:" + pb.command() + " with result:" + result);
}
System.out.println(result.toString());
```