**最近开始学习git这个版本控制系统，这个博客作为个人的git学习记录博客。**

个人是去廖雪峰的网站看git教程的。

@[TOC]

<hr/>

## git与集中式版本控制系统区别
git和集中式版本控制系统的**区别**大致有：
	1. 分布式管理，不在太过依赖中央服务器，没网也可以进行工作。
	2. 在集中式版本控制系统中的中央服务器如果误删除了你的git仓库，或者服务器故障，那么你存放的git代码也无法找回了，而分布式可以有多个副本，如果一个出现故障，可以去别的那里备份
	3. 分布式管理代码，效率会更高。
	4. git管理的是文件的修改，而集中式如svn管理的是文件
	*4. 等等，后续发现接着补充。。。*

由于是分布式管理，所以一个团队里不同的开发人员写好代码后可以互相推送，前提是要在同一个局域网下。如果不在同一个局域网下的话，git它是有一个类似“中央服务器”的电脑，可以拿它来中转，这里借用一下廖雪峰老师的图：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200311205026743.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0pva2Vyb25lZQ==,size_16,color_FFFFFF,t_70)
这样就可以完成团队间的协作了。

<hr/>

## git的内部结构:

**1. 工作区(Working DIrectory)**
 	工作区就是你当前git仓库所在的目录
 	![在这里插入图片描述](https://img-blog.csdnimg.cn/2020031217124978.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0pva2Vyb25lZQ==,size_16,color_FFFFFF,t_70)
 	我这里是git目录
**2. 版本库（Repository）**
 	工作区里面有一个隐藏的`.git`文件,这个就是Git的版本库
	Git的版本库里存了很多东西，其中最重要的就是称为`stage`（或者叫index）的暂存区，还有Git为我们自动创建的第一个分支`master`，以及指向`master`的一个指针叫`HEAD`。
	你的`git add`命令就是往暂存区里面添加，之后commit就推送到当前分支下
	
	当你把文件一个一个添加到暂存区(stage)时，使用git commit命令就可以一股脑的全推送到分支下了


<hr/>

## git命令：

#设置你的git用户信息（全局）
git config --global user.name "Your Name"
git config --global user.email "email@example.com"

#初始化git仓库
**git init** 

#添加代码或文件到git的暂存区
**git add (filename)**

#提交到仓库
**git commit -m "描述"**

#查看当前git仓库的状态
**git status**

#修改文件时，查看改动了什么
**git diff (filename)**

#查看仓库的历史提交信息
**git log**

#比较简洁地查看历史提交信息
**git log --pretty=oneline**

#查看仓库的命令记录
**git reflog**

#回滚到某一时间点，或者回到未来的某一时间点，(根据commit_id)
**git reset --hard (commit_id)
git reset --hard (HEAD^)**

#文件已经编辑，但没有提交到暂存区，撤销编辑
**git checkout -- (filename)**

#文件已经编辑，并且已经提交到暂存区，清空暂存区并撤销编辑
**git reset HEAD (filename)**
**git checkout -- (filename)**

#删除git仓库中的某个文件
1. 首先在工作区中删除该文件
	**rm -rf (filename)**
	
  2. 然后在git版本库中将其删除并记录改动
  	**git rm (filename)
  	git commit -m "delete a file"**


#关联远程仓库(以GitHub为例)并第一次进行推送到远程仓库

```
git retome add origin git@github.com:michaelliao/learngit.git
git push -u origin master
```

#推送最新修改到远程仓库

```
git push origin master
```

#从远程仓库中克隆仓库到本地

```
git clone git@github.com:(username@repositoryname)
```

#创建git分支
```
git branch <branch name>
```

#删除git分支

```
git branch -d <branch name>
```

#切换分支(两种)

```
git switch <branch name>			#需要git版本2.23以上
git checkout <branch name>
```

#合并分支

```
git merge <branch name>
```

<hr/>

##  git与GitHub或Gitee(码云)的远程连接
**GitHub：**
首先，GitHub与本地git可以采用ssh加密连接，所以就需要一个ssh公钥和密钥。创建SSH Key。在用户主目录下，看看有没有.ssh目录，如果有，再看看这个目录下有没有id_rsa和id_rsa.pub这两个文件，如果已经有了，可直接跳到下一步。如果没有，打开Shell（Windows下打开Git Bash），创建SSH Key：

```
ssh-keygen -t rsa -C "youremail@example.com"
```

之后在GitHub的对应配置里配置上你的公钥就可以了。

使用命令关联远程仓库后就可以在本地操作了。
**最近开始学习git这个版本控制系统，这个博客作为个人的git学习记录博客。**

个人是去廖雪峰的网站看git教程的。

@[TOC]

<hr/>

## git与集中式版本控制系统区别
git和集中式版本控制系统的**区别**大致有：
	1. 分布式管理，不在太过依赖中央服务器，没网也可以进行工作。
	2. 在集中式版本控制系统中的中央服务器如果误删除了你的git仓库，或者服务器故障，那么你存放的git代码也无法找回了，而分布式可以有多个副本，如果一个出现故障，可以去别的那里备份
	3. 分布式管理代码，效率会更高。
	4. git管理的是文件的修改，而集中式如svn管理的是文件
	*4. 等等，后续发现接着补充。。。*

由于是分布式管理，所以一个团队里不同的开发人员写好代码后可以互相推送，前提是要在同一个局域网下。如果不在同一个局域网下的话，git它是有一个类似“中央服务器”的电脑，可以拿它来中转，这里借用一下廖雪峰老师的图：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200311205026743.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0pva2Vyb25lZQ==,size_16,color_FFFFFF,t_70)
这样就可以完成团队间的协作了。

