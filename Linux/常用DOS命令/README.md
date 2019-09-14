1. 清除屏幕：cls
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
