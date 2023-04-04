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

每次操作完可以看git status
它会告诉你文件有被修改过 
  modified ：filename

git push origin main
提交到远程库

**删除文件** <br>
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

## Git分支
分支就相当于平行宇宙 在分支里的操作不影响main 但结果是可以合并的  
创建分支 git branch xx  
切换到分支 git checkout xx  
这两步骤可以合并git checkout -b xx  
查看所有分支 git branch  
删除分支 git branch -d xxx  


**更新代码到分支**  
先切换到分支  
git add ./  
git commit -m ""  
git push origin 分支名  

**合并分支到main**
先切换到main   git checkout main  
然后合并 git merge 分支名  
最后删除分支 git branch -d 分支（删除本地分支）  
git删除远程分支  
git push origin --delete [branch_name]  

**查看分支**
查看本地分支 git branch  
查看远程分支 git branch -r  
查看本地和远程分支 git branch -a  



** 如何把本地仓库里的内容搬运到github上 **
首先在本地目标仓库打开bash 输入git init 将当前仓库变成git可管理的仓库  
然后add+commit一波操作猛如虎  
再在git创建远程仓库   
把远程和本地关联    git remote add origin 仓库地址  
关联之后推送$ git push -u origin main【不要写成master不然创建一个新的master分支】  
新建的远程仓库是空的，所以要加上 -u 这个参数  
