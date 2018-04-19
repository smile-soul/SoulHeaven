## Linux(1)-基础命令

---
### 基础常用命令

* [Linux命令网站](http://man.linuxde.net/)

####  目录管理: ls、cd、pwd、mkdir、rmdir、tree、install

* ls

```
	-l: 长格式
		文件类型: 
			-: 普通文件 (f)
			d: 目录文件
			b: 块设备文件 (block)
			c: 字符设备文件 (character)
			l: 符号链接文件(symbolic link file)
			p: 命令管道文件(pipe)
			s: 套接字文件(socket)
		文件权限: 9位，每3位一组，每一组: rwx(读，写，执行), r--
		文件硬链接的次数
		文件的属主(owner)
		文件的属组(group)
		文件大小(size)，单位是字节
		时间戳(timestamp): 最近一次被修改的时间
			访问:access
			修改:modify，文件内容发生了改变
			改变:change，metadata，元数据
	-h: 做单位转换
	-a: 显示以.开头的隐藏文件
		. 表示当前目录
		.. 表示父目录
	-A 列示所有条目，除了 .（点）和 ..（点-点）
	-d: 显示目录自身属性
	-i: index node, inode
	-r: 逆序显示
	-R: 递归(recursive)显示
```
* cd:
	* cd ~USERNAME: 进入指定用户的家目录
	* cd -:在当前目录和前一次所在的目录之间来回切换
* pwd: 当前路径
* mkdir: 创建空目录
	* -p: 创建丢失中间路径名称目录。如果没有指定 -p 标志，那么每个新创建的目录的父目录必须已经存在。
	* -v: 提示信息
```
	mkdir -p a/{m,y} <=> mkdir -pv a/m a/y
	mkdir -pv /mnt/test/{x/m,y}

	命令行展开: 
	mkdir -p a/{a,d}_{b,c} <=> mkdir -p a/{a_b, a_c, d_b, d_c}
	(a+d)(b+c) = ab,ac,db,dc
	{a,d}_{b,c} = a_b, a_c, d_b, d_c
```
* tree: 查看目录树
* rmdir: 删除目录
	* -p: 删除空目录
* install
	-d: 创建目录
	-D: 创建<目的地>前的所有主目录，然后将<来源>复制至 <目的地>
```
    install a/e c <=> cp a/e c  #注意c必须是文件。
```
#### 文件管理: touch、stat、file、rm、cp、mv

* touch 
	* -a 只更改存取时间
	* -m 只更该变动时间
	* -t 使用指定的日期时间，而非现在的时间
* stat: 显示文件的状态信息
* file: 用来探测给定文件的类型
* rm
	* -i 提示信息
	* -f 强制删除
	* -r 递归目录
* cp:  复制命令(复制)
	* -r/R 递归	
	* -i  覆盖提示信息
	* -f 强制
	* -p mode 属组
	* -P 保持链接自有的属性
	* -a 归档复制，常用于备份
	* -d == -P 当复制符号连接时，把目标文件或目录也建立为符号连接，并指向与源文件或目录连接的原始文件或目录
	* -a == -rd
```
    cp /etc/{passwd,inittab,rc.d/rc.sysinit} /tmp/
```
* mv: 移动文件(剪切)

#### 日期时间: date、cal

* date: 时间管理
* cal: 日历

#### 查看文本: cat、tac、more、less、head、tail

* cat: 连接并显示
	-n 显示行号
	-E 显示行尾  $为结束符 (macOs -e)
* tac: 已行为单位的反序输出
* cat tac more less都为查看文件
	* [cat more less 区别](https://blog.csdn.net/xyw_blog/article/details/16861681)
* head: 查看前n行 
* tail: 查看后n行
	tail -f: 查看文件尾部，不退出，等待显示后续追加至此文件的新内容

#### 文本处理: cut、join、sed、awk

cut:
	-d: 指定字段分隔符，默认是空格
	-f: 指定要显示的字段
		-f 1,3
		-f 1-3

文本排序：sort
	-n：数值排序
	-r: 降序
	-t: 字段分隔符
	-k: 以哪个字段为关键字进行排序
	-u: 排序后相同的行只显示一次
	-f: 排序时忽略字符大小写
	
uniq: 
	-c: 显示文件中行重复的次数
	-d: 只显示重复的行
	
文本统计：wc (word count)
	-l 行数
	-w 单词
	-c 字节数
	-L 最长一行包含多少字节


#### 内置命令

* 命令类型: 
	* 内置命令(shell内置)，内部，内建
	* 外部命令: 在文件系统的某个路径下有一个与命令名称相应的可执行文件
    * type: 显示指定属于哪种类型
```
    type pwd
    # pwd is a shell builtin
    type chmod
    # chmod is /bin/chmod
    type ls
    # ls is an alias for ls -G
```

### 文件系统

* /boot: 系统启动相关的文件，如内核、initrd，以及grub(bootloader)
* /dev: 设备文件
	设备文件: 
		块设备: 随机访问，数据块
		字符设备: 线性访问，按字符为单位
		设备号: 主设备号（major）和次设备号（minor）
* /etc: 配置文件
* /home: 用户的家目录，每一个用户的家目录通常默认为/home/USERNAME
* /root: 管理员的家目录；
* /lib: 库文件
	静态库,  .a
	动态库， .dll, .so (shared object)
	/lib/modules: 内核模块文件
* /media: 挂载点目录，移动设备
* /mnt: 挂载点目录，额外的临时文件系统
* /opt: 可选目录，第三方程序的安装目录
* /proc: 伪文件系统，内核映射文件
* /sys: 伪文件系统，跟硬件设备相关的属性映射文件
* /tmp: 临时文件, /var/tmp
* /var: 可变化的文件
* /bin: 可执行文件, 用户命令
* /sbin: 管理命令

* /usr: shared, read-only
	/usr/bin
	/usr/sbin
	/usr/lib
	
* /usr/local: 
	/usr/local/bin
	/usr/local/sbin
	/usr/local/lib


