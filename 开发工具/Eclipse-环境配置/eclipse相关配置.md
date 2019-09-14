![](https://i.loli.net/2019/03/11/5c85ff37289a1.jpg)
A java Runtime Environment (JRE) or Java Development Kit (JDK) must be available in order to run Eclipse. No Java virtual machine was found after searching the following locations……
首先要确定你的JDK已经安装好，环境变量也已经配置无误。

如果前面两个都没有问题，那就是路径的问题。

因为Eclipse需要javaw.exe来启动，程序会先查找path目录，如果没有找到，这会在eclipse的安装目录下查找，再找不到就会报如上的错误。

所以可以肯定的就是路径出问题了。来到eclipse的安装目录，找到eclipse.ini文件里的vm这两行：
如果没有这行加上这；两行
-vm
D:\java\j2sdk1.6.0_26_32\bin



#### 更换工作空间

左上角 file ->  Switch Workspace

