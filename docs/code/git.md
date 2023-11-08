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
#### git branch
> 分支是一种轻量级的可移动指针，它指向某个提交记录。  
切换：git checkout [branch-name]  
git checkout -b [branch-name] 创建并切换到新分支  
git checkout -d [branch-name] 删除分支
git checkout -f [branch-name] [某一节点或相对位置]强制切换分支
#### git merge
> 合并分支
> git merge [branch-name]  
> git merge --abort 取消合并  
> git merge --continue 继续合并  
#### git rebase
线性合并
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
> git rebase -i [commit-hash]
> 同样的可以进行多重节点操作，即可以进行多个节点的合并（删除），也可以进行多个节点的拿取，并按照自己需要的顺序进行排列
#### 本地栈式提交
> git stash 用于临时保存和隐藏你的工作目录中未完成的修改。当你想要切换分支但是又不想提交时，这一特性就显得非常有用。

#### git Tag
TODO



