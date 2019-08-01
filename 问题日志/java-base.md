

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