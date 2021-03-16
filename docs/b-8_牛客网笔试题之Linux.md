> 作者：optics915。
>
> **介绍:** 这是一个随手化的类似笔记的个人博客 作者: **[optics915](https://optics915.gitee.io/docsify-blog)** 。一般会在此记录一些从知乎、B站、GitHub上学来的有意思的操作，每一个过程都先自己操作成功之后再将其记录下来，以方便日后碰到相似类型时有理可依。
    
这个系列的文章是之前在牛客网上做基础题时遇到的一些自己认为有难度以及做错的题目，某种程度上这些题目可以给面试带来一些辅助作用，很多是基础问题，有利于面试前的突击。

#### 1. linux修改路由的命令是？
		a. 选项	A
			i. route
			ii. tracert
			iii. ping
			iv. netstat
		b. 解析
			i. route：route命令是在本地 IP 路由表中显示和修改路由。
			ii. tracert：tracert（跟踪路由）是路由跟踪实用程序，用于确定 IP 数据包访问目标所采取的路径。tracert 命令用 IP 生存时间 (TTL) 字段和 ICMP 错误消息来确定从一个主机到网络上其他 主机的路由。  
			iii. ping：ping命令可以检查网络是否连通。
			iv. netstat：netstat是控制台命令,是一个监控TCP/IP网络的非常有用的工具，它可以显示路由表、实际的网络连接以及每一个网络接口设备的状态信息。
#### 2. 以下的命令得在（ ）自动执行： 
		a. 06 03 * * 3 lp /usr/local/message | mail -s "server message" root
		b. 选项	C
			i. 每周三06:03分
			ii. 每周六03:03分
			iii. 每周三03:06分
			iv. 每周六03:06分
		c. 解析 
			i. 分　 时　 日　 月　 周　 命令
                第1列表示分钟1～59 每分钟用*或者 */1表示
                第2列表示小时1～23（0表示0点）
                第3列表示日期1～31
                第4列表示月份1～12
                第5列标识号星期0～6（0表示星期天）
                第6列要运行的命令
			ii. *  表示  
				1) 第1列时：表示每分钟都要执行一次， 
				2) 第2列时：表示每小时都要执行一次，依次类推，
#### 3. 如果系统的umask设置为244，创建一个新文件后，它的权限：（）
		a. 选项	A
			i. --w-r--r--
			ii. -r-xr--r--
			iii. -r---w--w-
			iv. -r-x-wx-wx
		b. 解析
			i. linux系统中权限rwx对应数值为421，故文件权限为r-- -w- -w-
#### 4. 修改/etc/sysctl.conf如下哪项参数可以开启Linux流量转发功能（）
		a. 选项	C
			i. net.ipv4.conf.all.rp_filter = 0
			ii. net.ipv4.conf.default.rp_filter = 0
			iii. net.ipv4.ip_forward = 1
			iv. net.ipv4.conf.all.rp_filter = 1
			v. net.ipv4.conf.default.rp_filter = 1
			vi. net.ipv4.ip_forward = 0
		b. 解析
			i. 可以通过命令：cat /proc/sys/net/ipv4/ip_forward查看，1为开启Linux流量转发，0为禁止使用 

			ii. rp_filter参数有三个值，0、1、2，具体含义： 
				1) 0：不开启源地址校验。 
				2) 1：开启严格的反向路径校验。对每个进来的数据包，校验其反向路径是否是最佳路径。如果反向路径不是最佳路径，则直接丢弃该数据包。 
				3) 2：开启松散的反向路径校验。对每个进来的数据包，校验其源地址是否可达，即反向路径是否能通（通过任意网口），如果反向路径不同，则直接丢弃该数据包。
