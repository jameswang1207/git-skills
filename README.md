# Git相关--------https://git-scm.com/book/zh/v2

## 写在前面

1. Git是什么？
    - 分布式版本控制系统。

    - 那什么是版本控制系统
      - 版本控制透过文档控制（documentation control）记录程序各个模组的改动，并为每次改动编上序号。这种方法是工程图维护的标准做法， 它伴随着工程图从图的诞生一直到图的定型。一种简单的版本控制形式，例如，赋给图的初版一个版本等级“A”。当做了第一次改变后，版本等级改为“B”，以此类推等等。

2. Git的诞生
    - https://git-scm.com/book/zh/v2/%E8%B5%B7%E6%AD%A5-Git-%E7%AE%80%E5%8F%B2

3.集中式vs分布式

    - 集中式:

        1. 版本库是集中存放在中央服务器的，而干活的时候，用的都是自己的电脑，所以要先从中央服务器取得最新的版本，然后开始干活，干完活了，再把自己的活推送给中央服务器

        2. 集中式版本控制系统最大的毛病就是必须联网才能工作，如果在局域网内还好，带宽够大，速度够快，可如果在互联网上，遇到网速慢的话，可能提交一个10M的文件就需要5分钟,------->get code 非常困难时间太久。

    - 分布式：
    
        1. 首先，分布式版本控制系统根本没有“中央服务器”，每个人的电脑上都是一个完整的版本库，这样，你工作的时候，就不需要联网了，因为版本库就在你自己的电脑上。既然每个人电脑上都有一个完整的版本库，那多个人如何协作呢？比方说你在自己电脑上改了文件A，你的同事也在他的电脑上改了文件A，这时，你们俩之间只需把各自的修改推送给对方，就可以互相看到对方的修改了。---------->不会你这样做。

4.Git的安装
    - https://git-scm.com/download/win
    - 安装完成后，进行配置
    ```sh
        git config --global user.name "Your Name"
        git config --global user.email "email@example.com"
    ```
    - 因为Git是分布式版本控制系统，所以，每个机器都必须自报家门

5.创建版本库-----> 提交到本地版本库
    - 初始化一个Git仓库，使用git init命令。
    - 使用命令git add <file>，注意，可反复多次使用，添加多个文件；
    - 使用命令git commit，完成


6. 时光机穿梭
    - 使用git status命令。
    - 如果git status告诉你有文件被修改过，用git diff可以查看修改内容。
    - Git的版本回退速度非常快，因为Git在内部有个指向当前版本的HEAD指针-----commit-id
    - HEAD指向的版本就是当前版本，因此，Git允许我们在版本的历史之间穿梭，使用命令git reset --hard commit_id.穿梭前,用gitlog可以查看提交历史，以便确定要回退到哪个版本。
    - 要重返未来，用git reflog查看命令历史，以便确定要回到未来的哪个版本。
    - 工作区和暂存区
       1.


3. 统一概念：
	- 工作区：改动（增删文件和内容）
	- 暂存区：输入命令：`git add 改动的文件名`，此次改动就放到了‘暂存区’
	- 本地仓库(简称：本地)：输入命令：`git commit 此次修改的描述`，此次改动就放到了’本地仓库’，每个commit，我叫它为一个‘版本’。
	- 远程仓库(简称：远程)：输入命令：`git push 远程仓库`，此次改动就放到了‘远程仓库’（GitHub等)
	- commit-id：输出命令：`git log`，最上面那行`commit xxxxxx`，后面的字符串就是commit-id

4.对象：Git用户，还有的高深的命令，等用到再google。

