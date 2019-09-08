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
