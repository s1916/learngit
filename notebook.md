git add filename    //添加到暂存区<br>
git commit -m "备注"    //提交<br>
git log     //查看日志<br>
git log --pretty=oneline    //简洁显示日志<br>
git reset --hard HEAD^      //回到上个版本<br>
git reset --hard HEAD^^     //回到上上个版本<br>
cat filename    //查看文本文件<br>
git reset --hard id前几位   //回到指定id版本<br>
git status      //查看状态<br>
git checkout -- filename    //用版本库的替换本机的文件<br>
git reset HEAD filename     //撤销暂存区的东西<br>
git rm filename     //删除文件，最后还需要commit提交<br>

-------------------------------------------------------------------------

//远程库<br>
<br>
ssh-keygen -t rsa -C "youremail@example.com"    //创建SSHkey<br>
git remote add origin git@server-name:path/repo-name.git   //添加远程库<br>
git remote //查看远程库信息<br>
git remote -v   //查看远程库详细信息<br>
git push (-u) origin master    //把本地master推送到远程库origin,第一次使用加上-u参数，表示将远程库与本地连接起来<br>
git remote -v   //查看远程库信息<br>
git remote rm origin    //删除远程库链接<br>
git checkout -b dev origin/dev  //新建dev分支并与远程库origin/dev分支建立跟踪关系<br>
git branch --set-upstream-to=origin/dev dev     //将本地dev分支与远程origin/dev分支连接<br>
git pull    //从远程库拉取分支，可能和本地分支有冲突，需要手动解决<br>
git push    //推送到远程库<br>

-------------------------------------------------------------------------
因此，多人协作的工作模式通常是这样：<br>
首先，可以试图用git push origin <branch-name>推送自己的修改；<br>
如果推送失败，则因为远程分支比你的本地更新，需要先用git pull试图合并；<br>
如果合并有冲突，则解决冲突，并在本地提交；<br>
没有冲突或者解决掉冲突后，再用git push origin <branch-name>推送就能成功！<br>

-------------------------------------------------------------------------

//分支管理<br>
git branch dev     //创建dev分支<br>
git checkout dev        //切换到dev分支<br>
git switch dev          //也是切换到dev分支<br>
git checkout -b dev     //创建并切换到dev分支，git checkout命令加上-b参数表示创建并切换<br>
git switch -c dev       //同上<br>
git branch      //查看分支<br>
git merge dev   //合并dev分支到master分支<br>
git branch -d dev   //删除dev分支<br>
git branch -D dev   //强制删除未合并的dev分支<br>
git log --graph --pretty=oneline --abbrev-commit    //图表展示分支<br>
<br>
git stash   //保存现场<br>
git stash list      //现场列表<br>
git stash apply .  //恢复现场.<br>
git stash drop .   //删除现场.<br>
git stash pop .    //恢复并删除现场.<br>
先git branch展示所有分支再git cherry-pick 4c80    //把编号4c80的提交复制到所有分支上<br>

-------------------------------------------------------------------------

git tag <tagname>   //用于新建一个标签，默认为HEAD，也可以指定一个commit id<br>
git tag -a <tagname> -m "备注"      //指定标签名和备注信息<br>
git tag     //查看所有标签<br>
git tag -d v1.0     //删除标签v1.0<br>
git push origin v1.0   //推送标签到远程库<br>
git push origin --tags  //推送所有标签到远程库  <br>

------------
如果标签已经推送到远程，要删除远程标签就麻烦一点，先从本地删除：git tag -d v0.9<br>

然后，从远程删除：git push origin :refs/tags/v0.9<br>

------------