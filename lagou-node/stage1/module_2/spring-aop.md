# Spring IoC-BeanFactory继承体系

## 工厂接口

**顶级接口**：BeanFactory

继承体系：

![img](https://img2018.cnblogs.com/blog/1829343/201910/1829343-20191013213900444-1754406464.png)

部分实现类和子接口

![1613700863191](C:\Users\yangqi\AppData\Roaming\Typora\typora-user-images\1613700863191.png)

其中：FACTORY_BEAN_PREFIX是获取FactoryBean本身的方式（默认获取FactoryBean生产的对象）

![1613701791816](C:\Users\yangqi\AppData\Roaming\Typora\typora-user-images\1613701791816.png)

**高级接口**：ApplicationContext（继承了顶级接口）

高级接口常用实现类：AnnotationConfigApplicationContext,ClassPathXmlApplicationContext,FileSystemXmlApplicationContext

![1613701028038](C:\Users\yangqi\AppData\Roaming\Typora\typora-user-images\1613701028038.png)

## IoC容器

Spring应用上下文，官方称之为IoC容器。IoC容器为一组组件和过程的集合，其中的map、BeanFactory只是IoC容器的一部分，map实际上为IoC容器的单例池（singleObjects）。  



# Bean生命周期

1. 实例化Bean

AbstractApplicationContext#refresh() 方法



