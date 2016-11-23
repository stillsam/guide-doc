-f file Specify an alternative configuration file.  By default, tmux loads the system configuration file from `/etc/tmux.conf`, if present, then looks for a user configuration file at `~/.tmux.conf`.  The configuration file is a set of tmux commands which are executed in sequence when the server is first started.



### 常用按键
这里需要说明一点的是，tmux的任何指令，都包含一个前缀，也就是说，你按了前缀(一组按键，默认是Ctrl+b)以后，系统才知道你接下来的指令是发送给tmux的。
```bash
C-b ? 显示快捷键帮助
C-b C-o 调换窗口位置，类似与vim 里的C-w
C-b 空格键 采用下一个内置布局
C-b ! 把当前窗口变为新窗口
C-b " 模向分隔窗口
C-b % 纵向分隔窗口
C-b q 显示分隔窗口的编号
C-b o 跳到下一个分隔窗口
C-b 上下键 上一个及下一个分隔窗口
C-b C-方向键 调整分隔窗口大小
C-b c 创建新窗口
C-b 0~9 选择几号窗口
C-b c 创建新窗口
C-b n 选择下一个窗口
C-b l 切换到最后使用的窗口
C-b p 选择前一个窗口
C-b w 以菜单方式显示及选择窗口
C-b t 显示时钟
C-b ; 切换到最后一个使用的面板
C-b x 关闭面板
C-b & 关闭窗口
C-b s 以菜单方式显示和选择会话
C-b d 退出tumx，并保存当前会话，这时，tmux仍在后台运行，可以通过tmux attach进入 到指定的会话
```

### 配置
我们先来看一下几个配置，这些配置才是我离不开tmux的原因:-)。tmux的配置文件是`~/.tmux.conf`，这个文件可能不存在，你可以自己新建。下面开始配置，首先，有没有觉得tmux的前缀按起来太不方便了，ctrl与b键隔得太远，很多人把它映射成C+a，也就是在配置文件(`~/.tmux.conf`)中加入下面这条语句：

#### 设置前缀为Ctrl + a
`set -g prefix C-a`
与此同时，取消默认的前缀按键：

#### 解除Ctrl+b 与前缀的对应关系
`unbind C-b`
配置完以后，重启tmux起效，或者先按C+b，然后输入：，进入命令行模式，在命令行模式下输入：
`source-file ~/.tmux.conf`
你也可以跟我一样，在配置文件中加入下面这句话，以后改了只需要按前缀+r了。

##### 将r 设置为加载配置文件，并显示"reloaded!"信息
`bind r source-file ~/.tmux.conf \; display "Reloaded!"`

***
##### 6.5 将切换窗口设置成vim模式
```bash
bind-key k select-pane -U # up
bind-key j select-pane -D # down
bind-key h select-pane -L # left
bind-key l select-pane -R # right
```
上面的最后一条语句会更改C-a l的功能，我挺喜欢这个功能的，因为我们很时候都是在两个窗 口或这两个面板中切换，所以我又加入如下语句

`bind-key C-l select-window -l`
现在我的l键可不能随便按了，Ctrl+a l是切换面板，Ctrl+x Ctrl+l切换窗口，Ctrl+l清屏。

##### 6.6 复制模式copy-mode

前缀 [ 进入复制模式
按 space 开始复制，移动光标选择复制区域
按 Enter 复制并退出copy-mode。
将光标移动到指定位置，按 前缀 ] 粘贴
如果把tmux比作vim的话，那么我们大部分时间都是处于编辑模式，我们复制的时候可不可以像vim一样移动呢？只需要在配置文件中加入如下行即可。

`setw -g mode-keys vi` #copy-mode 将快捷键设置为vi 模式
##### 6.7 会话

C-x s 以菜单的方式查看并选择会话
C-x :new-session 新建一个会话
C-x d 退出并保存会话
终端运行 `tmux attach` 返回会话

##### 6.8 命名会话

`tmux new -s session`
`tmux new -s session -d` #在后台建立会话
`tmux ls` #列出会话
`tmux attach -t session` #进入某个会话
##### 6.9 使当前pane最大化

前缀 z tmux 1.8新特性，最大化当前所在面板
前缀 z 返回原来状态
##### 6.10 滚屏

`set-window-option -g mode-mouse on` # (setw其实是set-window-option的别名)
##### 6.11 用鼠标切换窗口/调节分屏大小

`setw -g mouse-resize-pane on` # 开启用鼠标拖动调节pane的大小（拖动位置是pane之间的分隔线）
`setw -g mouse-select-pane on` # 开启用鼠标点击pane来激活该pane
`setw -g mouse-select-window on` # 开启用鼠标点击来切换活动window（点击位置是状态栏的窗口名称）
`setw -g mode-mouse on` # 开启window/pane里面的鼠标支持（也即可以用鼠标滚轮回滚显示窗口内容，此时还可以用鼠标选取文本）
##### 6.12 保存Tmux会话

Tmux 会话功能它有一点不好，如果机器重启，那么 Tmux 会话就消失了，包括打开的各个窗口、窗格布局、以及其中跑的程序等所有东东。Tmux Resurrect 和 Tmux Continuum 这两个 Tmux 插件正是因此而生的。



