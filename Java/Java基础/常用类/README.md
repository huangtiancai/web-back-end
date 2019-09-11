## 一、Math

### 概述
1. Math是最终类，且构造函数被私有化，所以不允许创建对象。但是提供了一系列的静态方法---完全作为了工具类使用
2. Math类位于java.lang包中(java.lang.Math)

### 常量
1. E  ：底数 ，是所有自然数的底数。
2. PI ：π  ，圆周率 

### 方法
1. ceil() : 向上取整。 返回doouble类型的值。
2. floor() : 向下取整。 返回都变了类型的值。
3. round() : 四舍五入。返回long类型的值
4. random() : 返回一个 [0,1) 的随机小数 eg ： 获取一个30~50之间的随机整数 Int i = (int)(Math.random*21 +30);

4. max（Int arg,int arg2） : 返回最大值。
5. min() : 返回最小值。
6. pow(int arg1,int arg2) : 求第一个参数的第二个参数次幂。

8. strictfp方法修饰符 ： 要求小数在运算过程中以80位 二进制来算，但是最后仍然以64位存放结果； 小数在计算机中不能精确存储，doouble 在计算机中是以64位 二进制存储和运算。
9. BigDecimal类： 一个精确运算小数的类。 BigDecimal d1 = new BigDecimal("1.2"); BigDecimal d2 = new BigDecimal("0.99"); d1.subtract(d2);//执行减法 注意：参数必须是字符串。底层实现： 字符串底层是以字符数组存储，运算时字符数组按位相减，相当于整数运算，保证了运算的精确性。
10. 注意： 绝大部分十进制小数转换为二进制时都是无限的，所以计算机不能精确表示和存储小数。


## [System](https://github.com/huangtiancai/web/blob/master/CommonClass/src/com/htc/system/SystemDemo.java)
### 作用：System类是一些与系统相关的属性和方法的集合，位于java.lang包下


## [Date](https://github.com/huangtiancai/web/blob/master/CommonClass/src/com/htc/date/dateDemo.java)
Date-java.util.Date;
Calendar-java.util.Calendar;
DateFormat-java.text.DateFormat;
Locale-java.util.Locale
SimpleDateFormat-java.text.SimpleDateFormat;



总结：
一、 相关概念
1. 所有的数据类型，无论是整数，布尔，浮点数还是字符串，最后都需要以数字的形式表现出来=>日期类型也不例外，换句话说，一个日期，比如2020年10月1日，在计算机里，会用一个数字来代替
2. 最特殊的一个数字，就是零. 零这个数字，就代表Java中的时间原点=>对应日期：`日期是1970年1月1日 8点0分0秒`
3. 所有的日期，都是以为这个0点为基准，每过一毫秒，就+1。
二、Java时间日期的处理：Java Date类、Calendar类详解
1. 时间戳：timestamp
2. 在 Java 中获取当前时间，可以使用 java.util.Date 类和 java.util.Calendar 类完成。
其中，Date 类主要封装了系统的日期和时间的信息，Calendar 类则会根据系统的日历来解释 Date 对象
三、Date
Date 类表示系统特定的时间戳，可以精确到毫秒。
Date 对象表示时间的默认顺序是星期、月、日、小时、分、秒、年 => Wed Sep 11 09:54:28 CST 2019
1. 构造方法：
Date 类有如下两个构造方法：
Date()：Date 类的无参数构造方法获取的是系统当前的时间，显示的顺序为星期、月、日、小时、分、秒、年
Date(long date)：Date 类带 long 类型参数的构造方法获取的是距离 GMT 指定毫秒数的时间，60000 毫秒是一分钟。
注意：
1)GMT时间是格林尼治标准时间;CST时间是指包含中国,美国,巴西,澳大利亚四个时区的时间
2)GMT（格林尼治标准时间）与 CST相差 8 小时 => 1970 年 1 月 1 日 00:00:00 GMT 与 1970 年 1 月 1 日 08:00:00 CST 表示的是同一时间。 `我们一般使用1970 年 1 月 1 日 08:00:00 作为java中的时间原点`
1970 年 1 月 1 日 00:00:00 CST 使用 Date 对象表示为:Thu Jan 01 08:00:00 CST 1970;距离 1970 年 1 月 1 日 00:00:00 CST 一分钟的时间为 1970 年 1 月 1 日 00:01:00 CST，使用 Date 对象表示为:Thu Jan 01 08:01:00 CST 1970

