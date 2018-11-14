# git 使用笔记

> 参考资料
>
> - [Git的原理简介和常用命令](https://www.cnblogs.com/yelbosh/p/7471979.html)

## 1. 基本操作

| 操作       | 命令                                          | 拓展         | 命令                    |
| ---------- | --------------------------------------------- | ------------ | ----------------------- |
| 设置用户名 | $ git config --global user.name "Your Name"   |              |                         |
| 设置邮箱   | $ git config --global user.email "Your Email" |              |                         |
| 初始化     | $ git init                                    |              |                         |
| 克隆       | $ git clone                                   | 指定分支     | git clone -b 分支号 url |
| 获取       | $ git fetch origin master                     |              |                         |
| 变基       | $ git rebase origin master                    |              |                         |
| 合并       | $ git merge origin master                     |              |                         |
| 拉取       | $ git pull                                    |              |                         |
| 添加       | $ git add file                                | 添加全部变化 | .                       |
|            |                                               | 添加某文件   | 文件名                  |
| 提交       | $ git commit –m “提交信息”                    |              |                         |
| 推送       | $ git push origin master                      |              |                         |

> pull = fetch + merge
>
> 一般开发用 fetch +rebase 为主，分支整洁



## 2. 日志 差异 状态

| 操作 | 命令         | 拓展                 | 命令        |
| ---- | ------------ | -------------------- | ----------- |
| 日志 | $ git log    | 当前文件日记         | -p filename |
|      |              | 只显示一行           | --oneline   |
| 差异 | $ git diff   | 查看add后文件diff    | --staged    |
|      |              | 查看commit后文件diff | HEAD        |
|      |              | 只查看修改文件       | --stat      |
| 状态 | $ git status | 显示额外信息         | -s          |
|      |              |                      |             |



## 2. Git三种状态

1. 已修改 (modified)
   - 工作区修改了某个文件，但还没放到暂存区
2. 已暂存 (staged / cached)
   - 把已修改的文件放在暂存区，即下次提交时要提交的清单中
3. 已提交 (committed)
   - 该文件已经被安全地保存在本地版本库中了





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



## Git底层原理

- Git是一套内容寻址（content-addressable）文件系统

  记录的是文件的差异

- 采用HashTable的方式进行查找
  - key：文件（头+内容）的哈希值（采用sha-1的方式，40位）
  - value：经过压缩后的文件内容
- 应用层 porcelain命令/底层 plumbing命令
- git对象类型
  - BLOB对象
  - tree对象
  - commit对象





