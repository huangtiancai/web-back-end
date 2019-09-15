
### 报错分析
1. 报错1：
```
2019-08-20 09:09:38,768 WARN [com.alibaba.druid.pool.vendor.MySqlValidConnectionChecker] - Cannot resolve com.mysq.jdbc.Connection.ping method.  Will use 'SELECT 1' instead.
java.lang.NullPointerException
	at com.alibaba.druid.pool.vendor.MySqlValidConnectionChecker.<init>(MySqlValidConnectionChecker.java:50)
	at com.alibaba.druid.pool.DruidDataSource.initValidConnectionChecker(DruidDataSource.java:944)
	at com.alibaba.druid.pool.DruidDataSource.init(DruidDataSource.java:659)

java.lang.NullPointerException
at com.alibaba.druid.util.JdbcUtils.getDriverClassName(JdbcUtils.java:354)
at com.alibaba.druid.pool.DruidDataSource.init(DruidDataSource.java:577)
at com.alibaba.druid.pool.DruidDataSource.getConnection(DruidDataSource.java:915)
at com.alibaba.druid.pool.DruidDataSource.getConnection(DruidDataSource.java:911)
at com.alibaba.druid.pool.DruidDataSource.getConnection(DruidDataSource.java:98)

```

2. 报错2：
```
内存溢出：
java.lang.OutOfMemoryError: PermGen space
```

3. 报错3：
```
严重: Servlet.service() for servlet jsp threw exception
javax.el.PropertyNotFoundException: Property 'menuLevel' not found on type com.htc.entity.Menu
	at javax.el.BeanELResolver$BeanProperties.get(BeanELResolver.java:291)
	at javax.el.BeanELResolver$BeanProperties.access$300(BeanELResolver.java:243)
	at javax.el.BeanELResolver.property(BeanELResolver.java:378)
	at javax.el.BeanELResolver.getValue(BeanELResolver.java:97)
	at org.apache.jasper.el.JasperELResolver.getValue(JasperELResolver.java:104)
原因：maven  Data注解无效，导致无法提供set/get方法
解决：
如果你是用eclipse作为开发环境，配置了maven依赖以后，还需要在eclipse/myeclipse中手动安装lombok。
lombok 安装
```


4. 报错4：
```
Exception in thread "main" java.lang.ExceptionInInitializerError
	at com.htc.test.Test.main(Test.java:30)
Caused by: org.apache.ibatis.exceptions.PersistenceException: 
### Error building SqlSession.
### Cause: org.apache.ibatis.builder.BuilderException: Error creating document instance.  Cause: org.xml.sax.SAXParseException; lineNumber: 1; columnNumber: 1; 前言中不允许有内容。
	at org.apache.ibatis.exceptions.ExceptionFactory.wrapException(ExceptionFactory.java:26)
	at org.apache.ibatis.session.SqlSessionFactoryBuilder.build(SqlSessionFactoryBuilder.java:54)
	at org.apache.ibatis.session.SqlSessionFactoryBuilder.build(SqlSessionFactoryBuilder.java:38)
	at com.htc.utils.MybatisUtil.<clinit>(MybatisUtil.java:31)
	... 1 more
```

