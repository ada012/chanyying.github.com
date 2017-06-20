---
layout: post
title: 常用的git命令
description: ""
date: 2014-11-09
tags: [React]
comments: true
share: true
---

```
git status  //查看状态
changes：改变的意思；
commit：可提交状态（本地保存）
git commit -a //提交全部，把所有的changes变为commit
git commit -a -m"这里填写你修改的提示语句"；这个命令可以跳过commit -a 之后的弹出编辑提示语句的编辑器
gitk//图形化形式
git add   D://      //添加某一个文件
git add -A  //如果本地存在多份新添加的文件，就使用这个，不用一个一个add
git commit -a --amend // 把本次的commit追加到上次的commit
git checkout -b issue88 //创建并切换到issue88分支
git branch //查看本地分支
git branch -a    查看所有分支 
git checkout master   //切换到master分支 
git fetch origin issue88    //从服务器端下载最新的文件 
git rebase issue88   //把最新的文件合并到本地的issue88 
git push origin issue88  //把本地的issue88的commit上传到服务器端
git pull origin master//从服务器端下载master最新文件到本地
git diff  // 比较当前文件和暂存区文件不同情况
git merge <branch> //将branch分支合并到当前目录所在分支
git clone //从服务端下载整个库到本地
git help <command> //显示command的帮助

分支问题：
git branch    查看本地分支
git branch -r    查看远程分支
git push origin :branch    删除远程分支
git branch -d branch    删除本地分支
使用git checkout可以丢弃掉本地的改动，然后使用git pull去拿server上的最新更新。
比如，我想丢弃一个文件的所有改动：
git checkout routes.js
然后再使用git pull，就可以拿到server上的版本的代码了。
回退到上一次的commit
git reset HEAD^
回退到本次pull之前，(撤销本次pull)
git reset --hard HEAD
今天在一个分支上修改文件，然后线上已经更新了，我就是用git stash将修改的文件保存到缓存区，在checkout到master去pull了一次，然后我就忘记了切换到之前分支上git stash pop，在master上就git stash pop了，结果冲突了。在切换的时候出现needs merge的错误，然后谷歌了一下。。。
本地修改了东西git stash的时候出现 needs merge的情况，pull不了，stash不了，解决办法使用
git reset --mixed
git marge再revert，撤销revert的方法
git revert HEAD                  撤销前一次 commit
git revert HEAD^               撤销前前一次 commit
git revert commit （比如：fa042ce57ebbe5bb9c8db709f719cec2c58ee7ff）撤销指定的版本，撤销也会作为一次提交进行保存。
然后git status查看状态，就解除冲突了，不会影响到之前的任何更改
如果你想删除全部本地的修改
git reset --hard origin/master
同步远程分支到本地
git remote prune origin
```