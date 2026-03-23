---
title: "Yazi 终端文件管理器"
---

# Yazi
基于异步 I/O，用 Rust 编写的超快终端文件管理器

## 资料
- [yazi](https://github.com/sxyazi/yazi)
- [docs](https://yazi-rs.github.io/)

## 安装 (wsl)
```sh
#!/bin/bash
set -e

ARCH=$(uname -m)
case "$ARCH" in
    x86_64)         FILE="yazi-x86_64-unknown-linux-gnu.deb" ;;
    aarch64|arm64)  FILE="yazi-aarch64-unknown-linux-gnu.deb" ;;
    *) echo "❌ 架构不支持"; exit 1 ;;
esac

URL="https://github.com/sxyazi/yazi/releases/latest/download/$FILE"

echo "📥 正在下载 $FILE 到当前目录..."
curl -L -O "$URL"

echo "📦 正在安装并自动清理本地包..."
sudo apt install -y "./$FILE" && rm "$FILE"

echo "✅ 安装成功，已自动清除 $FILE。"
yazi --version
```
