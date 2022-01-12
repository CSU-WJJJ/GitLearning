git branch xxx 创建分支xxx

git checkout xxx 切换到分支xxx

git checkout -b xxx 创建并切换到分支xxx

git merge xxx 将xxx分支合并到当前分支

git rebase xxx同上

**具体区别还没搞懂**

如何在提交树上移动

HEAD 是一个对当前检出记录的符号引用 —— 也就是指向你正在其基础上进行工作的提交记录。

HEAD 总是指向当前分支上最近一次提交记录。大多数修改提交树的 Git 命令都是从改变 HEAD 的指向开始的。

git checkout xxx 切换到分支xxx（也改变了HEAD指向）

git checkout xxx^ 切换到分支xxx的父节点

git checkout HEAD~x 向上走x步

git branch -f main HEAD~3 将main分支强制指向HEAD向上走三步的提交

**撤销变更的两种方法**

`git reset` 通过把当前分支记录回退几个提交记录来实现撤销改动。你可以将这想象成“改写历史”。`git reset` 向上移动分支，原来指向的提交记录就跟从来没有提交过一样。

虽然在你的本地分支中使用 git reset 很方便，但是这种“改写历史”的方法对大家一起使用的远程分支是无效的哦！

`git revert` 通过把当前分支在我们要撤销的提交记录后面增加一个新提交，使得新提交记录引入了更改，这些更改刚好是用来撤销原先的提交的，`revert` 之后就可以把你的更改推送到远程仓库与别人分享啦。

**远程仓库**

`git fetch` 完成了仅有的但是很重要的两步:

- 从远程仓库下载本地仓库中缺失的提交记录
- 更新远程分支指针(如 `o/master`)

但是：`git fetch`并不会改变你本地仓库的状态。它不会更新你的 `master` 分支，也不会修改你磁盘上的文件，可以将 `git fetch`的理解为单纯的下载操作。

git pull = git fetch + git merge

git pull --rebase = git fetch + git rebase



