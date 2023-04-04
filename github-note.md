## Git区域
工作区 --> 暂存区 --> Head  --> 远程库
      add       commit     push
工作区是你肉眼可见的文件那些
暂存区和head都属于版本库 是隐藏文件

## Git 基本操作

git add .
意思是提交所有文件
此处将文件从工作区提交到暂存区

git commit -m 'xxx'
xxx是本次提交的说明 一定要写

每次修改一定是先add 否则无法commit

git push origin main
提交到远程库

**删除文件**
直接在文件管理器中删，或者用rm命令删：
$ rm test.txt

这个时候，Git知道你删除了文件，因此，工作区和版本库就不一致了，git status命令会立刻告诉你哪些文件被删除
$ git status
On branch master
Changes not staged for commit:
  (use "git add/rm <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

	deleted:    test.txt

no changes added to commit (use "git add" and/or "git commit -a")

再从版本库中删除该文件，用命令git rm删掉，并且git commit：
$ git rm test.txt
rm 'test.txt'

$ git commit -m "remove test.txt"
[master d46f35e] remove test.txt
 1 file changed, 1 deletion(-)
 delete mode 100644 test.txt
现在，文件就从版本库中被删除了

最后 把远程库里的同步一下
$ git push origin main