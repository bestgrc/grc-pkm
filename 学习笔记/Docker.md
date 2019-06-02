





## Docker使用中出现的问题：

| 问题描述                 | 问题原因 | 解决方案 | 备注                                                         |
| ------------------------ | -------- | -------- | ------------------------------------------------------------ |
| 容器状态显示:exited(137) | 内存不足 |          | [Linux 错误码列表](http://blog.chinaunix.net/uid-26111972-id-3400556.html) |
|                          |          |          |                                                              |



命令：

docker service start



进入容器

sudo docker exec -it pid /bin/bash 



## 安装参考

[使用Docker部署Gitlab](<https://www.cnblogs.com/int32bit/p/5310382.html>)