# springmvc学习笔记

## springmvc的三大组件

1. 处理器映射器
2. 处理器适配器
3. 视图解析器

## 需要用户开发的组件

1. handler
2. view

------

## 参数绑定

### 1. 绑定简单类型

1. Integer

2. String

3. Float

4. Double

5. Boolean

> 参数类型推荐使用包装数据类型，因为基础数据类型不可以为null

### 2. 绑定pojo类型

### 3. 绑定包装pojo

- 参数复杂，名称可能重复时使用。

### 4. 自定义参数

- 日期格式多变，需要使用。
- springMVC.xml中配置Conveter转换器