<hr/>

## git的内部结构:

**1. 工作区(Working DIrectory)**
 	工作区就是你当前git仓库所在的目录
 	![在这里插入图片描述](https://img-blog.csdnimg.cn/2020031217124978.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0pva2Vyb25lZQ==,size_16,color_FFFFFF,t_70)
 	我这里是git目录
**2. 版本库（Repository）**
 	工作区里面有一个隐藏的`.git`文件,这个就是Git的版本库
	Git的版本库里存了很多东西，其中最重要的就是称为`stage`（或者叫index）的暂存区，还有Git为我们自动创建的第一个分支`master`，以及指向`master`的一个指针叫`HEAD`。
	你的`git add`命令就是往暂存区里面添加，之后commit就推送到当前分支下
	
	当你把文件一个一个添加到暂存区(stage)时，使用git commit命令就可以一股脑的全推送到分支下了


<hr/>

## git命令：

#设置你的git用户信息（全局）
git config --global user.name "Your Name"
git config --global user.email "email@example.com"

### 初始化git仓库
**git init** 

### 添加代码或文件到git的暂存区
**git add (filename)**

### 提交到仓库
**git commit -m "描述"**

### 查看当前git仓库的状态
**git status**

### 修改文件时，查看改动了什么
**git diff (filename)**

### 查看仓库的历史提交信息
**git log**

### 比较简洁地查看历史提交信息
**git log --pretty=oneline**

### 查看仓库的命令记录
**git reflog**

### 回滚到某一时间点，或者回到未来的某一时间点，(根据commit_id)
**git reset --hard (commit_id)
git reset --hard (HEAD^)**

### 文件已经编辑，但没有提交到暂存区，撤销编辑
**git checkout -- (filename)**

### 文件已经编辑，并且已经提交到暂存区，清空暂存区并撤销编辑
**git reset HEAD (filename)**
**git checkout -- (filename)**

### 删除git仓库中的某个文件
1. 首先在工作区中删除该文件
	**rm -rf (filename)**
	
  2. 然后在git版本库中将其删除并记录改动
  	**git rm (filename)
  	git commit -m "delete a file"**


### 关联远程仓库(以GitHub为例)并第一次进行推送到远程仓库

```
git retome add origin git@github.com:michaelliao/learngit.git
git push -u origin master
```

### 推送最新修改到远程仓库

```
git push origin master
```

### 从远程仓库中克隆仓库到本地

```
git clone git@github.com:(username@repositoryname)
```

### 创建git分支
```
git branch <branch name>
```

### 删除git分支

```
git branch -d <branch name>
```

### 切换分支(两种)

```
git switch <branch name>			#需要git版本2.23以上
git checkout <branch name>
```

### 合并分支

```
git merge <branch name>
```

### git log参数之显示合并图，缩短显示commit_id

```
git log --graph --pretty=oneline --abbrev-commit	#--graph显示分支合并图，--abbrev-commit只显示commit_id前几位
```

<hr/>

##  git与GitHub或Gitee(码云)的远程连接
**GitHub：**
首先，GitHub与本地git可以采用ssh加密连接，所以就需要一个ssh公钥和密钥。创建SSH Key。在用户主目录下，看看有没有.ssh目录，如果有，再看看这个目录下有没有id_rsa和id_rsa.pub这两个文件，如果已经有了，可直接跳到下一步。如果没有，打开Shell（Windows下打开Git Bash），创建SSH Key：

```
ssh-keygen -t rsa -C "youremail@example.com"
```

之后在GitHub的对应配置里配置上你的公钥就可以了。

使用命令关联远程仓库后就可以在本地操作了。

