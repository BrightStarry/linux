####Linux 学习

如何设置root用户的密码
第一步：sudo passwd 
第二步：输入密码
第三步：确认密码
这样三个步骤过后root用户的密码就设置好了
切入root用户，  su root     输入刚刚设置好的密码就可以了

JDK
http://jingyan.baidu.com/article/642c9d34e7a9df644a46f720.html
http://blog.csdn.net/tonytfjing/article/details/42167599

虚拟机网卡设置成桥接，可以无需配置linux的网络。

clear 清空命令行

uname -r 查看内核版本

yum update 更新yum

yum list installed |grep java   查看是否安装了java

ctrl + c 退出

yum -y list java*  查找yum中java开头的安装包

yum -y install java-1.7.0-openjdk*  安装java

shift + PgUp PgDn  上下翻页  （注意，不是箭头，麻痹的）

pwd 当前所处目录

netstat -aon|grep xxxx 查看xxxx端口的状态 如果有，且状态为listen，就是成功的。

ifconfig 查看ip

rm  [文件] 删除 -f 删除文件  -r删除目录  -rf删除目录，包括目录下文件

touch x  创建一个空文件
mkdir x 创建一个文件夹 -p 递归创建 就是 /a/b/c这样字创建多个

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
	
命令模式下
    :/xx 可以查找xx，n表示下一个
    %s/[old]/[new]/g 全局替换

:q! 退出保存
:qw 保存退出
ZZ快捷键 保存修改并退出


####Docker容器 
    慕课网上看到的教程，试着学一下，顺便把Linux也学一下。
    今天乘着上班的空闲时间，在虚拟机上把docker（还有个redis）装好了。
--- 
    docker 教程
    http://www.runoob.com/docker/docker-tutorial.html

    CTRL + C 停止进程
    
    安装docker
    http://www.imooc.com/article/16448 
    
    启动
    systemctl start docker.service
    
    xx表示不同的命令如，pull、run等。可以查看该命令的帮助，所有参数
    docker xx --help
    
    获取镜像 name：镜像名  [:tag]：版本，默认为最新的（也就是会自己加上一个参数:latest）
    docker pull [options] name[:tag]
    
    上面的需要翻墙，下面的是指定 下载地址 。网易蜂巢不错。
    docker pull hub.c.163.com/public/redis:2.8.4 
    
    查看本机的镜像  
    docker images [options] [repository[:tag]]
    
    运行 image：镜像名字 command:命令 arg:命令的参数
    docker run [options] image[:tag][command][arg...]
    docker run -d image 后台运行，并打印出id
    -p 8080:80  进行端口映射，将nginx的80端口映射到主机的8080端口上，也就是别人访问8080，可以访问到自己的80
    -P 同上，不过是80端口映射到随机端口。
    查看目前正在运行的容器
    docker ps
    
    在运行的容器中执行命令 
    docker exec [options] container command [arg...]
    例如:   f：id中的字符
    docker exec -it f bash
    可以进入一个容器，和虚拟机中一样。相当于一个虚拟的linux。也就是容器内部
    
    停止运行容器 如果只有一个，f就是任意字符
    docker stop f
    
    
    制作镜像
    以下就是 打包镜像tomcat和jpress.war
    在某个目录创建文件 Dockerfile 使用vim，编辑输入如下内容：
        from images(镜像名)   （继承自哪个镜像）
        MAINTAINER ZX 970389745@qq.com  (维护人员信息)
        COPY jpress.war  /usr/local/tomcat/webapps    (同一目录下要打包成镜像的文件,拷贝到tomcat的运行目录下)

    然后在目录下使用  
    即可创建镜像，注意， . 是当前目录的意思
    docker build .   
    下面这句 -t是创建镜像并命名，因为上面的镜像没有命名
    docker build -t jpress:latest .
    
    运行容器
    -d表示后台运行 -p表示设置端口映射， jpress是镜像名
    docker run -d -p  8888:8080 jpress
    
    删除镜像
    docker rmi xx(名字或id)
    
    运行mysql镜像
    docker run -d -p 3306:3306 -e MYSQL_ROOT_PASSWORD=123456 -e MYSQL_DATABASE=xxx  images(镜像名)

---
### 静态IP  http://blog.csdn.net/johnnycode/article/details/40624403

1. 使用ifconfig 命令查看目前使用的ifcfg-xx是多少。
2. 使用vim /etc/sysconfig/network-scripts/ifcfg-xxx 命令修改该配置
3. 修改如下内容：
    BOOTPROTO="static" #dhcp改为static   
    ONBOOT="yes" #开机启用本配置  
    IPADDR=192.168.7.106 #静态IP  
    GATEWAY=192.168.7.1 #默认网关  
    NETMASK=255.255.255.0 #子网掩码  
    DNS1=114.114.114.114 #DNS 配置 
4. 保存，并重启网络。service network restart

如果能ping内网，ping不通外网，可以看下网关设置是否正确。

---
远程拷贝
scp  -r [路径/] 192.168.x.x:/xx/xx 
---

TAB键自动补全。贼好用

---
--- 
###Shell学习   这个突然不想看了，确实没什么用，用到的时候看下教程把
http://www.runoob.com/linux/linux-shell.html
sh example.sh 运行shell脚本

    #!/bin/sh  #开头规则
