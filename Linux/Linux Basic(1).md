## Linux基础(1)

---
### ls

```
	-l：长格式
		文件类型：
			-：普通文件 (f)
			d: 目录文件
			b: 块设备文件 (block)
			c: 字符设备文件 (character)
			l: 符号链接文件(symbolic link file)
			p: 命令管道文件(pipe)
			s: 套接字文件(socket)
		文件权限：9位，每3位一组，每一组：rwx(读，写，执行), r--
		文件硬链接的次数
		文件的属主(owner)
		文件的属组(group)
		文件大小(size)，单位是字节
		时间戳(timestamp)：最近一次被修改的时间
			访问:access
			修改:modify，文件内容发生了改变
			改变:change，metadata，元数据
	-h：做单位转换
	-a: 显示以.开头的隐藏文件
		. 表示当前目录
		.. 表示父目录
	-A 列示所有条目，除了 .（点）和 ..（点-点）
	-d: 显示目录自身属性
	-i: index node, inode
	-r: 逆序显示
	-R: 递归(recursive)显示
```
---

### 内置命令

* 命令类型：
	* 内置命令(shell内置)，内部，内建
	* 外部命令：在文件系统的某个路径下有一个与命令名称相应的可执行文件
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
	设备文件：
		块设备：随机访问，数据块
		字符设备：线性访问，按字符为单位
		设备号：主设备号（major）和次设备号（minor）
* /etc：配置文件
* /home：用户的家目录，每一个用户的家目录通常默认为/home/USERNAME
* /root：管理员的家目录；
* /lib：库文件
	静态库,  .a
	动态库， .dll, .so (shared object)
	/lib/modules：内核模块文件
* /media：挂载点目录，移动设备
* /mnt：挂载点目录，额外的临时文件系统
* /opt：可选目录，第三方程序的安装目录
* /proc：伪文件系统，内核映射文件
* /sys：伪文件系统，跟硬件设备相关的属性映射文件
* /tmp：临时文件, /var/tmp
* /var：可变化的文件
* /bin: 可执行文件, 用户命令
* /sbin：管理命令

* /usr：shared, read-only
	/usr/bin
	/usr/sbin
	/usr/lib
	
* /usr/local：
	/usr/local/bin
	/usr/local/sbin
	/usr/local/lib

### 其他常见命令

* cd
    * cd ~USERNAME: 进入指定用户的家目录
	* cd -:在当前目录和前一次所在的目录之间来回切换
* pwd: 当前路径
* date: 时间管理
* cal: 日历
* man:命令手册
    1. 用户命令(/bin, /usr/bin, /usr/local/bin)
    2. 系统调用
    3. 库用户
    4. 特殊文件(设备文件)
    5. 文件格式(配置文件的语法)
    6. 游戏
    7. 杂项(Miscellaneous)
    8. 管理命令(/sbin, /usr/sbin, /usr/local/sbin)
    9. 手册内容提示:
        * <>：必选
        * []：可选
        * ...：可以出现多次
        * |：多选一
        * {}：分组
* mkdir：创建空目录
	* -p: 创建丢失中间路径名称目录。如果没有指定 -p 标志，那么每个新创建的目录的父目录必须已经存在。
	* -v: 提示信息
* tree：查看目录树
* rmdir: 删除目录
	* -p: 删除空目录
* stat: 显示文件的状态信息
* touch 
	* -a 只更改存取时间
	* -m 只更该变动时间
	* -t 使用指定的日期时间，而非现在的时间
* rm
	* -i 提示信息
	* -f 强制删除
	* -r 递归目录
* cp： 复制命令(复制)
	* -r/R 递归	
	* -i  覆盖提示信息
	* -f 强制
	* -p 保留源文件属性
	* -a：归档复制，常用于备份
	* -d：当复制符号连接时，把目标文件或目录也建立为符号连接，并指向与源文件或目录连接的原始文件或目录；
```
    cp /etc/{passwd,inittab,rc.d/rc.sysinit} /tmp/
```
* mv: 移动文件(剪切)
* install
	-d: 创建目录
	-D: 创建<目的地>前的所有主目录，然后将<来源>复制至 <目的地>
```
    install a/e c
    <==>
    cp a/e c  #注意c必须是文件。
```