实例：
1)获取系统当前的时间：`Date date = new Date();`
2)获取时间原点:`Date date = new Date(0);`
3)获取距时间原点（CST）指定毫秒数的的时间：`Date date = new Date(60000);`
3)获取距时间原点（CST）指定毫秒数的的时间：`Date date = new Date(1567912944032L);;`

2. 常用方法
String toString() 将此Date对象转换为String的形式
long getTime() 返回自1970年1月1日以来，由 Date对象表示的00:00:00 GMT的毫秒数
void setTime(long time) 设置此 Date对象以表示1970年1月1日00:00:00 GMT后的 time毫秒的时间点
boolean after(Date when) 判断此日期是否在指定日期之后
boolean before(Date when) 判断此日期是否在指定日期之前
boolean equals(Object obj) 比较两个日期的相等性
int compareTo(Date anotherDate)	比较两个日期的顺序

四、Calendar类
1. 作用
Calendar 类是一个抽象类，它为特定瞬间与 YEAR、MONTH、DAY_OF—MONTH、HOUR 等日历字段之间的转换提供了一些方法，并为操作日历字段（如获得下星期的日期） 提供了一些方法。

2. 创建 Calendar 对象
创建 Calendar 对象不能使用 new 关键字，因为 Calendar 类是一个抽象类，但是它提供了一个 getInstance() 方法来获得 Calendar类的对象。getInstance() 方法返回一个 Calendar 对象，其日历字段已由当前日期和时间初始化。
```
Calendar c = Calendar.getInstance();
```
3. 日历对象=>日期对象
```
Date date = c.getTime();
```
4. Calendar 类中定义了许多常量,分别表示不同的意义
- Calendar.YEAR：年份。
- Calendar.MONTH：月份。
- Calendar.DATE：日期。
- Calendar.DAY_OF_MONTH：日期，和上面的字段意义完全相同
- Calendar.DAY_OF_WEEK：星期几。
- Calendar.HOUR：12小时制的小时。
- Calendar.HOUR_OF_DAY：24 小时制的小时。
- Calendar.MINUTE：分钟。
- Calendar.SECOND：秒。
- Calendar.MILLISECOND：毫秒

5. Calendar 对象中的一些方法:
1)Date getTime()        由日历对象返回日期对象
2)setTime(Date date)    使用给定的 Date设置此日历的时间
3)int get(int field)	返回指定日历字段的值 => `int year = c.get(Calendar.YEAR);` Calendar 对象调用 get() 方法可以获取有关年、月、日等时间信息，参数 field 的有效值由 Calendar 静态常量指定。
4)set(..)方法
void set(int field, int value)为指定的日历字段设置给定值
void set(int year, int month, int date);
void set(int year, int month, int date, int hourOfDay, int minute);
void set(int year, int month, int date, int hourOfDay, int minute, int second);
5)void add(int field, int amount)	根据日历的规则，为给定的日历字段 field 添加或减去指定的时间量 amount

五、DateFormat类
获取当前日期对象后需要格式化
```
// 获取当前日期对象
Date d = new Date();//Wed Sep 11 13:15:42 CST 2019
// 获取日期格式器:getDateInstance() - 获取默认格式化样式为默认的 FORMAT语言环境的日期格式化 程序 yyyy-MM-dd
DateFormat dateformat = DateFormat.getDateInstance();
//将日期格式化成日期字符串=>用字符串变量接收转换后的日期字符串
String dStr = dateformat.format(d);
```
常用方法：
`日期+时间`
1. String format(Date date) - 将日期格式化成日期/时间字符串
`日期`
2. static DateFormat getDateInstance()           - 获取默认格式化样式为默认的 FORMAT语言环境的日期格式化 程序 -yyyy-MM-dd
3. static DateFormat getDateInstance(int style)  - 获取默认的 FORMAT区域设置的给定格式化样式的日期格式化 程序 。 
    style为要格式话的样式：取值为0,1,2,3;对应的格式为FULL,LONG,MEDIUM,SHORT
    style的2种写法，4个不同的值:
    0 = DateFormat.FULL    - 2019年9月9日 星期一
    1 = DateFormat.LONG    - 2019年9月9日
    2 = DateFormat.MEDIUM  - 2019-9-9
    3 = DateFormat.SHORT   - 19-9-9
