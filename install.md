# 常用插件安装URL

## 编码规范

[checkstyle](http://eclipse-cs.sourceforge.net/update )

> 最新版本在myeclipse2017上有问题，无法启动。
>
> 解释都是英文的，用起来不大舒服，要去查

[阿里p3c](<https://p3c.alibaba.com/plugin/eclipse/update>)

> 中文信息，比较友好



## 查找bug

[findbugs](http://findbugs.cs.umd.edu/eclipse)



# 在阿里云服务器上安装redis

-   参考资料
    -   [redis 从0搭建---一次在阿里云上的redis安装](https://blog.csdn.net/qq_41376740/article/details/81007226)
    -   [Redis need tcl 8.5 or newer](https://blog.csdn.net/luyee2010/article/details/18766911)

## 操作步骤

```bash
cd /usr/local/					//1.切换到安装目录

wget http://download.redis.io/releases/redis-4.0.10.tar.gz 
								//2.wget：下载文件的工具
								
tar -xvzf redis-4.0.10.tar.gz 	//3.tar:解压
                                    //x:解压
                                    //v:显示过程
                                    //z:先解压gzip格式的压缩文件（不必须）
                                    //f:使用文件
								
make							//4.编译

make test						//5.测试编译结果

cd src/
./redis-server 					//启动服务
```

### 出现问题：

-   make test时 报tcl版本不够高

>   tcl:一种脚本语言

-   报错：You need tcl 8.5 or newer in order to run the Redis test

### 解决方案：

```shell
wget http://downloads.sourceforge.net/tcl/tcl8.6.1-src.tar.gzsudo 

tar xzvf tcl8.6.1-src.tar.gz  -C /usr/local/   //-c:解压到的目录
cd  /usr/local/tcl8.6.1/unix/
sudo ./configure							//sudo是linux系统管理指令
sudo make
sudo make install 
```





