

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

1.  根据系统信息判断一下当前操作系统.
2.  使用相对路径.



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



# 注入方式

spring团队为什么推荐使用构造器注入

<https://blog.csdn.net/wo541075754/article/details/85494481>

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