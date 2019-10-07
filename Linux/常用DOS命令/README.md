DOS:Disk Operating System => 磁盘操作系统
DOS命令:指DOS操作系统的命令，是一种面向磁盘的操作命令，主要包括目录操作类命令、磁盘操作类命令、文件操作类命令和其它命令


## 目录命令
1. 一般打开DOS命令窗口的目录是 C:\Users\用户名>
2. 输入"cd\"敲回车会直接退回到C盘根目录
3. 在CMD程序里输入盘符如"e:",大小写均可
4. 在DOS命令下尽量使用"\"
下面介绍一些重要命令：
1. `md/mkdir`
作用：创建一个子目录（make directory）
语法：`md[盘符：][路径名][子目录名]`
以md为例：
- md  E:\testDOS\test1
- md test1
- md testDOS\test4
mkdir testDOS/test4:错误

2. `cd`
作用：改变或显示当前目录（change directory 输入“cd\”敲回车会直接退回到C盘根目录）。
语法：cd `[盘符：][路径名][子目录名]`  => E:\>cd testDOS\test2
PS：路径可以使用绝对路径和相对路径两种。
- 在根目录去往指定目录：`cd testDOS/test1` , `cd testDOS\test1`
- 在testDOS目录下：`cd test1`
- 回到根目录:`cd /`,`cd\`,`cd/`,`cd \`
- 回到上级目录:`cd../`,`cd..`
- 显示当前路径:`cd`  

3. `rd`
作用：删除空子目录（remove directory）。
语法：`rd [盘符：][路径名][子目录名]`
`rd E:\testDOS\test1`
注意：如果`E:\testDOS\test1`目录下有文件（非空）
会出现如下情况：
```
D:\>rd E:\testDOS\test1
目录不是空的
```
故`rd`是专门删除空子目录的命令

4. `del`- 删除文件命令
- 删除当前文件夹下的文件：del 文件名.文件类型 => del 1.txt
- 删除文件夹下所有文件：del 文件夹目录 => del test1
- 删除指定的文件:del  e:\testDOS\test1\1.txt
cd testDOS
5. `dir` 
作用：主要用来显示一个目录下的文件和子目录。(directory)
语法：`dir  [盘符：][路径名][filename][/o][/s][/p][/w][/a]`如：`dir e:\testDOS\test1\1.txt`
>斜杠表示后面的内容是参数:
/p 显示信息满一屏时，暂停显示，按任意键后显示下一屏
/o 排序显示。o后面可以接不同意义的字母
/w 只显示文件名目录名，每行五个文件名。即宽行显示
/s 将目录及子目录的全部目录文件都显示
/a 显示隐藏文件

6. cls 清屏幕命令
7. ver 查看系统版本号命令

8. ping命令
作用：ping命令不仅可以测试网络是否通，而且还可以粗略的判断网络传输质量。
语法：`ping +空格+“IP地址或者域名” [-t][-l][-n]`



用法: ping [-t] [-a] [-n count] [-l size] [-f] [-i TTL] [-v TOS] 
           [-r count] [-s count] [[-j host-list] | [-k host-list]
           [-w timeout] [-R] [-S srcaddr] [-4] [-6] target_name
选项:
- `-t Ping 指定的主机，直到用户按Ctrl＋C键终止`,因为如果想用Ping命令测试网络传输质量，至少要查看Ping命令三分钟到五分钟的结果。
    若要查看统计信息并继续操作 - 请键入 Control-Break；
    若要停止 - 请键入 Control-C。
- `-a  将地址解析成主机名`
- `-n count` 在默认情况下，Ping命令一般都会发送四个数据包，通过这个命令可以自己定义发送的个数，对测试网络传输质量很有帮助
- `-l size`  定义echo数据包大小。我们可以将数据包的大小定义在极限值附近，以此可以测试出网络传输质量的优劣，尤其是测试外网的传输质量，非常明显

- `-f`       在数据包中设置“不分段”标志(仅适用于 IPv4)。
- `-i TTL`     生存时间。
- `-v TOS`         服务类型(仅适用于 IPv4。该设置已不赞成使用，且对 IP 标头中的服务字段类型没有任何影响)。
- `-r count`       记录计数跃点的路由(仅适用于 IPv4)。
- `-s count`       计数跃点的时间戳(仅适用于 IPv4)。
- `-j host-list`   与主机列表一起的松散源路由(仅适用于 IPv4)。
- `-k host-list`   与主机列表一起的严格源路由(仅适用于 IPv4)。
- `-w timeout`     等待每次回复的超时时间(毫秒)。
- `-R`             同样使用路由标头测试反向路由(仅适用于 IPv6)。
- `-S srcaddr`     要使用的源地址。
- `-4 `            强制使用 IPv4。
- `-6`             强制使用 IPv6。

9. tracert
作用：tracert命令可以测试路由器的工作是否正常（部分网站无法访问）。
我们根据返回的结果来判断，哪一个环节的网络出现了问题。
语法：`tracert +空格+"IP地址或者域名"`


10. 灵活使用ipconfig命令
作用：`ipconfig`这个命令查看计算机当前的网络配置信息。
- `ipconfig /all`：完全显示计算机的网络信息，IP地址、MAC地址及其他相关的信息，都可以显示出来。
- `ipconfig/release`：释放计算机当前获得的IP地址。对于使用动态IP地址的单位来说，如果发现机器无法上网，而计算机从DHCP服务器处获得的IP地址等相关信息不完全，可以将该地址释放。
`ipconfig /renew`：从DHCP服务器重新获得IP地址。释放了IP地址及相关信息之后，必须重新获得一个IP地址，直接输入此命令之后，便可以从DHCP服务器处获得一个IP地址。如果不用此命令，要想重新获得一个IP地址信息，需要重新启动计算机或注销计算机才行。

参考：https://www.jb51.net/article/140920.htm

11. net
作用：这个命令是网络命令中最重要的一个，必须透彻掌握它的每一个子命令的用法，因为它的功能实在是太强大了在这里，我们重点掌握几个常用的子命令:
- `net start`
使用它来启动远程主机上的服务。用法：net start servername
- `net stop`
使用它来停止远程主机上的服务
- `net view`
使用此命令查看远程主机的所有共享资源。命令格式为net view \IP。
- `net use`
把远程主机的某个共享资源影射为本地盘符，图形界面方便使用。命令格式为net use x: \IP\sharename。
- `net user`
查看和帐户有关的情况，包括`新建帐户`、`删除帐户`、`查看特定帐户`、`激活帐户`、`帐户禁用`等。
1)net user abcd 1234 /add，新建一个用户名为abcd，密码为1234的帐户，默认为user组成员。
2)net user abcd /del，将用户名为abcd的用户删除。
3)net user abcd /active:no，将用户名为abcd的用户禁用。
4)net user abcd /active:yes，激活用户名为abcd的用户。
5)net user abcd，查看用户名为abcd的用户的情况
- `net localgroup`　
查看所有和用户组有关的信息和进行相关操作。
- `net time`
这个命令可以查看远程主机当前的时间。




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
