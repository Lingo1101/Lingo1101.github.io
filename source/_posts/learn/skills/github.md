---
title: github
date: 2020-10-24 22:27:18
tags: git
categories: 学习笔记
---
## GitHub
1、**目的** ：托管代码！——repository库  
2、**Star**：收藏仓库(项目)  
3、**Fork**：克隆复制（独立个体）  
4、**Watch**：关注某人  
5、**创建网页**：(.html文件) 用户名.github.io+/仓库名.项目站点


# Github常用指令

## 提交文件
1.修改文件后提交修改到版本库：
>git add ./  
>git commit -m "描述"  
>git push

下载：
>git pull  

2.查看历史版本
```
git log # 显示最近到最远的提交
git reflog # 显示所有执行过的命令
```
3.回退到历史版本
```
# 回到上一个版本
git reset --hard HEAD^

# 回到上上一个版本
git reset --hard HEAD^^

# 回到上一个版本 (同上)
git reset --hard HEAD~1

# 回到制定版本
git reset --hard commit_id

```
## 删除文件
```
# 在工作区新建test文件
touch test
# 添加到暂存区
git add test
# 提交到分支
git commit -m "add test"

# 在本地删除test
rm test
# 工作区和版本库不一致
git status
# 确认删除
git rm test
# git add test 等价
git commit -m "remove test"


```

## 远程仓库
### 1.添加远程库
```
# 初始化本地目录为git仓库
git init
# 关联一个远程库
git remote add origin git@github.com:your_name/repo_name.git
git push --set-upstream origin master
# 本地同步远程仓库
git pull origin master
# 提交到远程仓库
git push origin master

```
### 2.克隆远程库
```
git clone git@github.com:your_name/repo_name.git
```
## 创建合并分支
### 1.创建分支
```
# 创建dev分支
git branch dev
# 切换分支
git checkout dev
# 查看当前分支
git branch
# 查看所有分支
git branch -a
```
### 2.合并分支
```
# 切换到主分支, 切换前要git commit
git checkout master
# 合并dev到当前分支
git merge dev
# 删除dev分支
git branch -d dev
```