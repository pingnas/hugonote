---
title: "btop 资源监视器"
---

# btop
资源监视器，显示处理器、内存、磁盘、网络和进程的使用情况和统计​​信息。

## 资料
- [btop](https://github.com/aristocratos/btop)

## 安装(wsl)
```sh
#!/bin/bash
set -e

ARCH=$(uname -m)
case "$ARCH" in
    x86_64)         FILE="btop-x86_64-unknown-linux-musl.tbz" ;;
    aarch64|arm64)  FILE="btop-aarch64-unknown-linux-musl.tbz" ;;
    *) echo "❌ 架构不支持: $ARCH"; exit 1 ;;
esac
URL="https://github.com/aristocratos/btop/releases/latest/download/$FILE"

echo "📥 正在下载 $FILE 到当前目录..."
curl -L -O "$URL"

echo "📦 正在安装并自动清理..."

tar -xjf "$FILE"

sudo install -m 755 btop/bin/btop /usr/local/bin/btop

rm -rf "$FILE" btop

echo "✅ btop 安装成功。"
btop --version
```