5. 报错5：
```
org.apache.ibatis.builder.IncompleteElementException: Could not find parameter map com.htc.dao.OrdersMapper.int
	at org.apache.ibatis.builder.MapperBuilderAssistant.setStatementParameterMap(MapperBuilderAssistant.java:319)
	at org.apache.ibatis.builder.MapperBuilderAssistant.addMappedStatement(MapperBuilderAssistant.java:283)
	at org.apache.ibatis.builder.xml.XMLStatementBuilder.parseStatementNode(XMLStatementBuilder.java:107)
	at org.apache.ibatis.session.Configuration.buildAllStatements(Configuration.java:698)
	at org.apache.ibatis.session.Configuration.hasStatement(Configuration.java:668)
	at org.apache.ibatis.session.Configuration.hasStatement(Configuration.java:663)
	at org.apache.ibatis.binding.MapperMethod$SqlCommand.<init>(MapperMethod.java:180)
	at org.apache.ibatis.binding.MapperMethod.<init>(MapperMethod.java:43)
	at org.apache.ibatis.binding.MapperProxy.cachedMapperMethod(MapperProxy.java:58)
	at org.apache.ibatis.binding.MapperProxy.invoke(MapperProxy.java:51)
	at com.sun.proxy.$Proxy4.findUserById(Unknown Source)
	at com.htc.test.Test.finUserById(Test.java:49)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:606)
	at org.junit.runners.model.FrameworkMethod$1.runReflectiveCall(FrameworkMethod.java:50)
	at org.junit.internal.runners.model.ReflectiveCallable.run(ReflectiveCallable.java:12)
	at org.junit.runners.model.FrameworkMethod.invokeExplosively(FrameworkMethod.java:47)
	at org.junit.internal.runners.statements.InvokeMethod.evaluate(InvokeMethod.java:17)
	at org.junit.runners.ParentRunner.runLeaf(ParentRunner.java:325)
	at org.junit.runners.BlockJUnit4ClassRunner.runChild(BlockJUnit4ClassRunner.java:78)
	at org.junit.runners.BlockJUnit4ClassRunner.runChild(BlockJUnit4ClassRunner.java:57)
	at org.junit.runners.ParentRunner$3.run(ParentRunner.java:290)
	at org.junit.runners.ParentRunner$1.schedule(ParentRunner.java:71)
	at org.junit.runners.ParentRunner.runChildren(ParentRunner.java:288)
	at org.junit.runners.ParentRunner.access$000(ParentRunner.java:58)
	at org.junit.runners.ParentRunner$2.evaluate(ParentRunner.java:268)
	at org.junit.runners.ParentRunner.run(ParentRunner.java:363)
	at org.eclipse.jdt.internal.junit4.runner.JUnit4TestReference.run(JUnit4TestReference.java:86)
	at org.eclipse.jdt.internal.junit.runner.TestExecution.run(TestExecution.java:38)
	at org.eclipse.jdt.internal.junit.runner.RemoteTestRunner.runTests(RemoteTestRunner.java:459)
	at org.eclipse.jdt.internal.junit.runner.RemoteTestRunner.runTests(RemoteTestRunner.java:675)
	at org.eclipse.jdt.internal.junit.runner.RemoteTestRunner.run(RemoteTestRunner.java:382)
	at org.eclipse.jdt.internal.junit.runner.RemoteTestRunner.main(RemoteTestRunner.java:192)
Caused by: java.lang.IllegalArgumentException: Parameter Maps collection does not contain value for com.htc.dao.OrdersMapper.int
	at org.apache.ibatis.session.Configuration$StrictMap.get(Configuration.java:797)
	at org.apache.ibatis.session.Configuration.getParameterMap(Configuration.java:570)
	at org.apache.ibatis.builder.MapperBuilderAssistant.setStatementParameterMap(MapperBuilderAssistant.java:317)
	... 34 more

```

6. 报错6：
```
org.apache.ibatis.binding.BindingException: Invalid bound statement (not found): com.htc.dao.OrdersMapper.findUserById
	at org.apache.ibatis.binding.MapperMethod$SqlCommand.<init>(MapperMethod.java:189)
	at org.apache.ibatis.binding.MapperMethod.<init>(MapperMethod.java:43)
	at org.apache.ibatis.binding.MapperProxy.cachedMapperMethod(MapperProxy.java:58)
	at org.apache.ibatis.binding.MapperProxy.invoke(MapperProxy.java:51)
	at com.sun.proxy.$Proxy4.findUserById(Unknown Source)
	at com.htc.test.Test.finUserById(Test.java:49)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:606)
	at org.junit.runners.model.FrameworkMethod$1.runReflectiveCall(FrameworkMethod.java:50)
	at org.junit.internal.runners.model.ReflectiveCallable.run(ReflectiveCallable.java:12)
	at org.junit.runners.model.FrameworkMethod.invokeExplosively(FrameworkMethod.java:47)
	at org.junit.internal.runners.statements.InvokeMethod.evaluate(InvokeMethod.java:17)
	at org.junit.runners.ParentRunner.runLeaf(ParentRunner.java:325)
	at org.junit.runners.BlockJUnit4ClassRunner.runChild(BlockJUnit4ClassRunner.java:78)
	at org.junit.runners.BlockJUnit4ClassRunner.runChild(BlockJUnit4ClassRunner.java:57)
	at org.junit.runners.ParentRunner$3.run(ParentRunner.java:290)
	at org.junit.runners.ParentRunner$1.schedule(ParentRunner.java:71)
	at org.junit.runners.ParentRunner.runChildren(ParentRunner.java:288)
	at org.junit.runners.ParentRunner.access$000(ParentRunner.java:58)
	at org.junit.runners.ParentRunner$2.evaluate(ParentRunner.java:268)
	at org.junit.runners.ParentRunner.run(ParentRunner.java:363)
	at org.eclipse.jdt.internal.junit4.runner.JUnit4TestReference.run(JUnit4TestReference.java:86)
	at org.eclipse.jdt.internal.junit.runner.TestExecution.run(TestExecution.java:38)
	at org.eclipse.jdt.internal.junit.runner.RemoteTestRunner.runTests(RemoteTestRunner.java:459)
	at org.eclipse.jdt.internal.junit.runner.RemoteTestRunner.runTests(RemoteTestRunner.java:675)
	at org.eclipse.jdt.internal.junit.runner.RemoteTestRunner.run(RemoteTestRunner.java:382)
	at org.eclipse.jdt.internal.junit.runner.RemoteTestRunner.main(RemoteTestRunner.java:192)
```