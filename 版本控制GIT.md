#### 1、版本控制

版本控制（Revision control）是一种在开发的过程中管理我们对文件、目录或工程等内容的修改历史，方便查看更改历史记录，备份以便恢复以前版本的软件工程技术。简单来说就是用于管理多人协同开发项目的技术。

#### 2、作用

 实现跨区域多人协同开发

 追踪和记载一个或者多个文件的历史记录

 组织和保护源代码和文档

 统计工作量

 并行开发、提高开发效率

 减轻开发人员的负担，节约时间，同时降低人为错误

没有进行版本控制或者版本控制本身缺乏正确的流程管理，在软件开发过程中将会引入很多问题，如软件代码的一致性、软件内容的冗余、软件过程的事务性、软件开发过程中的并发性、软件源代码的安全性、以及软件的整合等问题。

#### 3、版本控制工具

 **GIT**

 **SVN**(Subversion)

 **CVS**（Concurrent Versions System）

 **VSS**（Micorosoft Visual SourceSafe ）

 **TFS**（Team Foundation Server）

 Visual Studio Online

#### 4、Git与SVN最主要区别

**SVN是集中式版本控制系统**，版本库是集中**放在中央服务器上**的，而工作的时候，用的都是自己的电脑，所以首先要从中央服务器得到最新的版本，然后工作，完成工作后，需要把自己做完的工作推送到中央服务器。**集中式版本控制系统是必须联网才能工作**，对网络带宽要求较高。

**Git是分布式版本控制系统**。**没有中央服务器**，每个人的电脑就是一个完整的版本库，工作的时候就不需要联网了，因为版本都在自己的电脑上，协同的方法是这样的：比如说自己在电脑上改了文件A。这时，两人只需要把各自的修改推送给对方，就可以互相看到对方的修改了。Git可以直接看到了更新了哪些代码和文件

**Git是目前世界上最先进的分布式版本控制系统。**

#### 5、Git环境配置

**安装Git**

Git Bash：Unix与Linux风格的命令行。使用最多，推荐最多

Git CMD：Windows风格的命令行

GIT GUI：图形界面的Git。不建议初学者使用，尽量先熟悉常见命令

#### **Git配置**

git config -l 查看当前git配置

git config --system --list 查看系统配置

git config --global --list 查看当前用户配置

#### 6、GIT基本原理

Git本地有三个工作区域：工作目录（Working Directory）、暂存区（Stage/index）、资源库（Repository 或Git Directory）。如果再加上远程的git仓库（Remote Directory）就可以分为四个工作区域。



 在工作目录中添加、修改文件

 将需要进行版本管理的文件放入暂存区域 git add.

 将暂存区域的文件提交到git仓库 git commit

因此，git管理的文件有三种状态：已修改（modified），已暂存（staged），已提交（committed）

#### 7、GIT文件状态

版本控制就是对文件的版本控制，要对文件进行修改、提交等操作，首先要知道文件当前在什么状态，不然可能会提交了现在还不想提交的文件，或者要提交的文件没提交上。

 Untracked：未跟踪，此文件在文件夹中，但没有加入到git库，不参与版本控制，通过**git add .** 状态变为**Staged**

 Unmodify：文件已经入库，未修改，即版本库中的文件快照内容与文件夹中完全一致，这种类型的文件有两种去处，如果它被修改，而变为**Modified**，如果使用**git rm**移出版本库，则成为**Untracked**文件

 Modified：文件已修改，仅仅是修改，并没有进行其他的操作，这个文件也有两个去处，通过**git add .**可进入暂存**staged**状态，使用**git checkout** 则丢弃修改过，返回到**unmodify**状态，这个**git checkout**即从库中取出文件，覆盖当前修改

 Staged：暂存状态，执行**git commit**则将修改同步到库中，这是库中的文件和本地文件又变为一致，文件为**unmodify**状态，执行**git reset HEAD filename** 取消暂存，文件状态为**Modified**

```
查看文件状态
# 查看指定文件状态    git status 文件名
# 查看所有文件状态    git status
# 添加所有文件到暂存区    git add .
# 提交暂存区中的内容到本地仓库    git commit -m "消息内容"
            -m提交信息
```

#### 8、git具体命令

```
安装Git
在命令行输入 git 用来检测 Git 是否安装成功
git init 初始化 git 仓库
git add 提交到缓存区
		git add 1.txt 将1.txt提交到缓存区
git commit 提交到工作区
		git commit -m “first commit” commit 是提交的意思，-m 代表是提交信息，进行提交
git remote add origin git@github.com:heathhou/gitdemo.git
  	origin 在以后就可以代表 git@github.com:heathhou/gitdemo.git
git push origin master 提交到远程仓库
git status 查看状态
git reset xxx 回滚版本
    git reset —mixed xxx （默认）归档区 和 缓冲区
    git reset —hard xxx 归档区 缓冲区 和 工作区
    git reset —soft xxx 归档区
    xxx —> 操作所对应的哈希值
git log 查看所有产生的 commit 记录
git reflog 查看提交的操作
git revert xxx 撤销某次提交的操作
    xxx —> 操作所对应的哈希值
git branch 查看分支
    git branch -v （默认）查看有哪些分支
    git branch a 创建a分支
git checkout 切换分支
    git checkout a 切换到 a 分支上
    git checkout -b a 先新建再切换，未免有点麻烦，可以一步到位的
git merge xxx 合并分支
    git merge b1 将b1分支合并到当前分支
    xxx —> 某一分支
git branch -d 删除分支
git branch -D 强制删除分支
git tag 贴标签
git pull （将本地更新到远程仓库一致）拉取远程仓库最新的版本并将远端同名分支合并到本地分支
git fetch 获取远端的更新
git clone 仓库地址 （使用git clone指令下载仓库）
git clone -b 分支名 仓库地址 （使用git clone指令下载指定分支代码）
git push origin master （使用master分支进行提交）
```

