## 简介

**Git是分布式版本控制系统**

- 集中式和分布式版本控制系统有什么区别呢？

```
先说集中式版本控制系统，版本库是集中存放在中央服务器的，而干活的时候，用的都是自己的电脑，所以要先从中央服务器取得最新的版本，然后开始干活，干完活了，再把自己的活推送给中央服务器。中央服务器就好比是一个图书馆，你要改一本书，必须先从图书馆借出来，然后回到家自己改，改完了，再放回图书馆。
```

## 设置邮箱和姓名

```git
$ git config --global user.name "Your Name"
$ git config --global user.email "email@example.com"
```

**注意`git config`命令的`--global`参数，用了这个参数，表示你这台机器上所有的Git仓库都会使用这个配置，当然也可以对某个仓库指定不同的用户名和Email地址。**

## 创建版本库

 **简介**

版本库又名仓库，英文名**repository**，你可以简单理解成一个目录，这个目录里面的所有文件都可以被Git管理起来，每个文件的修改、删除，Git都能跟踪，以便任何时刻都可以追踪历史，或者在将来某个时刻可以“还原”。

通过`git init`命令把当前所在目录变成Git可以管理的仓库

```
git init // 将当前所在目录（pwd可查看）变成git管理的仓库
```

在进行git init 后，当前目录下面就是多一个隐藏文件 .git 

 用`ls -ah`命令就可以看见。

## GIT 将文件添加到仓库（版本库）

添加文件到Git仓库，分两步：

1. 使用命令`git add ` <fileName>，注意，可反复多次使用，添加多个文件；
2. 使用命令`git commit -m `，完成。  //-m 后面的注释：解释跟新了哪些内容

 // 注意 你添加 的文件一定要在 git init 的文件夹下面

## 基础命令

### git status 

功能：可以让我们掌握当前仓库的状态

```
$ git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

	modified:   readme.txt

no changes added to commit (use "git add" and/or "git commit -a")
```

上面的命令输出告诉我们，`readme.txt`被修改过了，但还没有准备提交的修改。

### git diff

功能：查看文件的哪些地方被改动了

git diff <fileName>

只能查看到文本类文件哪里改动了。图片、视频类文件看不出来哪里改动了，只会区分文件大小上的变化。

```
$ git diff readme.txt 
diff --git a/readme.txt b/readme.txt
index 46d49bf..9247db6 100644
--- a/readme.txt
+++ b/readme.txt
@@ -1,2 +1,2 @@
-Git is a version control system.
+Git is a distributed version control system.
 Git is free software.
```

### git log

`git log`命令显示从最近到最远的提交日志

```
$ git log
commit 1094adb7b9b3807259d8cb349e7df1d4d6477073 (HEAD -> master)
Author: Michael Liao <askxuefeng@gmail.com>
Date:   Fri May 18 21:06:15 2018 +0800

    append GPL

commit e475afc93c209a690c39c13a46716e8fa000c366
Author: Michael Liao <askxuefeng@gmail.com>
Date:   Fri May 18 21:03:36 2018 +0800

    add distributed

commit eaadf4e385e865d25c48e7ca9c8395c3f7dfaef0
Author: Michael Liao <askxuefeng@gmail.com>
Date:   Fri May 18 20:59:18 2018 +0800

    wrote a readme file
```

如果嫌输出信息太多，看得眼花缭乱的，可以试试加上`--pretty=oneline`参数：

```
$ git log --pretty=oneline
1094adb7b9b3807259d8cb349e7df1d4d6477073 (HEAD -> master) append GPL
e475afc93c209a690c39c13a46716e8fa000c366 add distributed
eaadf4e385e865d25c48e7ca9c8395c3f7dfaef0 wrote a readme file
```

**不足**：

会丢失回到的reset之后的版本

### git reset

功能 ： 返回之前的版本

```
$ git reset --hard HEAD^
HEAD is now at e475afc add distributed
```

上面的操作是返回到上一个版本

以此类推，返回的上上个版本，就是HEAD^^

当返回的版本非常靠前的 时候。比如返回到上100个版本 HEAD~100，

- git reset --hard HEAD^
- git reset --hard <commit ID>  //commit ID不需要全部，只要git能识别出唯一的版本就行

### git reflog

`git reflog`用来记录你的每一次命令：

```
$ git reflog
e475afc HEAD@{1}: reset: moving to HEAD^
1094adb (HEAD -> master) HEAD@{2}: commit: append GPL
e475afc HEAD@{3}: commit: add distributed
eaadf4e HEAD@{4}: commit (initial): wrote a readme file
```

## 远程数据库

### 添加远程数据库

两步走

1. git remote add origin git@github.com:xia-2/HousekeepingBackgroundManagement.git

2. git push -u origin master

### 查看当前远程数据库

```
$ git remote -v   
// 或者
$ cat .git/config
```

```
origin  https://github.com/luodao236/test.git (fetch)
origin  https://github.com/luodao236/test.git (push)
test    https://github.com/luodao236/onceAgain.git (fetch)
test    https://github.com/luodao236/onceAgain.git (push)
```



### 查看某个远程数据库

**git remote remove <name>**
**$ git remote remove test**

结果为：

```
$ git remote -v
origin  https://github.com/luodao236/test.git (fetch)
origin  https://github.com/luodao236/test.git (push)
```



## SSH秘钥

### 检查SSH密钥是否存在

- 输入下面命令`ls -l ~/.ssh`
- 输入下面命令`cd ~/.ssh`，`ls -l ~/`
   如果有文件id_rsa.pub 或 id_dsa.pub，则密钥存在。



```rust
wwwdeiMac:~ www$ ls -l ~/.ssh
total 24
-rw-------  1 www  staff  1766  2  2  2018 id_rsa
-rw-r--r--@ 1 www  staff   402  2  2  2018 id_rsa.pub
-rw-r--r--  1 www  staff   367  2 26 11:25 known_hosts
```

### 生成新的ssh密钥

在命令行中输入`ssh-keygen -t rsa -C "your_email@example.com"`

```php
wwwdeiMac:~ www$ ssh-keygen -t rsa -C "your_email@example.com"
# Creates a new ssh key using the provided email
Generating public/private rsa key pair.
Enter file in which to save the key (/your_home_path/.ssh/id_rsa):
```

- 生成ssh 密钥后，可以到~/.ssh目录下查看相关文件，一般来说ssh 密钥会包含**id_rsa**和**id_rsa.pub**两个文件，分别表示生成的**私钥**和**公钥**。
- 在git等源代码管理中，使用`cat ~/.ssh/id_rsa.pub`命令，打印并将相应内容复制到源代码管理服务器即可实现git的无密码管理。



