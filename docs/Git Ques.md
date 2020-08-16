# Git 常见问题解决方法

## 推送到 GitHub 报错

fatal: remote origin already exists. 报错远程起源已经存在

先移除当前远程库，再重新关联远程库

```
$ git remote rm origin
$ git remote add origin git@github.com:dreamwhigh/test.git
```

## git fetch

git pull：从远程获取最新版本并merge到本地；

git fetch：从远程获取最新版本到本地，不会自动merge。

```
git fetch origin master
//比较本地的master分支和origin/master分支的差别
git log -p master..origin/master 
//合并
git merge origin/master
```

更佳的处理方法是：

```
git branch dev
//将远程的最新版本同步到本地的 dev 分支上
git fetch origin master:dev
//比较本地 master 分支与 本地 dev 分支的差别
git diff dev
//合并
git merge dev
git branch -d dev
```

