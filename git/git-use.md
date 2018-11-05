# git 使用笔记

## 1. 常用命令

```shell
# 设置用户名及邮箱：
$ git config --global user.name "Your Name"
$ git config --global user.email "email@example.com"
```

```shell
# 添加指定文件到暂存区
$ git add <file>
# 添加当前目录下所有发生变动的文件
$ git add .
```

```shell
# 提交暂存区文件到当前分支
$ git commit -m "提交文件的注释"
```







## 第一次ssh连接github

```shell
# ssh连接命令
$ ssh -T git@github.com	

# 第一次连接都会这样，输入yes就好了
The authenticity of host 'github.com (192.30.253.113)' can't be established.
RSA key fingerprint is SHA256:nThbg6kXUpJWGl7E1IGOCspRomTxdCARLviKw6E5SY8.
Are you sure you want to continue connecting (yes/no)? 

yes

# 连接成功
Warning: Permanently added 'github.com,192.30.253.113' (RSA) to the list of known hosts.
Hi bestgrc! You've successfully authenticated, but GitHub does not provide shell access.

```



