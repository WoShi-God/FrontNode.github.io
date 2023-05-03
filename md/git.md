# Git 上传下载操作
>先获取一个仓库，便于上传获取时候要密码
# 1.git clone 仓库地址（空仓库也行）

>上传,直接在获取仓库文件夹里面打开git
```
git init

git add  文件名/文件夹名

git commit -m "注释"    （注释必须写）

git push   上传github库
```
# 2.git 添加和修改远程仓库地址

```
git remote add origin 仓库地址
```
>查看仓库地址
```
git remote -v
```
>直接修改仓库地址
```
git remote set-url origin 仓库地址
```
# 3.清理本地的 git 缓存
```
git rm -r --cached .
```
# 4.分支
>查看远程/本地分支
```
git branch -r

git branch
```
>创建新分支
```
git branch 新分支名称
```
>切换分支
```
git checkout 分支名称
```
>删除分支
```
git branch -d 分支名称
```
>然后把dev分支的代码合并到master上
```
git merge 分支名称
```
>查看状态
```
git status
```
