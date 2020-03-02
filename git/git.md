### 初始化本地仓库
```shell
git init
```
### 追踪文件/将已修改的被追踪的文件放入暂存区
```shell
git add filepath
```
### 仓库状态
```shell
git status
git status -s
```
### 提交暂存区内容至本地仓库
```shell
git commit -m ""
git commit -am ""
git commit -ament 提交完了才发现漏掉了几个文件没有添加，或者提交信息写错了。 此时，可以运行带有 --amend 选项的提交命令尝试重新提交
```
### 删除文件/放弃追踪
```shell
git rm file
git rm -f file 删除之前修改过并且已经放到暂存区域的话，则必须要用强制删除选项 -f
git rm --cached file 从仓库中移除并放弃追踪文件(文件不会从本地磁盘中删除)
```
### 移动文件/文件重命名
```shell
git mv file file_m
```
### 重置
```shell
git reset HEAD^ [file]
git reset HEAD [file]  将HEAD区里HEAD版本给恢复到暂存区
git restore file 重置file为修改前

git reset commitID [file] 将某次提交Id版本给恢复到暂存区(然后可以使用`git checkout file`恢复指定文件)

reset --hard 重置stage区和工作目录, 没有commit的修改会被全部擦掉
  要放弃目前本地的所有改变或者抛弃目标节点后的所有commit時<br>
reset --soft 保留工作目录，并把重置 HEAD 所带来的新的差异放进暂存区
  使用reset--soft后，原节点和reset节点之间的【差异变更集】会放入index暂存区中,我们可以直接执行 git commit 將 index暂存区中的內容提交至 repository 中<br>
reset 如果不加参数，那么默认使用--mixed参数，它的行为是：保留工作目录，并且清空暂存区。
  移除所有Index暂存区中准备要提交的文件，然后所有原节点和reset节点之间差异会返回工作目录，假如有个没必要的文件的话就可以直接删除了，再commit上去就OK了。
```
### checkout file与restore file
```shell
git checkout file 从暂存区中拉取文件还原,常配合着reset使用
同
git restore file
与
git add 的功能相反
```

### 仓库日志
```shell
git log
git log --oneline
git log (--oneline) --graph
git log (--oneline) --reverse
git log --oneline --author=hacking-will
git log --oneline --after={2019-12-15}
git log --oneline --before={3.weeks.ago}

git log -p -2  显示最近两次提交的详细信息

git log --oneline --decorate 查看各个分支当前所指的对象

git log --oneline --decorate --graph --all 输出你的提交历史、各个分支的指向以及项目的分支分叉情况
```
### 分支管理
```shell
git branch 显示分支列表
git branch -vv
git branch branchname 创建新分支
git branch -d branchname 删除分支
git push --delete [origin] branchname 删除远程分支

git checkout branchname 切换分支
git cheackout -b branchname 创建新分支并切换

git merge (branchname) 合并分支

git mergetool 合并时冲突解决工具
```
### 标签
```shell
git tag 显示标签列表
git tag tagname 创建新标签
git show tagname 显示标签信息
git tag -a tagname
// 列出本地标签
git tag --list
// 创建标签
git tag -a v1.0.1 -m "创建v1.0.1"
// 推送本地标签到远程库
git push origin v1.0.1
// 删除本地标签
git tag -d v1.0.1
// 删除远程标签
git push origin  :refs/tags/v1.0.1

```
### 远程仓库(github)
```shell
git remote 查看当前的远程库
git remote -v 会显示需要读写远程仓库使用的 Git 保存的简写与其对应的 URL
git remote add [shortname] [url] 添加远程库
git push -u [shortname] [branchname] 推送到远程仓库

git pull
git fetch 提取远程仓库 该命令执行完后需要执行git merge 远程分支到你所在的分支
```
注意[pull与fetch两者的区别](https://blog.csdn.net/weixin_41975655/article/details/82887273)：
> git pull看起来像git fetch+get merge，但是根据commit ID来看的话，他们实际的实现原理是不一样的。<br>
> 多数时候这是没问题的，但一旦代码有问题，你很难找到出错的地方<br>
> 不要用git pull，用git fetch和git merge代替它。

### git别名

```shell
git config --global alias.st status
git config --global alias.br branch
git config --global alias.co checkout 
git config --global alias.unstage 'reset HEAD --'
git config --global alias.last 'log -1 HEAD'

Git 只是简单地将别名替换为对应的命令。 然而，你可能想要执行外部命令，而不是一个 Git 子命令。 如果是那样的话，可以在命令前面加入 ! 符号。 如果你自己要写一些与 Git 仓库协作的工具的话，那会很有用。 我们现在演示将 git visual 定义为 gitk 的别名：

$ git config --global alias.visual '!gitk'
```



### SSH Key
`$ ssh-keygen -t rsa -C "youremail@example.com"`
后面的your_email@youremail.com 改为你在 Github 上注册的邮箱，之后会要求确认路径和输入密码，我们这使用默认的一路回车就行。<br>
成功的话会在 ~/ 下生成 .ssh 文件夹，进去，打开 id_rsa.pub，复制里面的 key。<br>
回到 github 上，进入 Account => Settings（账户配置）。左边选择 SSH and GPG keys，然后点击 New SSH key 按钮,title 设置标题，可以随便填，粘贴在你电脑上生成的 key。



