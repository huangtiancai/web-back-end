### 注解-Annotation
### Annotation的作用
- 不是程序本身，可以对程序作出解释
- 可以被其他程序（比如：编译器等）读取（注解 => 信息处理流程）
### Annotation的格式

### Annotation在哪里使用？
- 可以附加在package、class、method、field等上面，相当于给他们添加了额外的辅助信息
 
### 内置的注解
- @Override - 检查该方法是否是重载方法。如果发现其父类，或者是引用的接口中并没有该方法时，会报编译错误。
- @Deprecated - 标记过时方法。如果使用该方法，会报编译警告。
- @SuppressWarnings - 指示编译器去忽略注解中声明的警告。
  参数：deprecation、unchecked、path、serial、finally、all...
  @SuppressWarnings("all")
  @SuppressWarnings(value={"unchecked","deprecation"})

### 元注解
元注解负责注解其他注解，被用来提供对其它Annotation类型作说明
java.lang.annotation包：
- @Target
- @Retention
- @Documneted
- @Inherited