echo "xxx"  #输出语句
/bin/pwd #执行pwd命令

/bin/data #输出时间 
/bin/date +%f #格式化输出时间
/bin/date +%f >> /x/x/y.info #格式化输出时间，到文件

---
###安装tomcat    
http://www.cnblogs.com/hanyinglong/p/5024643.html

解压
tar -zxvf apache-tomcat-8.0.29.tar.gz  
改名
mv apache-tomcat-8.0.29 tomcat
启动
/zx/tomcat/bin/startup.sh
停止
/zx/tomcat/bin/shutdown.sh

启动java web 项目，将项目放到webapps目录下。

---
### 防火墙

service firewalld.service status 查看防火墙状态

systemctl stop firewalld.service 关闭防火墙 这个是centos7的默认防火墙，7以下默认是iptables的
systemctl disable firewalld.service #禁止firewall开机启动
---
测试端口是否打开
telnet [ip]  [端口]

---
### Mysql 
>
	yum -y install perl perl-devel
	yum -y install libaio-devel
	下载
	wget http://dev.mysql.com/get/Downloads/MySQL-5.7/mysql-5.7.13-linux-glibc2.5-x86_64.tar.gz
	解压
	tar -zxvf mysql-5.7.13-linux-glibc2.5-x86_64.tar.gz
	改名
	mv mysql-5.7.13-linux-glibc2.5-x86_64 mysql
	#添加用户组
	groupadd mysql
	#添加用户mysql 到用户组mysql
	useradd -g mysql mysql
	安装
	cd /zx/mysql/
	chown -R mysql:mysql  /usr/local/mysql /zx/mysql 
	mkdir /zx/mysql/data  -p
	mkdir /zx/mysql/log -p
	创建my.cnf文件
	vim /etc/my.cnf
	复制如下：
	[client]
	port = 3306
	socket = /zx/mysql/mysql.sock
	[mysqld]
	server_id=10
	port = 3306
	user = mysql
	character-set-server = utf8mb4
	default_storage_engine = innodb
	log_timestamps = SYSTEM
	socket = /zx/mysql/mysql.sock
	basedir = /zx/mysql
	datadir = /zx/mysql/data
	pid-file = /zx/mysql/data/mysql.pid
	max_connections = 1000
	max_connect_errors = 1000
	table_open_cache = 1024
	max_allowed_packet = 128M
	open_files_limit = 65535
	#####====================================[innodb]==============================
	innodb_buffer_pool_size = 1024M
	innodb_file_per_table = 1
	innodb_write_io_threads = 4
	innodb_read_io_threads = 4
	innodb_purge_threads = 2
	innodb_flush_log_at_trx_commit = 1
	innodb_log_file_size = 512M
	innodb_log_files_in_group = 2
	innodb_log_buffer_size = 16M
	innodb_max_dirty_pages_pct = 80
	innodb_lock_wait_timeout = 30
	innodb_data_file_path=ibdata1:1024M:autoextend

	#####====================================[log]==============================
	log_error = /zx/mysql/log/mysql-error.log 
	slow_query_log = 1
	long_query_time = 1 
	slow_query_log_file = /zx/mysql/log/mysql-slow.log
	sql_mode=NO_ENGINE_SUBSTITUTION,STRICT_TRANS_TABLES
	skip-grant-tables
	---
	初始化
	/zx/mysql/bin/mysqld --initialize --user=mysql --basedir=/zx/mysql --datadir=/zx/mysql/data  --innodb_undo_tablespaces=3 --explicit_defaults_for_timestamp
	如果配置了my.cnf的log_error，那么初始密码在log_error文件中，否则会打印出来。
	查看日志中的初始密码，密码是xlewthsu01I
	tail -f 300 /zx/mysql/log/mysql-error.log 
	继续安装
	/zx/mysql/bin/mysql_ssl_rsa_setup --datadir=/zx/mysql/data
	再次执行权限
	chown -R mysql:mysql  /zx/mysql /usr/local/mysql 
	配置启动文件
	cp /zx/mysql/support-files/mysql.server /etc/init.d/mysql
	chkconfig --add mysql
	chkconfig mysql on
	配置环境变量
	vim /etc/profile
	增加
	MYSQL_HOME=/zx/mysql
	PATH=$PATH:$MYSQL_HOME/bin
	使其生效
	source /etc/profile
	---
	BUG：Access denied for user 'root'@'localhost' (using password:YES)
	http://blog.csdn.net/skywalker_leo/article/details/47274441
	---
	BUG
	You must reset your password using ALTER USER statement before executing this statement.
	SET PASSWORD = PASSWORD('123456'); 
	---
	如果有问题，这么启动mysql start --skip-grant-tables

	---
	启动
	mysqld_safe --user=mysql &
	重启
	service mysql restart
	执行
	mysql -u root -p
	然后回车即可登录
	修改密码
	use mysql;
	update mysql.user set authentication_string=password('123456') where user='root';
	FLUSH PRIVILEGES;

	添加远程权限
	use mysql; 
	update user set host = '%' where user = 'root';
	测试
	select host, user from user;

>
















    
