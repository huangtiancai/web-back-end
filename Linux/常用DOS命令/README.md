DOS:Disk Operating System => 磁盘操作系统
DOS命令:指DOS操作系统的命令，是一种面向磁盘的操作命令，主要包括目录操作类命令、磁盘操作类命令、文件操作类命令和其它命令

## 目录命令
1. md/mkdir
作用：创建一个子目录（make directory）
以md为例：
- mkdir test1
- mkdir testDOS\test4
mkdir testDOS/test4:错误

2. `cd`
作用：改变或显示当前目录（change directory）。
语法：cd [C:][path] => E:\>cd testDOS\test2
PS：路径可以使用绝对路径和相对路径两种。
- 在根目录去往指定目录：`cd testDOS/test1` , `cd testDOS\test1`
- 在testDOS目录下：`cd test1`
- 回到根目录:`cd /`,`cd\`,`cd/`,`cd \`
- 回到上级目录:`cd../`,`cd..`
- 显示当前路径:`cd`  






1. 清除屏幕：cl

2. cd
作用：改变或显示当前目录（change directory）。
语法：cd [C:][path]
PS：路径可以使用绝对路径和相对路径两种。
cd\ 表示退回到根目录。
cd.. 表示退回到上级目录。s
2. d: 去往D盘
3. 



2. 在DOS窗口、gitbash以及一些可以使用的命令行工具的界面上，输入：net stop mysql、net start mysql时，
总是提示：服务名无效。
原因是：因为net start +服务名，启动的是win下注册的服务。此时，系统中并没有注册mysql到服务中。即当前路径下没有mysql服务。
如何将MySQL注册到win服务里面？！！！（步骤如下）
(1).来到MySQL的安装路径下bin
cd C:\MySQL\bin
(2)在命令行中输入mysqld --install
成功：出现Service successfully install代表你已经安装成功，
(3)执行 net start mysql出现:
请求的服务已经启动。
