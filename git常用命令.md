
# git 常见命令

### 配置用户名和邮箱

> git config --global user.name "Your Name" 
>
> git config --global user.email "email@example.com"

### 初始化

>git init

### 将工作区(Workspace)文件添加到暂存区(Stage)

>git add filename

### 将缓存区文件添加到本地仓库(Repository)

>git commit -m "some info"

### 查看文件状态

>git status

### 比较不同

* 比较工作区和暂存区区别

    >git diff ***filename*** 

* 比较暂存区和本地仓库别
    >git diff --cached ***filename***
  
* 比较工作区和本地最新版本区别
    >git diff HEAD  ***filename***

* 比较工作区和指定commit-id 区别
    >git diff ***commit-id*** ***filename***

* 比较暂存区和指定commit-id 区别
    >git diff --cache ***commit-id*** ***filename***

### 查看提交记录

* 查看提交记录
    >git log

* 查看提交记录(包含撤销的记录)
    >git relog

* 已精简模式显示提交记录
    >git --oneline 

* 以图形模式显示提交记录
    >git log --graph

* 显示某个作者的日志
    >git log --author = ***name***

### 版本回退

* 回退到上一次提交的版本
    >git reset --hard HEAD^

* 回退到指定commit-id版本
    >git reset --hard ***commit-id***

* 回退到上两次提交的版本
    >git reset --head HEAD^^
    >
    >git reste --head HEAD~2

* --hard 和 --soft 区别：
    >--head 彻底回退到某个版本，本地的源码也会变为上一个版本的内容，撤销的commit中所包含的更改被冲掉
    >
    >--soft 回退到某个版本，只回退了commit的信息，不会恢复到stage一级。如果还要提交，直接commit即可

### 丢弃工作区修改

>git checkout --***filename***  *不要遗漏--，否则就变成切换到每一个分支*

>将文件在工作区的修改全部撤销，这里有两种情况：
>
>一种是文件自修改后还没有被放到暂存区，现在，撤销修改就回到和版本库一模一样的状态；
>
>一种是文件已经添加到暂存区后，又作了修改，现在，撤销修改就回到添加到暂存区后的状态。
>
>总之，就是让这个文件回到最近一次git commit或git add时的状态。

### 把暂存区修改撤销掉(unstage) 重新放回工作区

>git reset HEAD ***filename***

>执行此命令后 暂存区修改被撤销 但工作区修改并没有被撤销 要想撤销工作区修改 执行 git checkout --***filename***

### 删除版本库文件

>git rm ***filename***

1. 并提交到本地仓库
>git commmit -m ***someinfo***

2. 撤销删除
>git checkout -- ***filename***

### 关联远程仓库

>git remote add origin ***remote repository path*** 

### 第一次推送分支

>git push -u ***远程仓库名(一般为origin)*** ***要推送的分支名***
>
>-u参数: git不但会把本地的master分支内容推送的远程新的master分支，还会把本地的master分支和远程的master分支关联起来，在以后的推送或者拉取时可以省略-u

### 克隆远程仓库到本地

>git clone ***仓库地址***

### git clone ***仓库地址*** 只能看到本地的 master 分支, 要想在别的分支上提交修改 需要使用

>git checkout -b ***分支名***  origin/***分支名***

### 如果在使用git pull提示no tracking information，则说明本地分支和远程分支的链接关系没有创建 

>git branch --set-upstream-to ***分支名*** origin/***分支名***
###　抓取远程分支到本地

>git pull

### 查看分支

>git branch

### 创建分支

>git branch ***分支名***

### 切换分支

>git checkout ***分支名***

### 创建并切换分支

>git checkout -b ***分支名***


### 合并某个分支到当前分支

>git merge ***分支名***

### 删除分支

>git branch -d ***删除分支名***

### 删除没有被合并的分支

>git branch -D ***要删除分支名***

### 查看远程库信息

>git remote

### 查看远程库详细信息

>git remote -v 