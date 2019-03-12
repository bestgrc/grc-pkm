## 一 Linux调度机制

> 参考资料
>
> - [Shell作业调度控制](http://m.blog.chinaunix.net/uid-20753768-id-702742.html?/6472.html)
> - [Linux 作业和进程](https://blog.csdn.net/u011436666/article/details/73650968)

### (1) 进程调度

> Linux提供了**抢占式**的**多任务**模式。

- 实时进程优先级 > 普通进程优先级
- 实时进程的调度算法
  - FIFO
  - RR



### (2) 作业调度

#### 1. 作业是什么

- 从操作系统的角度来讲，作业是计算机系统中运行的一项用户任务
- 在unix/linux系统中作业可以定义为：在命令行中输入的一个或一组命令。

#### 2. 作业的分类

- 前台作业
- 后台作业

#### 3. 作业的状态

- 前台
- 后台
- 挂起



> **进程和作业的区别：**
>
> - **区别**：进程是一个程序在一个数据集上的一次执行，而作业是用户提交给系统的一个任务。
> - **关系**：一个作业通常包括几个进程，几个进程共同完成一个任务，即作业。



## 二 fork与exec

### 1. 相同

- 都是用来创建进程的方法

### 2. 不同

| fork                                                         | exec                     |
| ------------------------------------------------------------ | ------------------------ |
| 创建子进程                                                   | 创建进程用以完成一定任务 |
| 复制当前进程(包括进程在内存里的堆栈数据)为1个新的镜像.然后这个新的镜像和旧的进程同时执行下去 |                          |

### 3. exec函数族的六个成员函数

1. execl
2. execv
3. execle
4. execve
5. execlp
6. execvp

> - 函数名对应其参数列表

> | l        | e                | v              | p            |
> | -------- | ---------------- | -------------- | ------------ |
> | 列表传递 | 字符指针数组传递 | 可指定环境变量 | 路径自动搜索 |



## 三 linux启动顺序

![607348-20151229231206354-919070678](..\picture\面试题\linuxstart.png)



## 四 vfs（virtual file system）

- 这是Linux文件系统对外的接口。linux支持十几个文件系统，通过vfs，调用者可以不用关心各个文件系统的底层实现。

## 五 inode

> 参考资料
>
> - [Linux的inode的理解](https://www.cnblogs.com/itech/archive/2012/05/15/2502284.html)

### inode的内容

inode包含文件的元信息，具体来说有以下内容：

1. 文件的字节数
2. 文件拥有者的User ID
3. 文件的Group ID
4. 文件的读、写、执行权限
5. 文件的时间戳，共有三个：ctime指inode上一次变动的时间，mtime指文件内容上一次变动的时间，atime指文件上一次打开的时间。
6. 链接数，即有多少文件名指向这个inode
7. 文件数据block的位置



## 六 linux硬盘命名规则

### 串口硬盘

- 包括：
  - SCSI设备（Small Computer System Interface）
  - SATA设备 （Serial Advanced Technology Attachment）

- 命名方式：
  - sda	sdb	...

### 硬盘

- 包括：

  - IDE（Integrated Drive Electronics）

- 命名方式：

  - hda	hdb ...


## 七 linux开机顺序

1. BIOS引导 (Basic Input Output System)
2. 读取MBR (Master Boot Record)
3. Boot Loader
4. 加载内核
5. 设定运行等级
6. init进程执行rc.sysinit
7. 启动内核模块
8. 执行不同运行级别的脚本程序
9. 执行/etc/rc.d/rc.local
10. 执行/bin/login程序，进入登录状态

> 拓展阅读
>
> - [Linux启动过程（开机启动顺序）](https://blog.csdn.net/wangzhen209/article/details/72377317)



## 八 linux中的命令

服务器发包常用命令

ps -ef | grep tomcat
kill -9 ${pid}

tomcat path: /usr/local/apache-tomcat-8.5.34/

./bin/startup.sh

tail -f logs/catalina.out      根据文件描述符进行追踪，当文件改名或被删除，追踪停止。ctr+c 停止追踪

rz / sz linux系统接收文件、发送文件

### ps -ef |grep 

-   ps 显示当前进程 (process) 的状态。
-   -e 显示所有进程。
-   -f 全格式。
-   |是管道命令 是指ps命令与grep同时执行

>    参考资料
>
>    -   [linux命令 ps -ef 的含义](https://blog.csdn.net/qq_15037231/article/details/79753735)
>    -   [ps -ef|grep详解](https://www.cnblogs.com/freinds/p/8074651.html)



### pwd

-   print working directory
-   获取目前所在的工作目录的绝对路径

### 日期相关：

1.  date -r 查看当前服务器时间

2.  date -s 设置时间和日期

例如：将系统日期设定成2009年11月3日的命令

命令 ： "date -s 11/03/2009"

将系统时间设定成下午5点55分55秒的命令

命令 ： "date -s 17:55:55"





### ./	需要有执行权限

sh/bash 不需要执行权限

打开一个subshell去读取、执行.sh 文件

>   参考资料
>
>   -   [linux里source、sh、bash、./有什么区别](https://www.cnblogs.com/pcat/p/5467188.html)

>   扩展
>
>   -   cource命令 在**当前shell内**去读取、执行a.sh，而a.sh不需要有"**执行权限**"


etc/profile 修改环境变量，改完后source编译生
## [linux下删除文件夹的命令](https://www.cnblogs.com/winifred-tang94/p/5863722.html)

使用rm -rf 目录名字 命令即可

-r 就是向下递归，不管有多少级目录，一并删除
-f 就是直接强行删除，不作任何提示的意思

eg

删除文件夹实例：rm -rf /var/log/httpd/access
将会删除/var/log/httpd/access目录以及其下所有文件、文件夹

删除文件使用实例：rm -f /var/log/httpd/access.log
将会强制删除/var/log/httpd/access.log这个文件



yum 安装

rz、sz

yum install -y lrzsz



**一、ll命令**

ll并不是linux下一个基本的命令，它实际上是ls -l的一个别名。

Ubuntu默认不支持命令ll，必须用 ls -l，这样使用起来不是很方便。

如果要使用此命令，可以作如下修改：
打开 ~/.bashrc
找到 #alias ll=’ls -l’，去掉前面的#就可以了。（关闭原来的终端才能使命令生效）
这样个人用户可以使用ll命令，当切换成超级用户后，使用ll命令时提示找不到命令，那是因为你只是修改了个人用户的配置，所以，切换成root后做相同的操作即可解决问题。
启示：我们可以通过修改~/.bashrc添加任何其他的命令别名。



 第一个字母表示文件类型,

​        ”-”,普通文件.

​        ”d”目录,字母”d”,是dirtectory(目录)的缩写.

​        “l”符号链接。请注意,一个目录或者说一个文件夹是一个特殊文件,这个特殊文件存放的是其他文件和文件夹的相关信息.

​        “b”块设备文件。

​        “c”字符设备文件。

https://www.cnblogs.com/kongzhongqijing/p/3488884.html0



1) ls -lt  时间最近的在前面

2) ls -ltr 时间从前到后

3) 利用sort

​    ls -l | sort +7 (日期为第8列)   时间从前到后

​    ls -l | sort -r +7      时间最近的在前面





## 九 shell编程

-eq           //等于

-ne           //不等于

-gt            //大于

-lt            //小于

-ge            //大于等于

-le            //小于等于



${变量}	引用变量值

\#	求长度