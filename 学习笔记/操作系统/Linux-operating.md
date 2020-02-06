# 一 linux中的命令

| 功能                             | 命令                                                  | 详解                                                         |
| -------------------------------- | ----------------------------------------------------- | ------------------------------------------------------------ |
| 查看进程                         | ps -ef grep                                           | ps 显示当前进程 (process) 的状态。<br>-e 显示所有进程。<br>-f 全格式。<br> \|是管道命令 是指ps命令与grep同时执行<br> 参考资料:<br>  [linux命令 ps -ef 的含义](https://blog.csdn.net/qq_15037231/article/details/79753735) [ps -ef\|grep详解](https://www.cnblogs.com/freinds/p/8074651.html) |
| 杀进程                           | kill -9 ${pid}                                        | -9 强制执行                                                  |
| 查看文件                         | tail -f logs/catalina.out                             |                                                              |
| 接收文件、发送文件               | rz / sz                                               | yum 安装:yum install -y lrzsz                                |
| 以系统管理者身份执行指令         | sudo                                                  |                                                              |
| 查看当前内存使用                 | free -h  <br>top(详细信息)                            | Men 物理内存<br>Swap 虚拟内存                                |
| 获取目前所在的工作目录的绝对路径 | pwd                                                   | print working directory                                      |
| 日期相关                         | date -r 查看当前服务器时间 <br>date -s 设置时间和日期 | 例如：将系统日期设定成2009年11月3日的命令<br>命令 ： "date -s 11/03/2009"<br>将系统时间设定成下午5点55分55秒的命令<br>命令 ： "date -s 17:55:55" |
| 删除文件夹                       | rm -rf                                                | r 就是向下递归，不管有多少级目录，一并删除<br/>-f 就是直接强行删除，不作任何提示的意思<br>参考资料<br>[linux下删除文件夹的命令](https://www.cnblogs.com/winifred-tang94/p/5863722.html) |
| 寻找文件及目录                   | find -name "\*name\*"                                 |                                                              |
|                                  |                                                       |                                                              |
|                                  |                                                       |                                                              |



# 二 使用./与sh运行bash脚本

./	需要有执行权限

sh/bash 不需要执行权限

打开一个subshell去读取、执行.sh 文件

> 参考资料
>
> - [linux里source、sh、bash、./有什么区别](https://www.cnblogs.com/pcat/p/5467188.html)

> 扩展
>
> - cource命令 在**当前shell内**去读取、执行a.sh，而a.sh不需要有"**执行权限**"



etc/profile 修改环境变量，改完后source编译下



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



# 三 shell编程

-eq           //等于

-ne           //不等于

-gt            //大于

-lt            //小于

-ge            //大于等于

-le            //小于等于

${变量}	引用变量值

\#	求长度

# 四 jar包启动脚本

## 函件

```bash
#!/bin/sh
# 获取jar包的完整名称
# $() 执行命令
article=$(ls lettersystem*.jar)
echo $article
# nohup 后台运行
# --server.port 设置端口（和配置文件相同，但这里优先级更高）
# >letter.out 输出到这个文件
# 2>&1 错误输出流 输出到 正常输出流中 
# & 后台运行
nohup java -jar $article --server.port=8086 >letter.out 2>&1 & 
# &！ 最后执行的后台程序的pid
echo $!>letter.pid 
# -fn 动态显示日志
echo "LetterSystem start...."&&tail -fn 300 letter.out
```

## 查询

```bash
#!/bin/sh
## java env
export JAVA_HOME=/usr/java/jdk1.8.0_11
export JRE_HOME=$JAVA_HOME/jre

API_NAME=xxcx
JAR_NAME=$API_NAME\.jar
#PID  代表是PID文件
PID=$API_NAME\.pid

#使用说明，用来提示输入参数
usage() {
	echo -e "================会不会用啊,  你是不是蠢, 用下面的格式↓↓↓↓↓↓↓=======================\n"
 	echo -e "         >>>  Usage: sh 执行脚本.sh [start|stop|restart|status]  <<<"
    	echo -e "\n==================================================================================="
	exit 1
}

#检查程序是否在运行
is_exist(){
# 反引号内一般放的是bash的命令，返回命令运行结果
# grep -v 不包括
# awk '{print $2}'意为取第二个字段输出，在这里就是“grep”
  pid=`ps -ef|grep $JAR_NAME|grep -v grep|awk '{print $2}' `
  #如果不存在返回1，存在返回0     
  #-z string ,string长度为0则为真
  if [ -z "${pid}" ]; then
   return 1
  else
    return 0
  fi
}

#启动方法
start(){
  is_exist
  # $? 上个命令的退出状态，或函数的返回值。
  if [ $? -eq "0" ]; then 
    echo ">>> ${JAR_NAME} is already running PID=${pid} <<<" 
  else 
    nohup $JRE_HOME/bin/java -Xms256m -Xmx512m -jar $JAR_NAME >start.log 2>&1 &
    echo $! > $PID
    echo ">>> start $JAR_NAME successed PID=$! <<<" 
   fi
  }

#停止方法
stop(){
  #is_exist
  pidf=$(cat $PID)
  #echo "$pidf"  
  echo ">>> ${JAR_NAME} PID = $pidf begin kill $pidf <<<"
  kill $pidf
  rm -rf $PID
  sleep 2
  is_exist
  if [ $? -eq "0" ]; then 
    echo ">>> 哎呦, 竟然没杀掉, 挺顽强啊小包 <<<"
	echo ">>>  ${JAR_NAME} PID = $pid begin kill -9 $pid <<<"
    kill -9  $pid
    sleep 2
    echo ">>> $JAR_NAME process stopped <<<"  
  else
    echo ">>> ${JAR_NAME} is not running <<<"
  fi  
}

#输出运行状态
status(){
  is_exist
  if [ $? -eq "0" ]; then
    echo ">>> ${JAR_NAME} is running PID is ${pid} <<<"
  else
    echo ">>> ${JAR_NAME} is not running <<<"
  fi
}

#重启
restart(){
  stop
  start
}

#根据输入参数，选择执行对应方法，不输入则执行使用说明
case "$1" in
  "start")
    start
    ;;
  "stop")
    stop
    ;;
  "status")
    status
    ;;
  "restart")
    restart
    ;;
  *)
    usage
    ;;
esac
exit 0

```



### 参考资料

[bash中 2>&1 & 的解释](https://www.cnblogs.com/sos-blue/p/6798810.html)

[bash中` ` |' '| " "的区别](https://blog.csdn.net/qq_36041534/article/details/80233413)

[shell学习笔记（3）grep -v grep|awk '{print $2}' ` 表示是什么意思](https://blog.csdn.net/shGray/article/details/101350925)

[linux bash Shell特殊变量：Shell $0, $#, $*, $@, $?, $$和命令行参数](

