1、创建版本

```dockerfile
第一步
$ mkdir learngit
$ cd learngit
$ pwd		//pwd命令用于显示当前目录。
/Users/michael/learngit

第二布
$ git init
Initialized empty Git repository in /Users/michael/learngit/.git/

```

2、提交修改后的内容

```dockerfile
$ git add readme.txt | .
$ git commit -m "wrote a readme file"
[master (root-commit) eaadf4e] wrote a readme file
 1 file changed, 2 insertions(+)
 create mode 100644 readme.txt
```

3、查看被修改的文件

```dockerfile
$ git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

    modified:   readme.txt

no changes added to commit (use "git add" and/or "git commit -a")
```

4、查看具体的修改内容

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

5、显示最近到最远的提交日志

```
$ git log
$ git log --pretty=oneline		//减少输出的内容
```

6、把当前版本回退到上一个版本

```
git reset --hard HEAD^
```

上一个版本就是`HEAD^`，上上一个版本就是`HEAD^^`，上100个版本写成`HEAD~100`。

7、查看每一次操作记录

```
$ git reflog
e475afc HEAD@{1}: reset: moving to HEAD^
1094adb (HEAD -> master) HEAD@{2}: commit: append GPL
e475afc HEAD@{3}: commit: add distributed
eaadf4e HEAD@{4}: commit (initial): wrote a readme file
```

8、把文件往git版本库里添加的时候， 是分两部执行：

​	第一步是用git add吧文件添加进去，实际上就是把文件修改添加到暂存区。

​	第二不是用git commit提交更改，实际上就是把暂存区的所有内容提交到当前分支。

因为我们创建git版本库时，git自动为我们创建了唯一一个master分支，所以，现在，git commit就是往master分支上提交更改。

![](0.jpeg)

9、把readme.txt 文件在工作区的修改全部撤销：

```
$ git checkout --readme.txt
```

一种是readme.txt 自修改后还咩有被放到暂存区，现在，撤销修改就回到和版本库一模一样的状态；

一种是readme.txt 已经添加到暂存区后，又做了修改，现在，撤销修改就回到添加到暂存区后的状态。

10、删除文件

```
$ git rm test.txt
```

https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/001374385852170d9c7adf13c30429b9660d0eb689dd43a000