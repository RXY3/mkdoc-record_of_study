# 命令行环境
当使用shell进行工作时，有一些环境变量可以用来控制其行为，改善自己的工作流。
## 任务控制
### Ctrl-C —— 结束进程
Ctrl-C是一个特殊的键盘序列，它会发送一个SIGINT信号给当前进程。这个信号的默认行为是终止进程，但是进程可以选择忽略它。  
在shell中，Ctrl-C会终止当前正在运行的命令。
我们可以进行捕获这个信号，然后执行一些操作，比如清理工作，然后终止进程。
SIGTERM信号也可以用来终止进程，但是它的默认行为是终止进程，而不是忽略它，这更为通用，因为它可以被其他程序发送。语法为：
```bash
kill -s TERM <pid>
```

#### Ctrl-Z —— 暂停进程
Ctrl-Z是一个特殊的键盘序列，它会发送一个SIGTSTP信号给当前进程。这个信号的默认行为是暂停进程，但是进程可以选择忽略它。
在shell中，Ctrl-Z会暂停当前正在运行的命令。
我们可以使用fg或bg命令来恢复进程，其分别表示前台和后台。  
jobs命令可以列出当前正在运行的进程。可以使用 pid 引用这些任务（也可以用 pgrep 找出 pid）。
```bash
jobs
fg %1
bg %1
```
命令中的&后缀可以让命令在后台运行。  
让已经在运行的进程转到后台运行，您可以键入Ctrl-Z ，然后紧接着再输入bg。注意，后台的进程仍然是您的终端进程的子进程，一旦您关闭终端（会发送另外一个信号SIGHUP），这些后台的进程也会终止。  
您可以使用nohup命令来运行一个进程，这样即使关闭终端，进程也会继续运行。  
```bash
nohup <command> &
```
kill 不只是一个信号，它是一个命令，可以用来发送信号。语法为：
```bash
kill -s <signal> <pid>
```
KILL命令是唯一优先级比较高的信号，它可以终止任何进程，即使进程忽略了它。（即nohup）


## 终端多路复用
### tmux
像 tmux 这类的终端多路复用器可以允许我们基于面板和标签分割出多个终端窗口，这样您便可以同时与多个 shell 会话进行交互。  
tmux 会话可以在后台运行，这样即使您关闭了终端，会话也会继续运行。
其中有较多有用的快捷键可以进行操作  
- 会话 - 每个会话都是一个独立的工作区，其中包含一个或多个窗口
    - tmux 开始一个新的会话
    - tmux new -s NAME 以指定名称开始一个新的会话
    - tmux ls 列出当前所有会话
    - 在 tmux 中输入 <C-b> d ，将当前会话分离
    - tmux a 重新连接最后一个会话。您也可以通过 -t 来指定具体的会话

- 窗口 - 每个窗口都是一个独立的 shell 会话
    - <C-b> c 创建一个新窗口
    - <C-b> n 切换到下一个窗口
    - <C-b> p 切换到上一个窗口
    - <C-b> w 以菜单的形式显示所有窗口
    - <C-b> , 重命名当前窗口
    - <C-b> & 关闭当前窗口
    - <C-d> 关闭窗口

- 面板 - 每个面板都是一个独立的 shell 会话
  - <C-b> % 创建一个新的垂直面板
  - <C-b> " 创建一个新的水平面板
  - <C-b> o 切换到下一个面板
  - <C-b> ; 切换到上一个面板
  - <C-b> <方向> 切换到指定方向的面板，<方向> 指的是键盘上的方向键

[完整教程](https://www.hamvocke.com/blog/a-quick-and-easy-guide-to-tmux/)
包含screem的[教程](http://linuxcommand.org/lc3_adv_termmux.php)

## 别名/配置文件
您可以使用alias命令来创建别名。语法为：
```bash
alias <name>='<command>'
```
您可以使用unalias命令来删除别名。语法为：
```bash
unalias <name>
```
但是这往往只存在于当前会话中，如果您想要永久保存别名，您需要将其添加到您的shell配置文件中。
```bash
vim ~/.bashrc
```
每次运行是将会先进行此处文件的运行，所以您可以在此处添加任何您想要的命令，比如设置环境变量等。    
同样的，git,bash,ssh,vim等都可以通过点文件进行配置
因此，我们应该将这些配置文件放在一个git仓库中，这样我们就可以在任何地方使用我们的配置文件了。  
优势如下： 
- 安装简单: 如果您登录了一台新的设备，在这台设备上应用您的配置只需要几分钟的时间；
- 可移植性: 您的工具在任何地方都以相同的配置工作
- 同步: 在一处更新配置文件，可以同步到其他所有地方
- 变更追踪: 您可能要在整个程序员生涯中持续维护这些配置文件，而对于长期项目而言，版本历史是非常重要的


### ssh
ssh是一种安全的远程登录协议，它允许您在不安全的网络上安全地登录到远程系统。
1. 连接
通过ssh连接到远程系统，您需要知道远程系统的IP地址或者域名，以及您的用户名。语法为：
```bash
ssh <username>@<hostname>
```
hostname可以是IP地址或者域名，如果您使用的是默认的ssh端口（22），则可以省略端口号。
2. 密码与配置
ssh的配置文件位于~/.ssh/config，您可以在其中添加别名，以便于您可以通过别名来登录到远程系统。
```bash
Host <alias>
    HostName <hostname>
    User <username>
    Port <port>
    IdentityFile <path/to/private/key>
```
> 密钥生成
使用 ssh-keygen 命令可以生成一对密钥：
```bash
ssh-keygen -o -a 100 -t ed25519 -f ~/.ssh/id_ed25519
```
这会生成一对密钥，其中一个是私钥，另一个是公钥。私钥应该保持在本地，而公钥可以放在远程系统上。
> 基于密钥的认证机制
ssh 会查询 .ssh/authorized_keys 来确认那些用户可以被允许登录。您可以通过下面的命令将一个公钥拷贝到这里：
```bash
cat .ssh/id_ed25519.pub | ssh foobar@remote 'cat >> ~/.ssh/authorized_keys'
```


3. 文件复制
   
- ssh + tee :
tee命令会将标准输入的内容输出到标准输出，并且将其保存到文件中。语法为：
```bash
cat localfile | ssh remote_server tee serverfile
```
- scp
当需要拷贝大量的文件或目录时，使用scp 命令则更加方便，因为它可以方便的遍历相关路径。语法如下：
```bash
scp path/to/local_file remote_host:path/to/remote_file；
```
- rsync
它可以检测本地和远端的文件以防止重复拷贝。它还可以提供一些诸如符号连接、权限管理等精心打磨的功能。甚至还可以基于 --partial标记实现断点续传。rsync 的语法和scp类似；


作业：