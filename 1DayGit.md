# Git    重温!

##### *不要使用Windows自带的**记事本** 编辑任何文本文件(原因是Microsoft开发记事本的团队保存UTF-8编码的文件，在每个文件开头添加了0xefbbbf（十六进制）的字符，导致，比如，网页第一行可能会显示一个“?”，程序一编译就报语法错误，等等。)

##### 1.设置机器设备名字和邮箱

```shell
$ git config --global user.name "Your Name"
$ git config --global user.email "email@example.com"
```

##### 2.创建版本库

```shell
$ mkdir learngit    //创建
$ cd learngit
$ pwd      //这是显示目录结构
/Users/michael/learngit     //目录结构

$ git init    //初始化仓库
Initialized empty Git repository in /Users/michael/learngit/.git/

$ git add readme.txt  //添加文件到仓库   

```

##### 3.提交到仓库(git  add 添加到缓存区)

```shell
$ git add file1.txt    //先提交到缓存区  等待合并到分支
$ git add file2.txt file3.txt
//为什么Git添加文件需要add，commit一共两步呢？因为commit可以一次提交很多文件，所以你可以多次add不同的文件
$ git commit -m "add 3 files."
```

##### 4.查看修改

```shell
$ git status          //查看修改状态
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

	modified:   readme.txt

no changes added to commit (use "git add" and/or "git commit -a")

$ git diff readme.txt     //查看修改内容
diff --git a/readme.txt b/readme.txt
index 46d49bf..9247db6 100644
--- a/readme.txt
+++ b/readme.txt
@@ -1,2 +1,2 @@
-Git is a version control system.
+Git is a distributed version control system.
 Git is free software.
```

```
$ git log   //查看修改提交的纪录
$ git log  --pretty=oneline   //查看修改提交的纪录(精简信息 一行)

```

##### 5.回退版本

```shell
$ git reset --hard HEAD^   //回退上一版本  HEAD 当前版本  HEAD^^ 上上一版本  ....

$git reset --hard "commit_id"   //只要填前几个has值就行  自动索引

$ git reset HEAD readme.txt  //命令git reset HEAD <file>可以把暂存区的修改撤销掉

$ git reflog    //查看命令历史记录  防止不能回到最新版本

$ git checkout -- "file"     //重新回退到上一次最新修改

场景1：当你改乱了工作区某个文件的内容，想直接丢弃工作区的修改时，用命令 `git checkout -- file`。

场景2：当你不但改乱了工作区某个文件的内容，还添加到了暂存区时，想丢弃修改，分两步，第一步用命令 `git reset HEAD <file>`，就回到了场景1，第二步按场景1操作。

场景3：已经提交了不合适的修改到版本库时，想要撤销本次提交，参考[版本回退](https://www.liaoxuefeng.com/wiki/896043488029600/897013573512192)一节，不过前提是没有推送到远程库。

```

##### 6.删除文件 (命令 `git rm`用于删除一个文件。文件已经被提交到版本库，不用担心误删，只能恢复文件到最新版本，会丢失**最近一次提交后你修改内容**)

```shell
$ rm test.txt    //移除工作区文件

$ git rm test.txt   // 1. git rm删掉，并且git commit

$ git checkout -- test.txt    //2.误删工作区文件   恢复版本库文件

```

##### 7.远程仓库

```shell
//第1步
$ ssh-keygen -t rsa -C "1796646806@qq.com"   //创建SSH Key   在用户主目录下 id_rsa是私钥   id_rsa.pub是公钥

//第2步
登陆GitHub，打开“Account settings”，“SSH Keys”页面
然后，点“Add SSH Key”，填上任意Title，在Key文本框里粘贴id_rsa.pub文件的内容

//第3步
$ git  remote  add  origin  git@github.com:LemoncLin/JavaScriptDay.git    //关联github远程库  

```

##### *不要使用Windows自带的**记事本** 编辑任何文本文件(原因是Microsoft开发记事本的团队保存UTF-8编码的文件，在每个文件开头添加了0xefbbbf（十六进制）的字符，导致，比如，网页第一行可能会显示一个“?”，程序一编译就报语法错误，等等。)

