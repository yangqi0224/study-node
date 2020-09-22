# 										Spring笔记



## 一. 核心概念

### 1. 控制反转（IoC）

#### 1.1 配置元数据

​	给Spring提供相关信息，以便Spring实例化Bean并进行装配。

1. **XML方式配置**

   ```
   <!-- XML方式配置spring元数据时，中每个Bean都被定义在Beans标签内 -->
   <!-- ClassPathXmlApplicationContext("xmlpath") -->
   <beans>
   	<!-- id是每一个bean的唯一标识 -->
   	<bean id="beanId" class="类的全路径">
   		<!-- 类属性，ref可以引用其他bean来实例化本bean -->
   		<property name="" ref="">
   	</bean>
   </beans>
   ```

   

2. 注解方式配置(Spring2.5之后引入)

   ```java
   @Service("BeanId")
   //@Component,@Controller
   //
   public class XXXServiceImpl implements XXXService{
       @AutoWried
       private XXXDao xXXDao;
       ...
   }
   
   @Respository("BeanId")
   public class XXXServiceImpl implements XXXService{
       ...
   }
   ```

   ```
   <!-- 需配置包扫描路径 -->
   <context:component-scan base-package="packagePath">
   ```

   

3. 基于java的配置

   ```
   //标注配置类
   //AnnotionConfigApplicationContext(ClassName.class)
   @Configuration
   public class ClassName{
   	//每个方法对应一个Bean
   	@Bean
   	public XXXService serviceName(){
   		...
   	}
   }
   ```



### 1.2 依赖注入

1. Setter注入

   ```
   <!-- XML方式配置spring元数据时，中每个Bean都被定义在Beans标签内 -->
   <!-- ClassPathXmlApplicationContext("xmlpath") -->
   <beans>
   	<!-- id是每一个bean的唯一标识 -->
   	<bean id="beanId" class="类的全路径">
   		<!-- 类属性，ref可以引用其他bean来实例化本bean -->
   		<property name="" ref="">
   	</bean>
   </beans>
   ```

   

2. 构造方法注入

   ```
   <!-- XML方式配置spring元数据时，中每个Bean都被定义在Beans标签内 -->
   <!-- ClassPathXmlApplicationContext("xmlpath") -->
   <beans>
   	<!-- id是每一个bean的唯一标识 -->
   	<bean id="beanId" class="类的全路径">
   		<!-- 构造方法注入，ref可以引用其他bean给构造方法传参。通常，一个Bean只能配置一个构造方法注入 -->
   		<!-- 使用多个需要加index属性 -->
   		<constructor-arg ref="" index=“0”>
   	</bean>
   </beans>
   ```

   **循环依赖**

   ​		构造函数注入不能解决循环依赖的问题，Setter允许循环依赖，但是一般不建议使用。

```
<bean id="a" class="com.yq.A">
	<constructor-arg ref="b" />
</bean>
<bean id="b" class="com.yq.B">
	<constructor-arg ref="a" />
</bean>
```

​		depends on



​	