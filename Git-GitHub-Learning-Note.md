# Git
## 创建版本库
1. 在一个空文件夹中初始化一个Git仓库:  
`git init`

2. 添加文件到Git仓库，分两步：  
 * 将修改添加到暂存区（stage）：`git add <file>`   
 ![](Git-GitHub-File/0.jpg)

 * 把暂存区中的修改提交到当前分支，然后清空暂存区：`git commit -m "comment"`
 ![](Git-GitHub-File/1.jpg)

## 时光穿梭机
1. 查看当前仓库状态（被修改的文件、准备提交的修改）：  
`git status`

2. 查看具体修改了什么内容：
`git diff <file>`

## 版本回退
1. 显示从最近到当前版本（HEAD指针指向的版本）的提交日志：  
`git log`(简化版：`git log --pretty=oneline`)

2. 将工作区文件回退到Git仓库中以前的某个版本：  
`git reset --hard <version-id>`  
> Git在内部有一个指向当前版本的HEAD指针，当版本回退时，Git仅仅是把HEAD指针指向`<version-id>`所代表的版本，然后顺便更新工作区文件。

3. 错误回退，又找不到回退时的版本号时：  
 * 记录每一次命令：`git reflog`

## 管理修改
1. 查看工作区和版本库里最新版本的区别：  
`git diff HEAD -- <file>`

2. Git管理的是修改（一次add就是一次修改），`git commit`只会提交被添加进暂存区中的修改；没有`git add <file>`的修改不会被提交。

## 撤销修改
1. 让文件回到最近一次`git commit`或`git add`时的状态；仅能撤销工作区中尚未`git add/commit`的修改：    
`git checkout -- <file>`

2. 当错误的修改被添加到暂存区时：  
撤销暂存区中的修改，但保留工作区中的改动（相当于取消一次`git add <file>`操作），工作区中的改动保持最新的状态（不会强行回退到`git add <file>`时的状态）：`git reset HEAD <file>`

## 删除文件
1. 从版本库中删除文件：
`git rm <file>`

## 远程仓库（GitHub）
1. 创建SSH Key：  
`ssh-keygen -t rsa -C "email@me.com"`  
 - id_rsa  
 - id_rsa.pub

2. GitHub -> Account Setting -> SSH Keys -> Add SSH Key：  
 - Add title-field
 - Copy "id_rsa.pub" to key-field
 - Click "Add key"

3. 添加远程仓库 : GitHub -> Create a new repo  
 - Add repository-name-field
 - Click "Create Repository"

4. 将本地仓库关联到远程仓库：  
`git remote add <remote-repo-name> git@github.com:Github4Qiang/<repo-name>.git`

5. 第一次提交，Git把本地的master分支内容推送到远程仓库上，并且将本地的master分支和远程master分支关联起来：  
`git push -u <remote-repo-name> master`

6. 以后的提交：  
`git push <remote-repo-name> master`