##### 1.设置机器设备名字和邮箱

```shell
$ git config --global user.name "Your Name"
$ git config --global user.email "email@example.com"
```

##### 2.创建版本库

```shell
$ mkdir learngit    //创建
$ cd learngit
$ pwd      //这是显示目录结构
/Users/michael/learngit     //目录结构

$ git init    //初始化仓库
Initialized empty Git repository in /Users/michael/learngit/.git/

$ git add readme.txt  //添加文件到仓库   

```

##### 3.提交到仓库(git  add 添加到缓存区)

```shell
$ git add file1.txt    //先提交到缓存区  等待合并到分支
$ git add file2.txt file3.txt
//为什么Git添加文件需要add，commit一共两步呢？因为commit可以一次提交很多文件，所以你可以多次add不同的文件
$ git commit -m "add 3 files."
```

##### 4.查看修改

```shell
$ git status          //查看修改状态
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

	modified:   readme.txt

no changes added to commit (use "git add" and/or "git commit -a")

$ git diff readme.txt     //查看修改内容
diff --git a/readme.txt b/readme.txt
index 46d49bf..9247db6 100644
--- a/readme.txt
+++ b/readme.txt
@@ -1,2 +1,2 @@
-Git is a version control system.
+Git is a distributed version control system.
 Git is free software.
```

```
$ git log   //查看修改提交的纪录
$ git log  --pretty=oneline   //查看修改提交的纪录(精简信息 一行)

```

##### 5.回退版本

```shell
$ git reset --hard HEAD^   //回退上一版本  HEAD 当前版本  HEAD^^ 上上一版本  ....

$git reset --hard "commit_id"   //只要填前几个has值就行  自动索引

$ git reset HEAD readme.txt  //命令git reset HEAD <file>可以把暂存区的修改撤销掉

$ git reflog    //查看命令历史记录  防止不能回到最新版本

$ git checkout -- "file"     //重新回退到上一次最新修改

场景1：当你改乱了工作区某个文件的内容，想直接丢弃工作区的修改时，用命令 `git checkout -- file`。

场景2：当你不但改乱了工作区某个文件的内容，还添加到了暂存区时，想丢弃修改，分两步，第一步用命令 `git reset HEAD <file>`，就回到了场景1，第二步按场景1操作。

场景3：已经提交了不合适的修改到版本库时，想要撤销本次提交，参考[版本回退](https://www.liaoxuefeng.com/wiki/896043488029600/897013573512192)一节，不过前提是没有推送到远程库。

```

##### 6.删除文件 (命令 `git rm`用于删除一个文件。文件已经被提交到版本库，不用担心误删，只能恢复文件到最新版本，会丢失**最近一次提交后你修改内容**)

```shell
$ rm test.txt    //移除工作区文件

$ git rm test.txt   // 1. git rm删掉，并且git commit

$ git checkout -- test.txt    //2.误删工作区文件   恢复版本库文件

```

##### 7.创建链接远程仓库

```shell
 //第1步
$ ssh-keygen -t rsa -C "1796646806@qq.com"   //创建SSH Key   在用户主目录下 id_rsa是私钥   id_rsa.pub是公钥

//第2步
登陆GitHub，打开“Account settings”，“SSH Keys”页面
然后，点“Add SSH Key”，填上任意Title，在Key文本框里粘贴id_rsa.pub文件的内容

//第3步
$ git  remote  add  origin  git@github.com:LemoncLin/JavaScriptDay.git    //关联github远程库  

//第4步
$ git push -u origin master   //第一次推送添加参数 -u   本地master和远程master 推送并且关联  (以后可以简化命令  $ git push origin master)
```

##### 8.删除远程仓库

```shell
$ git remote -v    //查看有哪些 远程仓库

$ git remote rm origin  //根据名字"删除"-> 解除了本地和远程的绑定关系


```
