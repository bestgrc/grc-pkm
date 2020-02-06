[转自jiangydev](https://github.com/jiangydev/devdocmark)

## Git 工具使用解决方案

#### 1. 验证SSH登录
```shell
$ ssh -T git@github.com
# 返回以下内容则连接正确
"Hi jiangydev! You\'ve successfully authenticated, but GitHub does not provide shell access."
```

#### 2. Git 进程启用
```shell
$ eval "$(ssh-agent -s)"
```

#### 3. SSH密钥文件找不到
```shell
# 查看密钥文件
$ ssh-add -l
"The agent has no identities."

# 添加密钥文件
$ ssh-add /c/Users/(your)/.ssh/id_rsa
Enter passphrase for /c/Users/(your)/.ssh/id_rsa:
"Identity added: /c/Users/(your)/.ssh/id_rsa (/c/Users/(your)/.ssh/id_rsa)"
```

#### 4. Windows下git status中文乱码
```shell
$ git status
"On branch master
Untracked files:
  (use \"git add <file>...\" to include ...)

        \"\346\225\260\...\350\214\203.md\"

nothing added to commit but untracked ..."
# 解决方案
$ git config --global core.quotepath false
```

#### 5. 创建新ssh密钥

```shell
$ ssh-keygen -t rsa -C "注册Github用的邮箱"  
```

一路回车，会在默认位置创建ssh密钥



#### github下载速度过慢

1. 修改dns

参考资料：<https://www.jianshu.com/p/3f6477049ece>

2. 使用gitee fork github中项目，然后再从gitee进项clone。

