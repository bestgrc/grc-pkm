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

