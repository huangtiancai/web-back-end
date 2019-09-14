
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

