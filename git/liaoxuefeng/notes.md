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

https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/0013745374151782eb658c5a5ca454eaa451661275886c6000