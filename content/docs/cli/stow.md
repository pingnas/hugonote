# Stow

管理 dotfiles

## 安装
```sh
sudo apt update
sudo apt install stow
```

## 命令
```sh
# 在 ~/dotfiles 目录

# 将 nvim 文件夹内容链接到 ~/
stow nvim

# 模拟执行 只打印结果而不实际操作，用来检查路径对不对
stow -nv nvim

# 更新配置
stow -R nvim

# 撤销配置 清除软链接
stow -D nvim

# 输出每一条链接创建的具体路径（-vv 可以更详细）
stow -v nvim
```

## 示例
```txt
~/dotfiles/
└── tmux/                <-- 软件包名
    └── .config/         <-- 模拟home目录下的文件夹
        └── tmux/        <-- 模拟home目录下的文件夹
            └── tmux.conf <-- 实际的配置文件
```
```sh
cd ~/dotfiles
stow -v tmux
```

## 安装脚本
```sh
#!/bin/bash

list=(zsh git)

cd "$(dirname "$0")"

for i in "${list[@]}"; do
    stow -R -v "$i"
done
```