git add filename    //添加到暂存区
git commit -m "备注"    //提交
git log     //查看日志
git log --pretty=oneline    //简洁显示日志
git reset --hard HEAD^      //回到上个版本
git reset --hard HEAD^^     //回到上上个版本
cat filename    //查看文本文件
git reset --hard id前几位   //回到指定id版本
git status      //查看状态
git checkout -- filename    //用版本库的替换本机的文件
git reset HEAD filename     //撤销暂存区的东西
git rm filename     //删除文件，最后还需要commit提交

-------------------------------------------------------------------------

//远程库

ssh-keygen -t rsa -C "youremail@example.com"    //创建SSHkey
git remote add origin git@server-name:path/repo-name.git   //添加远程库
git remote //查看远程库信息
git remote -v   //查看远程库详细信息
git push (-u) origin master    //把本地master推送到远程库origin,第一次使用加上-u参数，表示将远程库与本地连接起来
git remote -v   //查看远程库信息
git remote rm origin    //删除远程库链接
git checkout -b dev origin/dev  //新建dev分支并与远程库origin/dev分支建立跟踪关系
git branch --set-upstream-to=origin/dev dev     //将本地dev分支与远程origin/dev分支连接
git pull    //从远程库拉取分支，可能和本地分支有冲突，需要手动解决
git push    //推送到远程库

-------------------------------------------------------------------------
因此，多人协作的工作模式通常是这样：
首先，可以试图用git push origin <branch-name>推送自己的修改；
如果推送失败，则因为远程分支比你的本地更新，需要先用git pull试图合并；
如果合并有冲突，则解决冲突，并在本地提交；
没有冲突或者解决掉冲突后，再用git push origin <branch-name>推送就能成功！

-------------------------------------------------------------------------

//分支管理
git branch dev     //创建dev分支
git checkout dev        //切换到dev分支
git switch dev          //也是切换到dev分支
git checkout -b dev     //创建并切换到dev分支，git checkout命令加上-b参数表示创建并切换
git switch -c dev       //同上
git branch      //查看分支
git merge dev   //合并dev分支到master分支
git branch -d dev   //删除dev分支
git branch -D dev   //强制删除未合并的dev分支
git log --graph --pretty=oneline --abbrev-commit    //图表展示分支

git stash   //保存现场
git stash list      //现场列表
git stash apply **  //恢复现场**
git stash drop **   //删除现场**
git stash pop **    //恢复并删除现场**
先git branch展示所有分支再git cherry-pick 4c80    //把编号4c80的提交复制到所有分支上

-------------------------------------------------------------------------

git tag <tagname>   //用于新建一个标签，默认为HEAD，也可以指定一个commit id
git tag -a <tagname> -m "备注"      //指定标签名和备注信息
git tag     //查看所有标签
git tag -d v1.0     //删除标签v1.0
git push origin v1.0   //推送标签到远程库
git push origin --tags  //推送所有标签到远程库  

------------
如果标签已经推送到远程，要删除远程标签就麻烦一点，先从本地删除：git tag -d v0.9

然后，从远程删除：git push origin :refs/tags/v0.9

------------