## 目录
* [展示帮助信息](#展示帮助信息)
* [回到远程仓库的状态](#回到远程仓库的状态)
* [重设第一个commit](#重设第一个commit)
* [展示工作区和暂存区的不同](#展示工作区和暂存区的不同)
* [展示暂存区和最近版本的不同](#展示暂存区和最近版本的不同)
* [展示暂存区、工作区和最近版本的不同](#展示暂存区工作区和最近版本的不同)
* [快速切换分支](#快速切换分支)
* [删除已经合并到master的分支](#删除已经合并到master的分支)
* [展示本地分支关联远程仓库的情况](#展示本地分支关联远程仓库的情况)
* [关联远程分支](#关联远程分支)
* [列出所有远程分支](#列出所有远程分支)
* [列出本地和远程分支](#列出本地和远程分支)
* [创建并切换到本地分支](#创建并切换到本地分支)
* [创建并切换到远程分支](#创建并切换到远程分支)
* [删除本地分支](#删除本地分支)
* [删除远程分支](#删除远程分支)
* [重命名本地分支](#重命名本地分支)
* [查看标签](#查看标签)
* [本地创建标签](#本地创建标签)
* [推送标签到远程仓库](#推送标签到远程仓库)
* [删除本地标签](#删除本地标签)
* [删除远程标签](#删除远程标签)
* [切回到某个标签](#切回到某个标签)
* [放弃工作区的修改](#放弃工作区的修改)
* [回到某一个commit的状态，并重新增添一个commit](#回到某一个commit的状态并重新增添一个commit)
* [回到某个commit的状态，并删除后面的commit](#回到某个commit的状态并删除后面的commit)
* [修改上一个commit的描述](#修改上一个commit的描述)
* [查看commit历史](#查看commit历史)
* [显示本地执行过git命令](#显示本地执行过git命令)
* [修改作者名](#修改作者名)
* [修改远程仓库的url](#修改远程仓库的url)
* [增加远程仓库](#增加远程仓库)
* [列出所有远程仓库](#列出所有远程仓库)
* [查看两个星期内的改动](#查看两个星期内的改动)
* [把A分支的某一个commit，放到B分支上](#把A分支的某一个commit放到B分支上)
* [给git命令起别名](#给git命令起别名)
* [存储当前的修改，但不用提交commit](#存储当前的修改但不用提交commit)
* [保存当前状态，包括untracked的文件](#保存当前状态包括untracked的文件)
* [展示所有stashes](#展示所有stashes)
* [回到某个stash的状态](#回到某个stash的状态)
* [回到最后一个stash的状态，并删除这个stash](#回到最后一个stash的状态并删除这个stash)
* [删除所有的stash](#删除所有的stash)
* [从stash中拿出某个文件的修改](#从stash中拿出某个文件的修改)
* [展示所有tracked的文件](#展示所有tracked的文件)
* [展示所有untracked的文件](#展示所有untracked的文件)
* [展示所有忽略的文件](#展示所有忽略的文件)
* [强制删除untracked的文件](#强制删除untracked的文件)
* [强制删除untracked的目录](#强制删除untracked的目录)
* [展示简化的commit历史](#展示简化的commit历史)
* [查看某段代码是谁写的](#查看某段代码是谁写的)
* [把某一个分支到导出成一个文件](#把某一个分支到导出成一个文件)
* [从包中导入分支](#从包中导入分支)
* [执行rebase之前自动stash](#执行rebase之前自动stash)
* [从远程仓库根据ID，拉下某一状态，到本地分支](#从远程仓库根据ID拉下某一状态-到本地分支)
* [详细展示一行中的修改](#详细展示一行中的修改)
* [清除`.gitignore`文件中记录的文件](#清除gitignore文件中记录的文件)
* [展示所有alias和configs](#展示所有alias和configs)
* [展示忽略的文件](#展示忽略的文件)
* [commit历史中显示Branch1有的，但是Branch2没有commit](#commit历史中显示Branch1有的但是Branch2没有commit)
* [在commit log中显示GPG签名](#在commit-log中显示GPG签名)
* [删除全局设置](#删除全局设置)
* [新建并切换到新分支上，同时这个分支没有任何commit](#新建并切换到新分支上同时这个分支没有任何commit)
* [展示任意分支某一文件的内容](#展示任意分支某一文件的内容)
* [clone下来指定的单一分支](#clone下来指定的单一分支)
* [忽略某个文件的改动](#忽略某个文件的改动)
* [忽略文件的权限变化](#忽略文件的权限变化)
* [展示本地所有的分支的commit](#展示本地所有的分支的commit)
* [在commit log中查找相关内容](#在commit-log中查找相关内容)
* [把暂存区的指定file放到工作区中](#把暂存区的指定file放到工作区中)
* [强制推送](#强制推送)
* [联系我](#联系我)

## 展示帮助信息
```sh
git help -g
```

## 回到远程仓库的状态
抛弃本地所有的修改，回到远程仓库的状态。  
```sh
git fetch --all && git reset --hard origin/master
```

## 重设第一个commit
也就是把所有的改动都重新放回工作区，并**清空所有的commit**，这样就可以重新提交第一个commit了
```sh
git update-ref -d HEAD
```

## 展示工作区和暂存区的不同
输出**工作区**和**暂存区**的different(不同)。
```sh
git diff
```

还可以展示本地仓库中任意两个commit之间的文件变动：
```sh
git diff <commit-id> <commit-id>
```

## 展示暂存区和最近版本的不同
输出**暂存区**和本地最近的版本(commit)的different(不同)。
```sh
git diff --cached
```

## 展示暂存区、工作区和最近版本的不同
输出**工作区**、**暂存区** 和本地最近的版本(commit)的different(不同)。
```sh
git diff HEAD
```

## 快速切换分支
```sh
git checkout -
```

## 删除已经合并到master的分支
```sh
git branch --merged master | grep -v '^\*\|  master' | xargs -n 1 git branch -d
```

## 展示本地分支关联远程仓库的情况
```sh
git branch -vv
```

## 关联远程分支
关联之后，`git branch -vv`就可以展示关联的远程分支名了，同时推送到远程仓库直接：`git push`，不需要指定远程仓库了。
```sh
git branch -u origin/mybranch
```

或者在push时加上`-u`参数
```sh
git push origin/mybranch -u
```

## 列出所有远程分支
-r参数相当于：remote
```sh
git branch -r
```

## 列出本地和远程分支
-a参数相当于：all
```sh
git branch -a
```

## 创建并切换到本地分支
```sh
git checkout -b <branch-name>
```

## 创建并切换到远程分支
```sh
git checkout -b <branch-name> origin/<branch-name>
```

## 删除本地分支
```sh
git branch -d <local-branchname>
```

## 删除远程分支
```sh
git push origin --delete <remote-branchname>
```

或者  
```sh
git push origin :<remote-branchname>
```

## 重命名本地分支
```sh
git branch -m <new-branch-name>
```

## 查看标签
```
git tag
```

展示当前分支的最近的tag
```sh
git describe --tags --abbrev=0
```

## 本地创建标签
```sh
git tag <version-number>
```

默认tag是打在最近的一次commit上，如果需要指定commit打tag：
```sh
$ git tag -a <version-number> -m "v1.0 发布(描述)" <commit-id>
```

## 推送标签到远程仓库
首先要保证本地创建好了标签才可以推送标签到远程仓库：
```sh
git push origin <local-version-number>
```

一次性推送所有标签，同步到远程仓库：
```
git push origin --tags
```

## 删除本地标签
```sh
git tag -d <tag-name>
```

## 删除远程标签
删除远程标签需要**先删除本地标签**，再执行下面的命令：
```sh
git push origin :refs/tags/<tag-name>
```

## 切回到某个标签
一般上线之前都会打tag，就是为了防止上线后出现问题，方便快速回退到上一版本。下面的命令是回到某一标签下的状态：
```sh
git checkout -b branch_name tag_name
```

## 放弃工作区的修改
```sh
git checkout <file-name>
```

放弃所有修改：  
```sh
git checkout .
```

## 回到某一个commit的状态，并重新增添一个commit
```sh
git revert <commit-id>
```

## 回到某个commit的状态，并删除后面的commit
和revert的区别：reset命令会抹去某个commit id之后的所有commit
```sh
git reset <commit-id>
```

## 修改上一个commit的描述
```sh
git commit --amend
```

## 查看commit历史
```sh
git log
```

## 查看某段代码是谁写的
blame的意思为‘责怪’，你懂的。
```sh
git blame <file-name>
```

## 显示本地执行过git命令
就像shell的history一样
```
git reflog
```

## 修改作者名
```sh
git commit --amend --author='Author Name <email@address.com>'
```

## 修改远程仓库的url
```sh
git remote set-url origin <URL>
```

## 增加远程仓库
```sh
git remote add origin <remote-url>
```

## 列出所有远程仓库
```sh
git remote
```

## 查看两个星期内的改动
```sh
git whatchanged --since='2 weeks ago'
```

## 把A分支的某一个commit，放到B分支上
这个过程需要`cherry-pick`命令，[参考](http://sg552.iteye.com/blog/1300713#bc2367928)
```sh
git checkout <branch-name> && git cherry-pick <commit-id>
```

## 给git命令起别名
简化命令

```sh
git config --global alias.<handle> <command>

比如：git status 改成 git st，这样可以简化命令

git config --global alias.st status
```

## 存储当前的修改，但不用提交commit
详解可以参考[廖雪峰老师的git教程](http://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/00137602359178794d966923e5c4134bc8bf98dfb03aea3000)
```sh
git stash
```

## 保存当前状态，包括untracked的文件
untracked文件：新建的文件
```sh
git stash -u
```

## 展示所有stashes
```sh
git stash list
```

## 回到某个stash的状态
```sh
git stash apply <stash@{n}>
```

## 回到最后一个stash的状态，并删除这个stash
```sh
git stash pop
```

## 删除所有的stash
```sh
git stash clear
```

## 从stash中拿出某个文件的修改
```sh
git checkout <stash@{n}> -- <file-path>
```

## 展示所有tracked的文件
```sh
git ls-files -t
```

## 展示所有untracked的文件
```sh
git ls-files --others
```

## 展示所有忽略的文件
```sh
git ls-files --others -i --exclude-standard
```

## 强制删除untracked的文件
可以用来删除新建的文件。如果不指定文件文件名，则清空所有工作的untracked文件。`clean`命令，**注意两点**：  
1. clean后，删除的文件无法找回
2. 不会影响tracked的文件的改动，只会删除untracked的文件

```sh
git clean <file-name> -f
```

## 强制删除untracked的目录
可以用来删除新建的目录，**注意**:这个命令也可以用来删除untracked的文件。详情见上一条

```sh
git clean <directory-name> -df
```

## 展示简化的commit历史
```sh
git log --pretty=oneline --graph --decorate --all
```

## 把某一个分支到导出成一个文件
```sh
git bundle create <file> <branch-name>
```

## 从包中导入分支
新建一个分支，分支内容就是上面`git bundle create`命令导出的内容
```sh
git clone repo.bundle <repo-dir> -b <branch-name>
```

## 执行rebase之前自动stash
```sh
git rebase --autostash
```

## 从远程仓库根据ID，拉下某一状态，到本地分支
```sh
git fetch origin pull/<id>/head:<branch-name>
```

## 详细展示一行中的修改
```sh
git diff --word-diff
```

## 清除gitignore文件中记录的文件
```sh
git clean -X -f
```

## 展示所有alias和configs
**注意：** config分为：当前目录（local）和全局（golbal）的config，默认为当前目录的config

```sh
git config --local --list (当前目录)
git config --global --list (全局)
```

## 展示忽略的文件
```sh
git status --ignored
```

## commit历史中显示Branch1有的，但是Branch2没有commit
```sh
git log Branch1 ^Branch2
```

## 在commit log中显示GPG签名
```sh
git log --show-signature
```

## 删除全局设置
```sh
git config --global --unset <entry-name>
```

## 新建并切换到新分支上，同时这个分支没有任何commit
相当于保存修改，但是重写commit历史  
```sh
git checkout --orphan <branch-name>
```

## 展示任意分支某一文件的内容
```sh
git show <branch-name>:<file-name>
```

## clone下来指定的单一分支
```sh
git clone -b <branch-name> --single-branch https://github.com/user/repo.git
```

## 忽略某个文件的改动
关闭 track 指定文件的改动，也就是 Git 将不会在记录这个文件的改动
```
git update-index --assume-unchanged path/to/file
```

恢复 track 指定文件的改动
```
git update-index --no-assume-unchanged path/to/file
```

## 忽略文件的权限变化
不再将文件的权限变化视作改动
```sh
git config core.fileMode false
```

## 展示本地所有的分支的commit
最新的放在最上面

```sh
git for-each-ref --sort=-committerdate --format='%(refname:short)' refs/heads/
```

## 在commit log中查找相关内容
通过grep查找，given-text：所需要查找的字段

```sh
git log --all --grep='<given-text>'
```

## 把暂存区的指定file放到工作区中
```sh
git reset <file-name>
```

## 强制推送
```sh
git push -f <remote-name> <branch-name>
```

