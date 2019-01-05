# Java 开发模式

## 工厂模式
### 问题描述
遇到.forName不懂什么意思
```Java
public class Factory {
    public static UserDao getUserDaoImpl() {
        // 1.使用SAX解析得到配置文件内容
        // 直接根据id值userDaoImpl得到class属性值
        String classvalue = "class属性值";
        // 2.使用反射得到对象
        Class clazz = Class.forName(classvalue);
        UserDaoImpl userDaoImpl = (UserDaoImpl)clazz.newInstance();
        return userDaoImpl;
    }
}
```
https://blog.csdn.net/yerenyuan_pku/article/details/69663685
### 解决方案
https://zhidao.baidu.com/question/181702741.html

### new关键字和newInstance()方法的区别：

newInstance: 弱类型。低效率。只能调用无参构造。
new: 强类型。相对高效。能调用任何public构造。



## 单例模式

### 代码范例

```java
public class Singtelon {
	private static Singtelon singtelon = new Singtelon();
	private Singtelon() {

	}
	public void print() {
		System.out.println("hello");
	}

	public static Singtelon getInstance() {
		return singtelon;
	}
}

public class Demo {
	public static void main(String[] args) {
		Singtelon.getInstance().print();
	}
}
```

##  策略模式

**主要解决：**在有多种算法相似的情况下，使用 if...else 所带来的复杂和难以维护。

> 在解决查询管理、数据采集系统多种子系统的问题时可以使用。



[代码重构：用工厂+策略模式优化过多的if else代码块](https://www.cnblogs.com/sanyejun/p/7850622.html)