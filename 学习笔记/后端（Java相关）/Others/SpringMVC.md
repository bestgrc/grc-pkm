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



# 两个框架的三大区别

| 区别     | springmvc                                                    | struts2                                                 |
| -------- | ------------------------------------------------------------ | ------------------------------------------------------- |
| 入口     | 前端控制器（servlet）                                        | 核心过滤器（filter）                                    |
| 开发方式 | 基于方法<br/>单例为主                                        | 基于类<br>只能多例                                      |
| 参数传递 | 请求参数传到方法形参;<br/>数据和视图封装成ModelAndView对象<br>视图解析器：JSTL表达式 | 采用值栈存储请求和响应的数据<br/>视图解析器：OGNL表达式 |



## 问题描述：

项目原本只有jsp页面，添加对于html页面的支持



## 解决方案：

修改 spring-mvc.xml

```xml
<bean id="freemarkerConfig" class="org.springframework.web.servlet.view.freemarker.FreeMarkerConfigurer">
            <property name="templateLoaderPath">
                <value>/view/</value>
            </property>
            <property name="freemarkerSettings">
                <props>
                    <prop key="template_update_delay">1</prop>
                    <prop key="default_encoding">UTF-8</prop>
                    <prop key="number_format">0.##</prop>
                    <prop key="datetime_format">yyyy-MM-dd HH:mm:ss</prop>
                </props>
            </property>
        </bean>
        <bean id="htmlviewResolver" class="org.springframework.web.servlet.view.freemarker.FreeMarkerViewResolver">
            <property name="suffix" value=".html" />
            <property name="order" value="0"></property>
            <property name="contentType" value="text/html;charset=UTF-8"></property>
        </bean>
```



> order值越小，优先级越高。从0开始



