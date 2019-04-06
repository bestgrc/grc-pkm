# docker卡死

## 问题描述：

mysql的一个容器stop不了，反复stop，到后来docker的所有命令都无效了。

## 问题原因：

可能是某个命令池满了，而前面有命令卡住了？？？

- [参考原因](http://dockone.io/question/110)

## 解决方案：

重启docker  

- 命令：systemctl restart  docker

## 意外收获：

docker 重启后，运行中的容器也会随之重启，而且是否随之重启通过参数可以配置。