#### 5. 使用什么命令把两个文件的合并成一个文件？
		a. 选项	A
			i. cat
			ii. grep
			iii. awk
			iv. cut
		b. 解析
			cat 【 Concatenate 连接】	  1：cat file1 file2 > file3 ：将两个文件拼接在一起生成一个新的文件
				       2：cat file1 >> file2  ：将文件1直接接在文件2的结尾
			grep【global regular expression print通用规则表达式输出】	找出检索内容所在的行
				可以从一个或者多个文件中搜索特定的字符串模式
			awk 【Aho Weiberger and Kernighan】 三个作者的姓的第一个字母 	在文件或字符串中基于指定规则浏览和抽取信息，awk '{if($4~/Brown/) print $0}' tab2
			cut 剪切	从文本文件的每一行中截取指定内容的数据。
#### 6. 在RHEL5系统中，小王希望将他执行的ls命令的输出结果保存在当前目录下文件output.ls中，以供日后进行分析和使用，但要求不覆盖原文件的内容，他应该使用的命令是（  ）
		a. 选项	B
			i. ls>output.ls
			ii. ls>>output.ls
			iii. ls<<output.ls
			iv. ls—output.ls
		b. 解析
			i.  > 	输出重定向到一个文件或设备 覆盖原来的文件
			    >!  输出重定向到一个文件或设备 强制覆盖原来的文件
			    >>  输出重定向到一个文件或设备 追加原来的文件
			    <   输入重定向到一个程序 
#### 7. cp拷贝命令的-f参数含义为?
		a. 选项	D
			i. 拷贝目录
			ii. 递归处理
			iii. 显示执行过程
			iv. 强制进行拷贝
		b. 解析
			i. -r ：recursive，递归处理
			ii. -v ：verbose，显示详细过程
			iii. -f ：force，强制执行，多用于覆盖拷贝。无论目的目录是否有同名文件，强制复制
#### 8. 在Linux中,对file.sh文件执行#chmod 645 file.sh中,该文件的权限是()
		a. 选项	D
			i. -rw-r--r--
			ii. -rw-r--rx-
			iii. -rw-r--rw-
			iv. -rw-r--r-x
		b. 解析
			i. 以数字来表示权限
				1) r: 对应数值4 
				2) w: 对应数值2 
				3) x：对应数值1 
				4) －：对应数值0 
			ii. 数字设定的关键是mode的取值，一开始许多初学者会被搞糊涂，其实很简单，我们将rwx看成二进制数，如果有则有1表示，没有则有0表示，那么-rw- r--r-x则可以表示成为： 
				1) 110 100 101 
				2) 再将其每三位转换成为一个十进制数，就是645。
#### 9. 在RHEL5系统中，下面关于shell环境变量配置文件的描述，正确的是（  ）
		a. 选项	A
			i. 用户登录系统时，bash首先执行/etc/profile配置文件和/etc/profile.d/目录下的配置文件，这些配置文件对所有用户都有效
			ii. 用户登录系统时，bash首先执行.bash_profile文件和.bashrc文件，这些配置文件对所有用户都有效
			iii. 用户主目录下的.bashrc设置为每次登录时执行，而.bash_profile则为每次打开新的终端时执行
			iv. 执行用户主目录下的环境变量配置文件时，不可以重复设置用户登录时配置文件中已经设置的选项
		b. 解析
			i. /ect/profile 
				1) 此文件为系统的每个用户设置环境信息,当用户第一次登录时,该文件被执行.并从 /etc/profile.d 目录的配置文件中搜集shell的设置.
			ii. /etc/bashrc 
				1) 为每一个 运行bash shell 的用户执行此文件.当bash shell被打开时,该文件被读取.
			iii. ~/.bash_profile 
				1) 每个用户都可使用该文件输入 专用于 自己使用的shell信息, 当用户登录时,该文件仅仅执行一次 !默认情况下,他设置一些环境变量,执行~/.bashrc文件.
			iv. ~/.bashrc 
				1) 该文件包含专用于用户的bash shell的bash信息 ,当登录时以及每次打开新的shell时,该文件被读取 .
			v. ~/.bash_logout 
				1) 当每次退出系统(退出bash shell)时,执行该文件.
