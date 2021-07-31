---
title: Git如何创建远程分支并提交文件
date: 2021-07-29 14:04:51
tags:
  - git
  - github
categories:
  - 测试工具
---

GIT (分布式版本控制系统) 编辑 Git是一款免费、开源的分布式版本控制系统,用于敏捷高效地处理任何或小或大的项目。了解和掌握它的基本用法是每个it人员的必备技能，详细的用法网上资料特别多，这里我专门梳理下这个场景 - “创建远程分支并提交文件”，个人认为这个场景使用非常的普遍，它涵盖了git的常用命令并直观的体现了git的工作原理，掌握了它对我们后续深入学习git很有帮助。

Common Commands -
1. 让本地文件夹作为git的版本控制创库
$ Git init
2. 创建新的分支：
$ Git branch branchName # 但依旧停留在当前分支
$ Git checkout -b branchName # 创建后并切换到该分支
3. 删除分支
$ Git branch -d branName
4. 切换到制定分支
$ Git checkout branchName
5. 查看远程仓库信息及常用操作
git remote -v：                                查看远程仓库详细信息，可以看到仓库名称
git remote remove orign：                      删除orign仓库（如果把origin拼写成orign，删除错误名称仓库）
git remote add origin 仓库地址：                重新添加远程仓库地址
gti push -u origin master：                    提交到远程仓库的master主干
此命令可以帮助查看当前本地仓库与远程仓库的关联情况，-v 会列出远程仓库主机名称，网址等信息（origin通常是默认远程主机名称）
6. 查看分支
查看本地分支
git branch, *号表示当前所在分支；git branch -v；git branch -vv，可以查看上流分支的名字；
查看所有远程分支
git branch -r，-r就是-remote；
查看所有本地分支与远程分支
git branch -a，-a就是-all；
7. 关联本地仓库和远程仓库
$ git remote add origin https://github.com/lelloandluck/basicfiles_backup.git

---
Scenario -
	**创建远程分支**（请确保step#7 已关联，不然本地分支无法识别远程仓库，也就无法创建远程分支了）
	把新建分支push到远程服务器
	• $ git push origin localbranch:newbranch_remote

  删除远程分支
  • $ git push origin :newbranch_remote
	• $ git push origin --delete newbranch_remote
	• 增加要上传的文件到本地分支
	• $ git add .
	• $ git commit -m "description for commit purpose"

**Reference document -**
在我们第一次提交git的时候：
![截图1](/medias/gitOpper001.png)
发现上面用了这个-u参数，也没作解释，特意搜索了下这个-u的用法，加了参数-u后，以后即可直接用git push 代替git push origin master
git push -u origin master

**对于经常更新的文件，如果我们需要备份它到远程仓库，就可以借用上面的方法来实现** -
1. 建立远程仓库链接后
2. 建立关联的远程分支
3. 将更新的文件加入本地仓库
4. Git add .
5. Git commit -m "description"
6. Git push -u origin "远程分支名称"