实例：`DateFormat df = DateFormat.getDateInstance(DateFormat.FULL);`
4. static DateFormat - getDateInstance(int style, Locale aLocale) - 获取给定区域设置的给定格式化样式的日期格式化程序(日期的格式化+国际化)
    Locale类中定义了国际化常量：
    Locale.CHINESE
    Locale.SIMPLIFIED_CHINESE   - CN                                        2019年9月9日
    Locale.TRADITIONAL_CHINESE  - TW                                        2019年9月9日
    Locale.CHINA                - CHINA = SIMPLIFIED_CHINESE                2019年9月9日
    Locale.PRC                  - PRC = SIMPLIFIED_CHINESE                  2019年9月9日
    Locale.TAIWAN               - TAIWAN = TRADITIONAL_CHINESE              2019年9月9日
    Locale.ENGLISH                                                          September 9, 2019
    Locale.UK                                                               09 September 2019
    Locale.US                                                               September 9, 2019

实例：`DateFormat df = DateFormat.getDateInstance(DateFormat.LONG, Locale.CHINESE);`

`时间`
5. static DateFormat - getTimeInstance() - 获取默认格式化样式为默认的 FORMAT语言环境的时间格式化 程序
实例：`DateFormat df = DateFormat.getTimeInstance();`
6. static DateFormat - getTimeInstance(int style) - 获取默认的 FORMAT区域设置的给定格式化样式的时间格式化 程序 
    0 = DateFormat.FULL    - 下午11时49分21秒 CST
    1 = DateFormat.LONG    - 下午11时49分21秒
    2 = DateFormat.MEDIUM  - 23:49:21
    3 = DateFormat.SHORT   - 下午11:49
实例：`DateFormat df = DateFormat.getTimeInstance(DateFormat.FULL);` 下午11时49分21秒 CST
7. static DateFormat - getTimeInstance(int style, Locale aLocale) - 获取给定区域设置的给定格式化样式的时间格式化程序
实例：`DateFormat df = DateFormat.getTimeInstance(DateFormat.MEDIUM,Locale.CHINA);`  23:53:33
8. static DateFormat - getDateTimeInstance() - 取默认格式化样式的日期/时间格式化程序默认的 FORMAT区域设置
实例：`DateFormat df1 = DateFormat.getDateTimeInstance();`  2019-9-10 0:01:20
9. static DateFormat - getDateTimeInstance(int dateStyle, int timeStyle, Locale aLocale)  - 获取给定区域设置的给定格式样式的日期/时间格式化程序。 
实例：`DateFormat df1 = DateFormat.getDateTimeInstance(DateFormat.LONG,DateFormat.MEDIUM,Locale.CHINA);`  2019年9月11日 13:42:44

10. 将日期格式化成日期/时间字符串 <=>  把字符串反向解析成一个date对象
```
String s = "2019年9月11日 13:42:44";
DateFormat df = DateFormat.getDateTimeInstance(DateFormat.LONG,DateFormat.MEDIUM,Locale.CHINA);//与给定的字符串的样式相同
Date d = df.parse(s);
System.out.println(d);//Wed Sep 11 13:42:44 CST 2019
```

六、SimpleDateFormat 类
1. 如果使用 DateFormat 类格式化日期/时间并不能满足要求,那么就需要使用 DateFormat 类的子类——SimpleDateFormat。
2. SimpleDateFormat 是一个以与语言环境有关的方式来格式化和解析日期的具体类，它允许进行格式化（日期→文本）、解析（文本→日期）和规范化。       SimpleDateFormat 使得可以选择任何用户定义的日期/时间格式的模式。
### 使用步骤：
1. 使用SimpleDateFormat类的构造函数(构造方法)构造格式化日期的格式
2. 通过format(Date date)方法将指定的日期对象格式化为指定格式的字符串
    SimpleDateFormat 类主要有如下 3 种构造方法：
    SimpleDateFormat()：用默认的格式和默认的语言环境构造 SimpleDateFormat。
    SimpleDateFormat(String pattern)：用指定的格式和默认的语言环境构造 SimpleDateFormat。
    SimpleDateFormat(String pattern,Locale locale)：用指定的格式和指定的语言环境构造 SimpleDateFormat。
实例：
```
//创建Date对象，获取当前时间
Date d = new Date();
//设置时间格式
SimpleDateFormat sdf1 = new SimpleDateFormat("yyyy-MM-dd HH:mm:ss");
System.out.println(sdf1.format(d));//2019-09-10 11:23:58
```

参考：
http://c.biancheng.net/view/876.html

http://c.biancheng.net/view/878.html

cnblogs.com/lijingran/p/9125800.html

https://www.jianshu.com/p/d6e391f12ab3