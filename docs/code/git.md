# GIT
## git 是什么
git 是一个分布式版本控制系统，可以有效、高速的处理从很小到非常大的项目版本管理。
## git 的优势
- 适合分布式开发，不依赖网络
- 本地操作速度快
- 适合多人协作
- 适合开源项目
- 适合大项目
- 适合敏捷开发
- 适合非线性开发

## git 的安装
- windows
> 下载地址：https://git-scm.com/download/win
- linux
> ubuntu: sudo apt-get install git
- mac
> brew install git
## github
- github 是什么
> github 是一个面向开源及私有软件项目的托管平台，因为只支持 git 作为唯一的版本库格式进行托管，故名 github。
- github 的优势
> - 只支持 git
> - 完整协议支持
> - 在线文件编辑
## git&github学习方式
由于笔者自身水平的原因，在此无法进行过多的讲解，所以推荐大家通过以下方式进行学习：
1. [git 官方文档](https://git-scm.com/docs)
2. [git_pro](https://github.com/anzhihe/Free-Git-Books/blob/master/book/Professional%20Git.pdf)
3. [图形化学习](https://learngitbranching.js.org/?locale=zh_CN)
### 图形化学习笔记
#### git commit
> Git 仓库中的提交记录保存的是你的目录下所有文件的快照，就像是把整个目录复制，然后再粘贴一样，但比复制粘贴优雅许多！    
> Git 希望提交记录尽可能地轻量，因此在你每次进行提交时，它并不会盲目地复制整个目录。条件允许的情况下，它会将当前版本与仓库中的上一个版本进行对比，并把所有的差异打包到一起作为一个提交记录。
> git commit -m "message"
> git commit -a -m "message" 会自动把所有已经跟踪过的文件暂存起来一并提交，从而跳过 git add 步骤
> git commit --amend 用于修改最后一次提交记录
> 
#### git branch
移动：
> git branch -f [branch-name] [commit-hash] 强制移动分支指针
> git reset --hard [commit-hash] 强制移动 HEAD 指针
> git branch [branch-name] 创建分支
> git branch -d [branch-name] 删除分支
> git branch -D [branch-name] 强制删除分支
> git branch -m [branch-name] 重命名分支
> git branch -a 查看所有分支
> git branch -v 查看所有分支的最后一次提交
> git branch --merged 查看已经合并到当前分支的分支
> git branch --no-merged 查看尚未合并到当前分支的分支
> git branch -vv 查看本地分支关联的远程分支
> git branch -u [remote-branch-name] 设置本地分支关联的远程分支
> git branch -u [remote-name]/[remote-branch-name] 设置本地分支关联的远程分支
> git branch -u --unset 取消本地分支关联的远程分支
> git branch -u [remote-name]/[remote-branch-name] [local-branch-name] 设置本地分支关联的远程分支
> git branch -f [branch-name] [commit-hash] 强制移动分支指针
#### git merge
> 合并分支
> git merge [branch-name]  
> git merge --abort 取消合并  
> git merge --continue 继续合并  
#### git rebase
线性合并
> git rebase [branch-name]
> git rebase --abort 取消合并
> git rebase --continue 继续合并
> git rebase -i [commit-hash] 交互式合并
#### git head
> HEAD 是一个指向你正在工作中的本地分支的指针（译注：它也是一个指向你上一次提交所在分支的指针）。  
> HEAD 总是指向当前分支上最近一次提交记录。大多数修改提交树的 Git 命令都是从改变 HEAD 的指向开始的。  
> 
#### 相对引用
> 相对引用是一种快捷方式，允许你轻松地在不同的分支之间切换。  
> 通过指定提交记录哈希值的方式在 Git 中移动不太方便。在实际应用时，并没有漂亮的可视化提交树供你参考，所以你就不得不用 git log 来查查看提交记录的哈希值。  
> 相对引用非常给力，这里我介绍两个简单的用法： 
1. 使用 ^ 向上移动 1 个提交记录
2. 使用 ~<num> 向上移动多个提交记录，如 ~3

#### git reset & git revert
> git reset 用于移动分支上的 HEAD 指针，git revert 用于撤销提交记录。  
> git reset 通过把分支记录回退几个提交记录来实现撤销改动。你可以将这想象成“改写历史”。git reset 向上移动分支，原来指向的提交记录就跟从来没有提交过一样。  
> 这种“改写历史”的方法对大家一起使用的远程分支是无效的哦！  
> git revert 通过在分支上新建一个提交记录来撤销更改。这个新提交记录的引入会撤销前面的提交记录。
#### git cherry-pick
> git cherry-pick 用于从一个分支中把一个或多个提交的修改复制到另一个分支中。  
> git cherry-pick [commit-hash](可以加多个节点)  
> 直接拿取多个节点的复制，按照顺序放置于HEAD下方

#### git rebase -i(interactive)
> git rebase [commit-hash] 用于将指定的提交记录移动到当前分支的最后面
> git rebase [commit-hash] [branch-name] 用于将指定的提交记录移动到指定分支的最后面(com)
> git rebase -i [commit-hash]
> 同样的可以进行多重节点操作，即可以进行多个节点的合并（删除），也可以进行多个节点的拿取，并按照自己需要的顺序进行排列
#### 本地栈式提交
> git stash 用于临时保存和隐藏你的工作目录中未完成的修改。当你想要切换分支但是又不想提交时，这一特性就显得非常有用。
#### git checkout
> git checkout [commit-hash] 用于切换到指定的提交记录
> git checkout [branch-name] 用于切换到指定的分支
> git checkout [branch-name] [相对位移] 用于切换到指定的创建分支
> git checkout -b [branch-name] 用于创建并切换到指定的分支
> git checkout -b [branch-name] [commit-hash] 用于创建并切换到指定的分支并指定提交记录
> git checkout -b [branch-name] [remote-name]/[remote-branch-name] 用于创建并切换到指定的分支
> git checkout -b [branch-name] [remote-name]/[remote-branch-name] 用于创建并切换到指定的分支
#### git Tag
> git tag 用于创建标签
> git tag [tag-name] [commit-hash]

#### git describe
Git Describe 能帮你在提交历史中移动了多次以后找到方向；当你用 git bisect（一个查找产生 Bug 的提交记录的指令）找到某个提交记录时，或者是当你坐在你那刚刚度假回来的同事的电脑前时， 可能会用到这个命令。
> git describe [commit-hash] 用于查看指定提交记录的描述
> git describe [commit-hash] --tags 用于查看指定提交记录的描述


### 远程git操作
#### git clone
> git clone [remote-url] 用于克隆远程仓库
> git clone [remote-url] [local-dir] 用于克隆远程仓库到指定目录
> git clone [remote-url] -b [branch-name] 用于克隆远程仓库的指定分支
#### git fetch
> git fetch [remote-name] 用于从远程仓库中获取数据
> git fetch [remote-name] [branch-name] 用于从远程仓库中获取指定分支的数据
> git fetch [remote-name] [branch-name] [local-branch-name] 用于从远程仓库中获取指定分支的数据并存储到本地分支  
请注意，git fetch 命令只是将远程仓库中的数据拉取到本地仓库，并不会自动合并到当前分支。在拉取完远程仓库的数据之后，你需要手动将远程分支合并到本地分支中。  
相当于知识一个下载的操作 
#### o/main
什么是 o/main？
> o/main 是一个特殊的本地分支，它代表了远程仓库的主分支。
> git remote show [remote-name] 用于查看远程仓库的详细信息
> git remote show [remote-name] -n 用于查看远程仓库的详细信息

#### git pull
git pull是git fetch和git merge的组合
> git pull [remote-name] [branch-name] 用于从远程仓库中获取指定分支的数据并合并到当前分支

#### 模拟团队协作

#### git push
git push 用于将本地分支的数据推送到远程仓库
origin：远程仓库的默认名称
> git push [remote-name] 用于将本地分支的数据推送到远程仓库
> git push [remote-name] [branch-name] 用于将本地分支的数据推送到远程仓库
> git push [remote-name] [local-branch-name]:[remote-branch-name] 用于将本地分支的数据推送到远程仓库的指定分支
> git push -u [remote-name] [local-branch-name] 用于将本地分支的数据推送到远程仓库的指定分支，并将本地分支与远程分支关联起来
git push的失效：
当你在本地创建了一个新的分支并且推送到远程仓库之后，你会发现 git push 命令失效了。这是因为 git push 命令只会将本地分支推送到远程仓库中存在的分支。如果你想要将本地分支推送到远程仓库中不存在的分支，你需要使用 git push -u 命令。

#### git pull --rebase
> git pull --rebase [remote-name] [branch-name] 用于从远程仓库中获取指定分支的数据并合并到当前分支
> git pull --rebase 用于从远程仓库中获取数据并合并到当前分支
具体图像示例：



#### 远程服务器拒绝!(Remote Rejected)
如果你是在一个大的合作团队中工作, 很可能是main被锁定了, 需要一些Pull Request流程来合并修改。如果你直接提交(commit)到本地main, 然后试图推送(push)修改, 你将会收到这样类似的信息:

> ! [远程服务器拒绝] main -> main (TF402455: 不允许推送(push)这个分支; 你必须使用pull request来更新这个分支.)
原因：
远程服务器拒绝直接推送(push)提交到main, 因为策略配置要求 pull requests 来提交更新.

你应该按照流程,新建一个分支, 推送(push)这个分支并申请pull request,但是你忘记并直接提交给了main.现在你卡住并且无法推送你的更新.  

解决方案：
1. 你可以使用 git pull --rebase 命令来更新你的本地main分支, 但是这样会导致你的提交历史变得混乱, 因为你的提交历史将会被重写.
2. 你可以使用 git pull 命令来更新你的本地main分支, 这样会保留你的提交历史, 但是会产生一个合并提交, 这样会导致你的提交历史变得混乱.
3. 你可以使用 git reset --hard 命令来重置你的本地main分支, 这样会丢失你的提交历史, 但是你可以重新提交你的修改, 这样会导致你的提交历史变得混乱.
4. 新建一个分支feature, 推送到远程服务器. 然后reset你的main分支和远程服务器保持一致, 否则下次你pull并且他人的提交和你冲突的时候就会有问题.


#### git push 的参数
> git push origin main

把这个命令翻译过来就是：

切到本地仓库中的“main”分支，获取所有的提交，再到远程仓库“origin”中找到“main”分支，将远程仓库中没有的提交记录都添加上去，搞定之后告诉我。

> git push origin main:main

把这个命令翻译过来就是：

切到本地仓库中的“main”分支，获取所有的提交，再到远程仓库“origin”中找到“main”分支，将本地仓库中的提交记录都添加上去，搞定之后告诉我。

<place> 参数详解
git push origin <source>:<destination>
source: 本地分支
destination: 远程分支
如果你想要将本地分支推送到远程仓库中不存在的分支，你需要使用 git push -u 命令。

#### git fetch 的参数
git fetch origin foo

把这个命令翻译过来就是：

到远程仓库“origin”中找到“foo”分支，获取所有的提交，搞定之后告诉我。

git fetch origin foo:bar

把这个命令翻译过来就是：

到远程仓库“origin”中找到“foo”分支，获取所有的提交，再到本地仓库中找到“bar”分支，将远程仓库中没有的提交记录都添加上去，搞定之后告诉我。

如果push 空分支，会删除远程分支

#### git pull 的参数

git pull origin foo 相当于：

git fetch origin foo; git merge o/foo

还有...

git pull origin bar~1:bugFix 相当于：

git fetch origin bar~1:bugFix; git merge bugFix





