





## Docker使用中出现的问题：

| 问题描述                 | 问题原因 | 解决方案 | 备注                                                         |
| ------------------------ | -------- | -------- | ------------------------------------------------------------ |
| 容器状态显示:exited(137) | 内存不足 |          | [Linux 错误码列表](http://blog.chinaunix.net/uid-26111972-id-3400556.html) |
|                          |          |          |                                                              |



命令：

docker service start

docker search 寻找镜像

docker pull 拉取镜像





docker rm [CONTAINER ID] 删除容器



docker exec -it [pid] /bin/bash  进入容器



## 安装参考

[使用Docker部署Gitlab](<https://www.cnblogs.com/int32bit/p/5310382.html>)



<https://www.runoob.com/docker/docker-install-mysql.html>

docker 创建mysql容器

菜鸟命令：（多设置了文件挂载）

docker run -p 3306:3306 --name mymysql -v $PWD/conf:/etc/mysql/conf.d -v $PWD/logs:/logs -v $PWD/data:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=123456 -d mysql:latest



8.0以后的版本有密码加密方式的问题

我的 命令：

docker run -p 3306:3306 --name grcmysql -e MYSQL_ROOT_PASSWORD=Gurencai2012 -d mysql:5.6



