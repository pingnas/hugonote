---
title: "WezTerm 跨平台终端模拟器"
---

# WezTerm
一个功能强大的跨平台终端模拟器和多路复用器

## 参考

- [wezterm docs](https://wezterm.org/)
- [wezterm仓库](https://github.com/wezterm/wezterm)
- [wezterm-config配置](https://github.com/KevinSilvester/wezterm-config)

## win使用

> 安装
```sh
scoop install wezterm
reg import "C:\Users\xxx\scoop\apps\wezterm\current\install-context.reg"

# 终端启动
wezterm-gui
```

> `wezterm-config`常用键

```sh
# 复制
Ctrl+Shift+c 

# 粘贴
Ctrl+Shift+v

# 查找文本
Alt+f 

# 打开 URL
Alt+Ctrl+u

# 激活命令面板
F2 

# 显示启动器 (Launcher)
F3

# 切换全屏
F11

# 显示调试面板
F12

# 新建默认标签页
Alt+t

# 新建 WSL (Ubuntu) 标签页
Alt+Ctrl+t

# 关闭当前标签页
Alt+Ctrl+w

# 重命名当前标签页
Alt+0

# 切换上一个
Alt+]

# 下一个标签页
Alt+[

# 向左移动标签页
Alt+Ctrl+[ 

# 向右移动标签页
Alt+Ctrl+]

# 垂直拆分
Alt+\ 

# 水平拆分分栏
Alt+Ctrl+\

# 关闭当前分栏
Alt+w

# 分栏缩放 (Zoom)
Alt+Enter

# 使用 HJKL 方向切换分栏焦点
Alt+Ctrl+h/j/k/l

# 向上滚动 5 行
Alt+u

# 向下滚动 5 行
Alt+d

# 随机切换背景
Alt+/ 

# 模糊搜索背景
Alt+Ctrl+/

# 循环切换 下一个 / 上一个背景
Alt+,
Alt+.


```
