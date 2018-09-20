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

11、创建 SSH Key

```
$ ssh-keygen -t rsa -c "youremail@example.com"
```

12、把一个已有的本地仓库与 github 关联

```
$ git remote add origin git@github.com:michaelliao/learngit.git
//把本地库的内容推送到远程，用git push命令，实际上是把当前分支master推送到远程
$ git push -u origin master
```

13、从远程库克隆

```
$ git clone git@github.com:michaelliao/gitskills.git
```

14、分支控制

```
//切换 dev 分支（加上 -b 表示创建并切换）
$ git checkout -b dev
//相当于如下语句
$ git branch dev
$ git checkout dev
//查看当前分值
$ git branch
// 在master主干上面，合并dev分支
$ git merge <name>
//删除分支
$ git branch -d <name>
```

15、解决冲突

​	1）、遇到冲突

​	2）、查看当前分支

​	3）、手动修改主干道被分支修改的内容，在主干道提交

​	4）、在主干道合并分支

​	5）、删除分支

16、在分支1上面做了修改，但是当前需要完成另外一个任务。

​	1）、把当前的工作现场“存储”起来：git stash

​	2）、切换到主干道

​	3）、创建另外一个分支： 分支2

​	4）、在分支2上面做修改，

​	5）、修改完成后切换到主干道，最后删除分支2

```
$ git checkout master
Switched to branch 'master'
Your branch is ahead of 'origin/master' by 6 commits.
  (use "git push" to publish your local commits)

$ git merge --no-ff -m "merged bug fix 101" issue-101
Merge made by the 'recursive' strategy.
 readme.txt | 2 +-
 1 file changed, 1 insertion(+), 1 deletion(-)
```

​	6）、切换到dev分支，恢复被stash存储的内容

```
一是用git stash apply恢复，但是恢复后，stash内容并不删除，你需要用git stash drop来删除；
另一种方式是用git stash pop，恢复的同时把stash内容也删了：
$ git stash pop
On branch dev
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

    new file:   hello.py

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

    modified:   readme.txt

Dropped refs/stash@{0} (5d677e2ee266f39ea296182fb2354265b91b3b2a)
```

查看stash内容

```
$ git stash list
$ git stash apply stash@{0}
```

17、多人协作开发

```
//要在dev分支上开发，就必须创建远程origin的dev分支到本地
$ git checkout -b dev origin/dev
//指定本地dev分支与远程origin/dev分支的链接
$ git branch --set-upstream-to=origin/dev dev
```

思路：

```
1、首先，可以试图用git push origin <branch-name>推送自己的修改；
2、如果推送失败，则因为远程分支比你的本地更新，需要先用git pull试图合并；
3、如果合并有冲突，则解决冲突，并在本地提交；
4、没有冲突或者解决掉冲突后，再用git push origin <branch-name>推送就能成功！
```

18、Rebase

查看历史提交记录

```
$ git log --graph --pretty=oneline --abbrev-commit
* 582d922 (HEAD -> master) add author
* 8875536 add comment
* d1be385 (origin/master) init hello
*   e5e69f1 Merge branch 'dev'
|\  
| *   57c53ab (origin/dev, dev) fix env conflict
| |\  
| | * 7a5e5dd add env
| * | 7bd91f1 add new env
...
```

通过rebase 把分差的提交历史“整理”城一条直线

```
$ git rebase
First, rewinding head to replay your work on top of it...
Applying: add comment
Using index info to reconstruct a base tree...
M    hello.py
Falling back to patching base and 3-way merge...
Auto-merging hello.py
Applying: add author
Using index info to reconstruct a base tree...
M    hello.py
Falling back to patching base and 3-way merge...
Auto-merging hello.py
$ git log --graph --pretty=oneline --abbrev-commit
* 7e61ed4 (HEAD -> master) add author
* 3611cfe add comment
* f005ed4 (origin/master) set exit=1
* d1be385 init hello
...
```

19、标签管理

发布一个版本时，我们通常先在版本库中打一个标签（tag），这样，就唯一确定了打标签时刻的版本。将来无论什么时候，取某个标签的版本，就是把那个打标签的时刻的历史版本去出来。所以，标签也是版本库的一个快照。

20、打标签

```
//切换到要打标签的分支上
$ git branch
* dev
  master
$ git checkout master
Switched to branch 'master'

// 打标签
$ git tag v1.0
$ git tag
v1.0

//在历史提交的commit id 上面打标签
$ git log --pretty=oneline --abbrev-commit
12a631b (HEAD -> master, tag: v1.0, origin/master) merged bug fix 101
4c805e2 fix bug 101
e1e9c68 merge with no-ff
f52c633 add merge
cf810e4 conflict fixed
5dc6824 & simple
14096d0 AND simple
b17d20e branch test
d46f35e remove test.txt
b84166e add test.txt
519219b git tracks changes
e43a48b understand how stage works
1094adb append GPL
e475afc add distributed
eaadf4e wrote a readme file
$ git tag v0.9 f52c633

//带指定说明文字打标签
$ git tag -a v0.1 -m "version 0.1 released" 1094adb

//看到说明文字
$ git show v0.1
tag v0.1
Tagger: Michael Liao <askxuefeng@gmail.com>
Date:   Fri May 18 22:48:43 2018 +0800

version 0.1 released

commit 1094adb7b9b3807259d8cb349e7df1d4d6477073 (tag: v0.1)
Author: Michael Liao <askxuefeng@gmail.com>
Date:   Fri May 18 21:06:15 2018 +0800

    append GPL

diff --git a/readme.txt b/readme.txt
...
```

21、操作标签

```
// 删除标签(创建的标签都只存储在本地，不会自动推送到远程)
$ git tag -d v0.1
Deleted tag 'v0.1' (was f15b0dd)

// 推送某个标签到远程，使用命令 git push origin <tagname>
$ git push origin v1.0
Total 0 (delta 0), reused 0 (delta 0)
To github.com:michaelliao/learngit.git
 * [new tag]         v1.0 -> v1.0
 //一次性推送全部尚未推送到远程的本地标签
$ git push origin --tags
Total 0 (delta 0), reused 0 (delta 0)
To github.com:michaelliao/learngit.git
 * [new tag]         v0.9 -> v0.9
```

删除远程标签，步骤：

1）、先删除本地标签

2）、从远程删除

```
$ git tag -d v0.9
Deleted tag 'v0.9' (was f52c633)
$ git push origin :refs/tags/v0.9
To github.com:michaelliao/learngit.git
 - [deleted]         v0.9
```

22、使用GitHub

```
//查看远程库信息
$ git remote -v
//删除已有的GitHub远程库
$ git remote rm origin
```

