# neovim

## 安装(wsl)
```sh
#!/bin/bash
set -e

ARCH=$(uname -m)
case "$ARCH" in
    x86_64)          BIN_ARCH="x86_64" ;;
    aarch64|arm64)   BIN_ARCH="arm64" ;;
    *) echo "❌ 架构不支持: $ARCH"; exit 1 ;;
esac

FILE="nvim-linux-${BIN_ARCH}.tar.gz"
DIR_NAME="nvim-linux-${BIN_ARCH}"
URL="https://github.com/neovim/neovim/releases/latest/download/${FILE}"

echo "🔍 正在从官方获取 $BIN_ARCH 版 Neovim..."

curl -LO "$URL"

echo "📦 正在安装至 /opt..."
sudo rm -rf "/opt/$DIR_NAME"
sudo tar -C /opt -xzf "$FILE"

rm -f "$FILE"

echo "------------------------------------------"
echo "✅ Neovim 已成功解压到 /opt/$DIR_NAME"

if [[ ":$PATH:" == *":/opt/$DIR_NAME/bin:"* ]]; then
    echo "🚀 PATH 已经配置好了。"
else
    echo "⚠️  请手动将以下行添加到您的 ~/.bashrc 或 ~/.zshrc 中："
    echo "   export PATH=\"\$PATH:/opt/$DIR_NAME/bin\""
    echo "   然后执行: source ~/.bashrc (或 source ~/.zshrc)"
fi

echo "------------------------------------------"
/opt/$DIR_NAME/bin/nvim --version | head -n 1
```
