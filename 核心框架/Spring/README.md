### 1.框架

### 2.Spring
容器（可以管理所有组件（类）框架；
核心关注：IOC和AOP

### 3.Spring模块
`spring资料文件夹spring-framework-x.x.x.RELEASE-dist\spring-framework-x.x.x.RELEASE\libs：`
spring-aop-x.x.x.RELEASE.jar
spring-aop-x.x.x.RELEASE-javadoc.jar
spring-aop-x.x.x.RELEASE-sources.jar

三个一组：source是源码包；
参考：[Spring 4.0.0 参考文档](https://docs.spring.io/spring/docs/4.0.0.RELEASE/spring-framework-reference/htmlsingle/)

Spring模块的划分图

![](../Spring/images/Spring模块.jpg)
`Test`:单元测试模块(Spring的单元测试模块功能强大，对比junit)
>spring-test-4.0.0.RELEASE

`Core containrer`:核心容器(IOC)：黑色代表这部分的功能由哪些jar包组成；要使用这部分的完整功能，这些jar都需要导入
>spring-beans-4.4.0.RELEASE
spring-core-4.4.0.RELEASE
spring-context-4.4.0.RELEASE
spring-expression-4.4.0.RELEASE

`AOP+Aspects(面向切面编程模块)`
>spring-aop-4.0.0.RELEASE
spring-aspects-4.0.0.RELEASE

`数据访问/集成模块`
>spring-jdbc-4.0.0.RELEASE
spring-orm(Objecet Relation Mapping)-4.0.0.RELEASE -对象关系映射
spring-tx-4.0.0.RELEASE(事务)
spring-oxm(Objecet Xml Mapping)-4.0.0.RELEASE - 对象xml关系映射
spring-jms-4.0.0.RELEASE - 消息服务

`Web:Spring开发web应用的模块`
>spring-websocket(新的技术)-4.0.0.RELEASE
spring-web-4.0.0.RELEASE - 原生的web开发相关(servlet)
spring-webmvc-4.0.0.RELEASE - 开发web项目的模块
spring-webmvc-portlet-4.0.0.RELEASE - 开发web应用的组件集成


### 4.Spring(IOC和AOP)
Spring是一个IOC(DI)和AOP容器框架。
>IOC => 整合其它框架：Struts2、Hibernate、MyBatis
AOP => 声明式事务管理 => Spring如何操作数据库

spring的核心：
`IOC`：(Inversion(反转) of Control:控制反转)
`控制`：资源的获取方式：
- `主动式`：要什么资源都自己创建即可
```
BookServlet{
    BookService bs = new BookService();
}
```
缺点：
>复杂的对象的创建时比较大的工程；
一个类会依赖另一个类，一个类出问题，那么引用该类的类也会出现问题；需要替换类型，需要修改源码 => 高耦合


- `被动式`：资源的获取不是我们自己创建，而是交给一个容器类创建和设置
```
BookServlet{
    BookService bs;
    public void tets01(){
        bs.checkout();
    }
}
```
`容器`：管理所有的组件（有功能的类）;
假设：BookServlet受容器管理，BookService也受容器管理；
容器可以自动探查出那些哪些组件（类），需要用到另一些组件（类）;
容器帮我们创建BookService对象，并把BookService对象复制过去；
`容器`：主动的new资源变为被动的接受资源

`控制反转`：将对象的创建权，交给spring完成

`DI:(Dependency Injecttion)`依赖注入
容器能知道哪个组件（类）运行的时候主要另外一个组件（类）；
容器通过反射的形式，将容器中准备好的BookService对象注入（利用反射给属性赋值）到BookServlet

只要IOC容器管理的组件，都能使用容器提供的强大功能；
***

HelloWorld
目标：使用Spring创建对象，为属性赋值
以前是自己new对象 => 现在所有对象交给容器创建；给容器注册组件

框架编写流程：
1. 导包
2. 写配置
3. 测试

1.导包：
>核心容器：
spring-beans-4.0.0.RELEASE.jar
spring-context-4.0.0.RELEASE.jar
spring-core-4.0.0.RELEASE.jar
spring-expression-4.0.0.RELEASE.jar
Spring运行时的时候依赖一个日志包，没有就报错：
commons-logging-1.1.3.jar

2.写配置
1)创建Student类
2)创建Spring配置文件

Spring配置文件中集合了Spring的ioc容器管理的所有组件（清单）
创建Spring Bean Configuration File(Spring的bean配置文件)
```
<!-- 注册一个Person对象，Springhi自动创建这个Person对象 -->
<!-- 一个Bean标签可以注册一个组件（对象、类） -->
<!-- class:写注册的组建的全类名 -->
<!-- id:这个对象的唯一标识； -->
<bean id="persion01" class="com.htc.bean.Person">
    <!-- 使用property标签为Person对象的属性赋值
        name="lastName":指定属性名
        value="张三:为这个属性赋值
        -->
    <property name="lastName" value="张三"></property>
    <property name="age" value="10"></property>
    <property name="gender" value="男"></property>
    <property name="email" value="zhangsan@qq.com"></property>
</bean>
```
3)测试
```
    //ApplicationContext:代表IOC容器
    //ClassPathXmlApplicationContext：当前应用的xml配置文件在ClassPath（类路径）下
    //1.根据spring配置文件得到ioc容器对象
    ApplicationContext ioc = new ClassPathXmlApplicationContext("ioc.xml");
    //2.根据id值获取bean实例对象
    Person bean = (Person) ioc.getBean("persion01");
    //3.打印bean
    System.out.println(bean);
```
4)验证：Spring在创建IOC容器对象时，就已经完成了bean的创建和属性的赋值

几个细节：
![](..\Spring\images\Spring-IOC容器.jpg)

ClassPathXmlApplicationContext("ioc.xml") - ioc容器的配置文件在类路径下
FileSystemXmlApplicationContext("ioc.xml") - - ioc容器的配置文件在磁盘路径下















