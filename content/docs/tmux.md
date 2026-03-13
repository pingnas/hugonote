# Tmux

一个终端复用器（terminal multiplexer）

## 参考

- [Tmux 使用教程 阮一峰](https://www.ruanyifeng.com/blog/2019/10/tmux.html)
- [最常用的快捷键和命令的 tmux 备忘单快速参考](https://wangchujiang.com/reference/docs/tmux.html)
- [tmux](https://github.com/tmux/tmux)

## 命令

> 新会话
```sh
# 创建一个新的会话
tmux
tmux new
tmux new-session


# 创建一个命名为name的新会话
tmux new -s name
```

> 显示所有会话
```sh
tmux ls
tmux list-sessions
```

> 连接会话
```sh
# 连接到上一个会话
tmux a
tmux at
tmux attach
tmux attach-session

# 连接到命名为name的对话
# 这里的name也可以是序号
tmux a -t myname
tmux at -t myname
tmux attach -t myname
tmux attach-session -t myname

```

> 中止会话
```sh
# 中止到命名为name的对话
tmux kill-ses -t name
tmux kill-session -t name

# 中止除当前之外的所有会话
tmux kill-ses -a

# 中止除命名为name之外的所有会话
tmux kill-sess -a -t name
```

> 没什么用的命令
```sh
# help
tmux info

# 显示配置
tmux show-options -g

# 重新加载配置
tmux source-file ~/.tmu­x.conf
```

> 复制模式
```sh
# 进入复制模式
Ctrl+b [ 

# 退出复制模式
q 
Esc

```