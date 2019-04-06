# Java 开发模式

## 工厂模式


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

运行过程中会需要切换某一段算法或流程时。
