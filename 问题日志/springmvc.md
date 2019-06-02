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



>  order值越小，优先级越高。从0开始