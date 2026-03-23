# Tmux

一个终端复用器（terminal multiplexer）

## 参考

- [Tmux 使用教程 阮一峰](https://www.ruanyifeng.com/blog/2019/10/tmux.html)
- [最常用的快捷键和命令的 tmux 备忘单快速参考](https://wangchujiang.com/reference/docs/tmux.html)
- [tmux仓库](https://github.com/tmux/tmux)
- [.tmux配置](https://github.com/gpakosz/.tmux)

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

# 立即关闭tmux服务器并关闭所有打开的tmux窗口
tmux kill-server
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
```txt
# 进入复制模式
Ctrl+b [ 

# 退出复制模式
q 
Esc

```

## 快捷建

> 列出所有快捷方式
```sh
Ctrl+b ?
```

> 后台运行会话，从会话中分离
```sh
Ctrl+b d
```

> 显示所有会话
```sh
Ctrl+b s
```

> 重命名会话
```sh
Ctrl+b $
```

>  会话切换
```txt
# 上一个
Ctrl + b (
# 下一个
Ctrl + b )
```

> 窗口分割窗格
```txt
# 上下
Ctrl+b "

#  左右
Ctrl+b %
```

> 窗格 -> 窗口
```sh
Ctrl+b !
```

> 关闭窗格
```sh
Ctrl+b x
```

> 导航窗格
```txt
Ctrl+b <Arrow>
```

> 窗格布局切换
```txt
Ctrl+b <Space>
```

> 窗格移动位置
```txt
# 往左移
Ctrl+b {

# 往右移
Ctrl+b }
```

> 转到下一个窗格
```sh
Ctrl+b o
```

> 切换全屏
```sh
Ctrl+b z
```

> 切换最后一个窗格
```sh
Ctrl+b ;
```

> 显示号码
```sh
Ctrl+b q
```

> 转到 # 窗格
```sh
Ctrl+b q 0...9
```

> 创建窗口
```sh
Ctrl+b c
```

> 窗口切换
```sh
# 上一个
Ctrl+b p

# 下一个
Ctrl+b n
```

> 列表窗口
```sh
Ctrl+b w
```

> 重命名窗口
```sh
Ctrl+b ,
```

> 查找窗口
```sh
Ctrl+b f
```

> 最后一个窗口
```sh
Ctrl+b l
```

> 移动窗口
```sh
Ctrl+b .
```

> 关闭窗口
```sh
Ctrl+b &
```

> 转到#窗口
```sh
Ctrl+b 0...9
```

## 命令模式

> 进入命令模式
```sh
Ctrl+b :
```


## .tmux(oh my tmux)

在该配置中，你可以使用双前缀键（Prefix）：`Ctrl + b` 或 **`Ctrl + a`**。

  - `<prefix>` 这意味着你必须按 <kbd>Ctrl</kbd> + <kbd>a</kbd> 或 <kbd>Ctrl</kbd> + <kbd>b</kbd>
  - `<prefix> c` 意思是您必须按 <kbd>Ctrl</kbd> + <kbd>a</kbd> 或 <kbd>Ctrl</kbd> + <kbd>b</kbd> 后跟 <kbd>c</kbd>
  - `<prefix> C-c` 意思是您必须按 <kbd>Ctrl</kbd> + <kbd>a</kbd> 或 <kbd>Ctrl</kbd> + <kbd>b</kbd> 后跟 <kbd>Ctrl</kbd> + <kbd>c</kbd>

快捷键：

```sh
# 打开自定义文件副本
<prefix> e 

# 重新加载配置
<prefix> r 

# 将当前窗格垂直分割
<prefix> - 

# 将当前窗格水平分割
<prefix> _ 

# 窗口导航
<prefix> h, `<prefix> j`, `<prefix> k`, `<prefix> l` 

# 窗口改大小
<prefix> H, `<prefix> J`, `<prefix> K`, `<prefix> L` 

# 交换窗格
<prefix> <, `<prefix> >` 

# 将当前窗格最大化为一个新窗口
<prefix> + 

# 切换鼠标模式的开启或关闭
<prefix> m 
```


## 安装 (wsl)
```sh
#!/bin/bash
set -e

ARCH=$(uname -m)
case "$ARCH" in
    x86_64)         BIN_ARCH="x86_64" ;;
    aarch64|arm64)  BIN_ARCH="arm64" ;;
    *) echo "❌ 架构不支持: $ARCH"; exit 1 ;;
esac

echo "🔍 正在搜索最新版 Tmux..."
URL_LATEST="https://github.com/tmux/tmux-builds/releases/latest"
REAL_URL=$(curl -Ls -o /dev/null -w %{url_effective} "$URL_LATEST")
TAG=$(basename "$REAL_URL")
VERSION=${TAG#v} 

FILE="tmux-${VERSION}-linux-${BIN_ARCH}.tar.gz"
URL="https://github.com/tmux/tmux-builds/releases/download/${TAG}/${FILE}"

echo "📥 正在下载 $FILE 到当前目录..."
curl -L -O "$URL"

echo "📦 正在安装并自动清理..."

tar -xzf "$FILE" tmux

sudo install -m 755 tmux /usr/local/bin/tmux

rm -f "$FILE" tmux

echo "✅ tmux 安装完成。"
tmux -V
```
 