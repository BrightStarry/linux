####Linux 学习

如何设置root用户的密码
第一步：sudo passwd 
第二步：输入密码
第三步：确认密码
这样三个步骤过后root用户的密码就设置好了
切入root用户，  su root     输入刚刚设置好的密码就可以了

虚拟机网卡设置成桥接，可以无需配置linux的网络。

clear 清空命令行

uname -r 查看内核版本

yum update 更新yum

yum list installed |grep java   查看是否安装了java

ping ctrl + C 停止ping，不然会一直ping下去

yum -y list java*  查找yum中java开头的安装包

yum -y install java-1.7.0-openjdk*  安装java

shift + PgUp PgDn  上下翻页  （注意，不是箭头，麻痹的）

pwd 当前所处目录

netstat -an|grep xxxx 查看xxxx端口的状态 如果有，且状态为listen，就是成功的。

ifconfig 查看ip

rm  [文件] 删除 -f 删除文件  -r删除目录  -rf删除目录，包括目录下文件

touch x  创建一个空文件
mkdir x 创建一个文件夹

ll 查看当前目录下所有文件即详细信息（-开头是文件，d开头是文件夹，l开头是快捷方式） 是ls -l 的简写 ls -a 表示显示隐藏文件

rwx： r读权限，w写权限，x执行权限。
rwxr-xr-x 分别是文件所有者的权限，所属组的权限和其他人的权限

cat x 查看文件，但只显示一行
more 查看文件，显示所有 使用 space 翻页，回车显示下一行，q或ctrl+c退出
head -number x 和 tall -number x 查看文件前x行 和 查看文件后x行

ln [源文件][目标文件] 创建硬链接文件 -s创建软链接文件   
软链接：权限为所有人，并且指向源文件，类似windows的快捷方式
硬链接：类似copy。但它对修改同步。它不能跨文件系统分区，软链接可以

cp [源文件] [目标文件]  复制文件  -r 拷贝文件夹下的所有文件

mv [源文件名] [新文件名] 修改文件名
mv [源文件名] [新文件夹位置+新文件名] 移动文件位置

chown user 文件  改变文件所有者
charp 改变文件所属组

useradd username  添加用户
passwd username 为用户设置密码

chmod 761 [文件目录] 改变权限 
文件的w权限不代表能够删除该文件，只有获取到该文件所属文件夹的w，才能删除该文件
 

su - root 切换到root

service iptables status 查看防火墙状态

systemctl stop firewalld.service 关闭防火墙 这个是centos7的默认防火墙，7以下默认是iptables的
systemctl disable firewalld.service #禁止firewall开机启动

hostname xx 修改主机名

http://www.imooc.com/article/16448 安装docker

redis1  安装  
http://blog.csdn.net/csujiangyu/article/details/49278801
http://www.imooc.com/article/16526 
http://blog.csdn.net/han_cui/article/details/54098061
$ wget http://download.redis.io/releases/redis-3.2.8.tar.gz
$ tar xzf redis-3.2.8.tar.gz
$ cd redis-3.2.8
$ make
2、run(在redis-3.2.8目录中)
$ src/redis-server
或者
$ src/redis-server redis.conf
3、测试
$ src/redis-cli
redis> set foo bar
OK
redis> get foo
"bar"
 redis停止命令：
pikll redis-server

find [搜索范围路径] -name [文件名]  根据文件名查找文件  * 任意字符 ? 一个字符
find [搜索范围路径] -size [(+-)文件大小] 根据文件大小查找（以数据块为单位，一个数据块是512bit）
find [搜索范围路径] -user [用户名] 根据所属用户查找
find [搜索范围路径] -type [文件类型] f表示二进制，l表示软连接 d表示目录
还可以根据时间查找
可以用 -a and 和 -o 或 拼接 -name -size 这些条件
find ... -exec [执行命令] {}\; 可以在查找到文件后，执行命令，例如删除文件 -ok也是执行命令，但是执行前会确认下

gzip [文件名] 压缩文件 ，不保留源文件，且只能压缩文件，不能压缩目录
gunzip [已压缩文件] 解压缩文件，不保留源文件
tar [zcvf] [zxvf] [打包文件名.tar.gz] [源文件] 
c产生打包文件（必选） x产生解压缩文件（必选） v显示详细信息 f指定压缩后文件名 z打包同时压缩
zip -r [压缩后文件名] [源文件]  压缩成zip
unzip -d [解压缩的文件] 

shutdown -h now 关机 
reboot 重启
ctrl+l 清屏
ctrl +c 退出

grep 将指定内容过滤然后输出
| 将一个命令的输出传送给另一个命令
&&  第一个命令成功了才执行第二个  || 第一个和第二个，有一个成功了就ok
tab 补全
ls . > a.log 把命令执行的结果保存到文件中
ls . >> a.log 把命令执行的结果追加保存到文件中



vim 
命令模式  esc
插入模式  i a o 
编辑模式  : 
编辑模式下 
	:set nu 显示行号 nonu 取消行号	
	yy 复制当前行， dd 剪切当前行 p 粘贴

:q! 退出保存
:qw 保存退出
ZZ快捷键 保存修改并退出
