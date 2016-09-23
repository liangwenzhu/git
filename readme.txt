hello

git add file                  把工作区的文件提交到暂存区stage
git commit -m"描述"           把暂缓区的文件提交到master。就是自己的本地库里。
git remote add origin git@826415551@qq.com/git.git     在个人github里创建一个名为"git"的git仓库，
                                                       在本地目录里添加名为"origin"的远程库，以后个人远程库就叫做origin了。 
git push origin master        把本地库master的文件同步到远程库里。 

git rm file                   工作台的情况（文件被删除）提交到暂存区。
git commit -m"描述"           暂存区被提交到master
git push origin master        把本地master库同步到网络库里（origin是库的名字，前面添加的）

从master把文件恢复到本地文件目录：
第一步，查询以往的操作，找到ID:          git reflog 
第二步，把文件从master恢复到stage:       git reset --hard ID  
第三部，把stage里的文件恢复到工作区      git reset HEAD file
第四步，把工作区的改动恢复到目录         git checkout -- file 

从网络库中的仓库把文件拷贝到本地：
git clone git@826415551@qq:liangwenzhu/gitskills.git  其中,邮箱和:后面的liangwenzhu是自己在github注册的邮箱和用户名，gitskills是仓库名。
储存工作状态                                      git stash
创建一个新的分支issue-01来修改master上的BUG       git branch issue-01   git checkout issue-01
修改完后合并到master                              git checkout master   git merge issue-01 
查看都有哪些工作现场                              git stash list
回到之前在dev分支上的工作状态                     git stash pop或者 git stash@[id] 回到指定工作状态
然后切换到master,合并dev 完成工作。       

为当前最新的COMMIT打标签。                        git tag v1.0
为以前的COMMIT打标签                            
1.找到以前COMMIT的ID                              git reflog
2.设置标签                                        git tag v1.1 id     其中,v1.0和v1.1都是标签名，自己设置的。
推送标签                                          git push origin v1.0
批量推送                                          git push origin --tags
删除标签                                          git tag -d v1.0
从远程端里删除标签                                git push origin:refs/tags/v1.0                       