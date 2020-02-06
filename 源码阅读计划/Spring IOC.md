Q : spring 在getBean方法中，针对单例模式、原型模式的

bean分别处理，那么spring是如何分辨bean是使用什么设计模式的呢？

根据设置的scope属性，每个类默认的scope属性为单例



Q: 





Spring ioc源码五大体系

| 体系                 | 描述                                             |
| -------------------- | ------------------------------------------------ |
| Resource             | 配合ResourceLoader，定义了自己的资源及资源加载器 |
| BeanFactory          | 类工厂                                           |
| BeanDefinition       | 类定义                                           |
| BeanDefinitionReader | 类定义加载器                                     |
| ApplicationContext   | 高级类工厂（Spring容器）                         |

