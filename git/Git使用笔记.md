[转自jiangydev](https://github.com/jiangydev/devdocmark)

## Git 分布式版本控制系统

### 一、Git 介绍
#### 1. 集中式与分布式
* 集中式版本控制系统: 版本库是集中存放在中央服务器, 必须联网（或局域网）才能工作;
> 如：SVN、CVS、ClearCase和VSS等。

* 分布式版本控制系统: 每个协作者本地都有一个完整的版本库;
> 如：BitKeeper、Mercurial和Bazaar等。

### 二、Git 安装
* Linux: 安装命令`sudo apt-get install git`;
* MacOS X: 通过 [homebrew](https://brew.sh/) 或 Xcode 安装;
* Windows: [MSysGit](https://git-for-windows.github.io) - Windows版Git;

```shell
# 设置用户名及邮箱：
$ git config --global user.name "Your Name"
$ git config --global user.email "email@example.com"
```

### 三、创建版本库 (Repository)
> 1. 一个由Git管理的目录文件，其中每个文件的创建、修改、删除，Git都可以跟踪，以便追踪历史，或回退到过去某一版本。
> 2. 工作区和暂存区概念
>> * 目录 = 工作区 + 版本库(.git)
>> * 版本库 = 暂存区 + 分支
>> * `git commit`只将暂存区(`git add`而来)的内容commit.

#### 1. 创建版本库目录
```shell
$ mkdir devdocmark
```

#### 2. 初始化版本库
```shell
# 使当前目录初始化为Git可以管理的仓库
$ git init
```

> 注意点：
版本控制系统，其实只能跟踪文本文件的改动，比如TXT文件，网页，所有的程序代码等等；图片、视频（包括 Word）这些二进制文件，虽然也能由版本控制系统管理，但没法跟踪文件的内容变化。

#### 3. 把文件添加到暂存区
```shell
# 添加指定文件
$ git add <file>
# 添加当前目录下所有发生变动的文件
$ git add .
```

#### 4. 把文件提交到当前分支
```shell
# 提交暂存区文件到当前分支
$ git commit -m "提交文件的注释"
```

### 四、版本控制
#### 1. 常用命令
```shell
# 查看版本库当前状态，显示未add和未commit的文件
$ git status
# 查看文件内容的变动详情，显示的格式正是Unix通用的diff格式
$ git diff
# 显示从最近到最远的提交日志，如果输出信息太多，可以加上`--pretty=oneline`参数,使每次提交只有一行的信息
$ git log
```

#### 2. 版本回退
> 在Git中，HEAD 表示当前版本，上一个版本为 `HEAD^`，上上一个版本为 `HEAD^^`，上100个版本可以写成 `HEAD~100`

```shell
# 回退到上一个版本, 使用HEAD指针
$ git reset --hard HEAD^
# 回退到上一个版本, 使用commit-id
$ git reset --hard <commit-id>
# 查看命令历史，可以看到之前所在的commit-id
$ git reflog
```

#### 3. 撤销修改或删除
```shell
# 把file文件在工作区的修改全部撤销
$ git checkout -- <file>
```
> 两种情况：
1. file修改（删除）后还没有被添加到暂存区，撤销修改后回到和版本库一致的状态;
2. file已经添加到暂存区后，又作了修改，现在撤销修改就回到添加到暂存区后的状态。
*注：即文件回到最近一次 `git commit`或 `git add`时的状态;
    命令中的 `--` 很重要，若没有--，就变成“切换到另一个分支”的命令*

#### 4. 删除文件
```shell
# 从版本库中删除该文件
$ git rm <file>
```

### 五、远程版本库
#### 1. 关联远程库
> 若本地有项目，在 GitHub 或其他代码仓库需要新建项目版本库则使用关联方法。

```shell
# 关联远程库(git ssh协议,也可以使用 https 协议)
$ git remote add origin git@github.com:jiangydev/devdocmark.git
# 推送当前分支到远程(origin)的 master 分支
$ git push -u origin master
# 拉取远程(origin)的 master 分支到本地
$ git pull origin master

# 建立本地分支和远程分支的关联
$ git branch --set-upstream <branch-name> origin/<branch-name>
```
> * `origin`是Git默认的远程库名称，可以修改名称，`git remote`命令可以查看远程库名称；
> * 远程库为空、本地第一次推送，使用`-u`参数，Git不仅会把本地的当前分支内容推送到远程新的对应分支，还会把本地分支和远程分支关联起来；使用`-f`参数，强制推送分支内容；在以后的推送或者拉取时可以不加参数。

#### 2. 克隆远程库
> 若在 GitHub 或其他代码仓库已有项目版本库的情况下可以使用克隆方法。

```shell
# 克隆远程库(git ssh协议,也可以使用 https 协议)
$ git clone git@github.com:jiangydev/devdocmark.git
```

### 六、分支管理
#### 1. 新建、切换、查看、合并、删除分支
```shell
# 新建 dev分支，并切换到 dev
$ git checkout -b dev
# 新建 dev分支
$ git branch dev

# 切换到 dev分支
$ git checkout dev

# 查看当前所在的分支和所有分支
$ git branch

# 合并 dev分支到当前分支
$ git merge dev

# 删除 dev分支
$ git branch -d dev
```

#### 2. 冲突解决
> * `git merge <name>`合并分支时(默认 Fast forward 模式)，会提示冲突内容；
> * 使用`--no-ff`参数禁用Fast forward模式;

```shell
# git log也可以看到分支的合并情况
$ git log --graph --pretty=oneline --abbrev-commit

# 使用普通模式合并 dev分支
$ git merge --no-ff -m "merge dev with no-ff" dev
```

#### 3. 现场暂存
> 暂存当前工作区后，工作区是 clean的，此时可以进行其他的修改。

```shell
# 暂存当前工作区
$ git stash
# 查看stash内容
$ git stash list

# 恢复现场
$ git stash apply
# 删除stash
$ git stash drop

# 恢复现场并删除stash
$ git stash pop
```

### 七、标签管理
#### 1. 创建、查看、删除标签
> 默认标签是打在最新提交的commit上, 可以根据 commit-id 打标签

```shell
# 创建新标签
$ git tag <tagname>
# 查看所有标签
$ git tag

# 在指定的 commit-id上打标签
$ git tag -a <tagname> -m "" <commit-id>
# 用私钥签名标签
$ git tag -s <tagname> -m "" <commit-id>

# 查看标签详细信息
$ git show <tagname>

# 删除标签
$ git tag -d <tagname>
```

#### 2. 远程标签
> * 创建的标签只存储在本地，不会自动推送到远程;
> * 删除远程标签前，先删除本地标签；

```shell
# 一次性推送全部尚未推送到远程的本地标签
$ git push origin --tags

# 删除远程标签
$ git push origin :refs/tags/<tagname>
```

