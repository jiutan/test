# git 操作
### 2. git 身份标识
```c
git config --global user.name"用户名"
git config --global user.email 邮箱
```

### 1. git 初始化
``` python
git init
```

### 2. git 绑定远程仓库
```c
git remote add <远程仓库平台名称(可以用orgin)> <远程仓库地址>
```
### 3. git 添加到缓存区
```c
git add *
```
### 4. git 提交一版并备注
```c
git commit -m '添加备注'
```
### 5. 推送本地代码至远程库
```c
git push <远程仓库平台名称(可以用orgin)> <代码分支（master）>
```