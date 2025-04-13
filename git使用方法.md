# git 操作
### 1. git 身份标识
```c
git config --global user.name"用户名"
git config --global user.email 邮箱
```

### 2. git 初始化
``` python
git init
```

### 3. git 绑定远程仓库
```c
git remote add <远程仓库平台名称(可以用orgin)> <远程仓库地址>
```
### 4. git 缓存区操作
```c
git add .     				// 添加目录下所有的文件夹
git add [file1] [file2] ... // 添加指定文件到暂存区
git add [dir]  				// 添加指定目录到暂存区，包括子目录
git add -p					// 添加每个变化前，都会要求确认

git rm [file1] [file2] ...	// 删除工作区文件，并且将这次删除放入暂存区
git mv [file-original] [file-renamed] // 改名文件，并且将这个改名放入暂存区
```
### 5. git 提交一版并备注
```c
git commit -m '添加备注'	// 提交暂存区到仓库区
git commit [file1] [file2] ... -m [message]	// 提交暂存区的指定文件到仓库区
git commit -v				// 提交时显示所有diff信息
```
### 6. git 查看当前库的信息
```c
git status				// 查看当前版本状态（是否修改）
git log --stat			// 显示commit历史，以及每次commit发生变更的文件
git log -S [keyword]	// 搜索提交历史，根据关键词
git log --follow [file]	// 显示某个文件的版本历史，包括文件改名
git log -p [file]		// 显示指定文件相关的每一次diff

git diff				// 显示暂存区和工作区的差异
git diff --cached [file]// 显示暂存区和上一个commit的差异
git diff HEAD			// 显示工作区与当前分支最新commit之间的差异

git reflog				// 显示当前分支的最近几次提交
```
### 7. git 分支
```c
git branch					// 列出所有本地分支
git branch -r				// 列出所有远程分支
git branch -a				// 列出所有本地分支和远程分支
git branch [branch-name]	// 新建一个分支，但依然停留在当前分支

git checkout -b [branch]	// 新建一个分支，并切换到该分支
git checkout [branch-name]	// 切换到指定分支，并更新工作区
    
git branch [branch] [commit]// 新建一个分支，指向指定commit
git checkout -				// 切换到上一个分支
git merge [branch]			// 合并指定分支到当前分支
git cherry-pick [commit] 	// 选择一个commit，合并进当前分支
git br -v					// 查看各个分支最后提交信息

git branch -d [branch-name]	// 删除分支
// 删除远程分支
git push origin --delete [branch-name]	
git branch -dr [remote/branch]			

git branch -m master main  	// 将本地的 master 分支重命名为 main

```
### 8. git 回退（ hash可以在git log中看到 ）
```c
1.commit前，没提交时 回退
git reset --hard <commit-hash> 	
// 丢弃工作区的所有改动以及暂存区的新增文件，并将指针移动到上一个提交版本，即把所有文件恢复至上一个提交点。【回退整个工程】
git checkout <commit-hash> -- <file-path>
// 【单个文件回退】仅需要回退某个文件到上次提交点的话
git reset HEAD <file-name>
// 把新增文件从暂存区移出来（还没有commit）

2.commit 后回退，提交后 回退
git revert HEAD	// 回退到上个版本，会创建一个新的提交，将上一次提交的改动反转回去
git reset --hard <commit-hash>	// 回退到指定版本并放弃后续修改【丢弃指定版本之后的所有提交，并将指针移动到指定版本】
git reset --soft <commit-hash>	// 回退到指定版本但保留工作区【我们本地的代码不会跟着回退，我们可以基于目前的代码改完后再次提交。】

3.push 后回退
第一步：修复本地内容
第二步：推送至远程
git push <origin> <分支名>
git push -f <origin> <分支名>		// 强制推送修改，这可能会导致他人的工作丢失

4.恢复误删分支
第一步：git reflog		// 查看所有的提交历史，找到被删除的分支的hash
第二步：git branch <branch-name> <commit-hash>	// 恢复的分支名称

```


### 9. 推送本地代码至远程库
```c
git push <远程仓库平台名称(可以用orgin)> <branch>
git push [remote] [branch]		// 上传本地指定分支到远程仓库

git push [remote] --force		// 强行推送当前分支到远程仓库，即使有冲突
git push [remote] --all			// 推送所有分支到远程仓库

```

### 10.远程仓库拉取代码
```c
git remote -v				// 显示所有远程仓库
git fetch [remote]			// 下载远程仓库的所有变动
git remote show [remote]	// 显示某个远程仓库的信息

git pull [remote] [branch]	// 取回远程仓库的变化，并与本地分支合并
```