---
title: "eza ls的现代替代方案"
---

# eza
ls 的现代替代方案

## 资料
- [eza](https://github.com/eza-community/eza)

## 使用

### 显示选项
 

- **-1**, **--oneline**: 每行显示一个条目
- **-G**, **--grid**: 以网格形式显示条目（默认）
- **-l**, **--long**: 显示扩展详细信息和属性
- **-R**, **--recurse**: 递归到目录
- **-T**, **--tree**: 以树状结构递归遍历目录。
- **-x**, **--across**: 横向排序，而不是纵向排序
- **-F**, **--classify=(when)**: 按文件名显示类型指示器 (always, auto, never)
- **--colo[u]r=(when)**: 何时使用终端颜色 (always, auto, never)
- **--colo[u]r-scale=(field)**: 高亮显示`field` distinctly(all, age, size)的各个级别
- **--color-scale-mode=(mode)**: 在 --color-scale 中使用渐变色或固定颜色。有效选项为 `fixed` or `gradient`
- **--icons=(when)**: 何时显示图标 (always, auto, never)
- **--hyperlink**: 将条目显示为超链接
- **--absolute=(mode)**: 显示条目的绝对路径 (on, follow, off)
- **-w**, **--width=(columns)**: 以列为单位设置屏幕宽度
 

### 筛选选项
 

- **-a**, **--all**: 显示隐藏文件和“点”文件
- **-d**, **--treat-dirs-as-files**: 像列出普通文件一样列出目录
- **-L**, **--level=(depth)**: 限制递归深度
- **-r**, **--reverse**: 反转排序顺序
- **-s**, **--sort=(field)**: 按哪个字段排序
- **--group-directories-first**: 优先列出目录，然后再列出其他文件
- **--group-directories-last**: 列出其他文件之后的目录
- **-D**, **--only-dirs**: 仅列出目录
- **-f**, **--only-files**: 仅列出文件
- **--no-symlinks**: 不显示符号链接
- **--show-symlinks**: 显式显示链接 (使用 `--only-dirs`, `--only-files`, 表示显示与过滤器匹配的符号链接)
- **--git-ignore**: 忽略在以下位置提到的文件 `.gitignore`
- **-I**, **--ignore-glob=(globs)**: 要忽略的文件的 glob 模式（以管道符分隔）

传递该 `--all` 选项两次以同时显示 `.` 和 `..` 目录.


## 安装(wsl)
```sh
#!/bin/bash
set -e

ARCH=$(uname -m)
case "$ARCH" in
    x86_64)         FILE="eza_x86_64-unknown-linux-gnu.tar.gz" ;;
    aarch64|arm64)  FILE="eza_aarch64-unknown-linux-gnu.tar.gz" ;;
    *) echo "❌ 架构不支持: $ARCH"; exit 1 ;;
esac

URL="https://github.com/eza-community/eza/releases/latest/download/$FILE"

echo "📥 正在下载 $FILE 到当前目录..."
curl -L -O "$URL"

echo "📦 正在解压并安装..."

tar -xzf "$FILE"

sudo install -m 755 eza /usr/local/bin/eza

rm -f "$FILE" eza

echo "✅ eza 安装完成。"
eza --version
```

