# Wsl debian
我的默认base debian 

## 安装wsl
```sh
# 版本
wsl --list --online

# 安装debian
wsl --install -d Debian
```

## 禁用 WSL 的 Windows`$PATH` 互操作性

```sh
# 运行以下命令以**root权限**打开文件：
sudo vi /etc/wsl.conf

# 输入您的 WSL 用户密码。
# 单击`i`进入编辑模式（插入模式）。
# 输入或修改内容：
[interop]
appendWindowsPath = false

# 单击`Esc`退出编辑模式。
# 输入`:wq`(保存并退出)。

# 修改`/etc/wsl.conf`后，您必须完全关闭并重新启动 WSL 才能更改生效。
wsl --shutdown
```


## 进入wsl
```sh
# base
sudo apt update && sudo apt install -y curl wget vim git build-essential iputils-ping net-tools htop dnsutils unzip zip procps 

sudo apt install git-lfs
git lfs install

# 清理安装产生的缓存，节省 WSL 空间
sudo apt autoremove -y && sudo apt clean
```



## 安装脚本
> 安装 lazygit
```sh

#!/bin/bash
# set -e

ARCH=$(uname -m)
case "$ARCH" in
    x86_64)         BIN_ARCH="x86_64" ;;
    aarch64|arm64)  BIN_ARCH="arm64" ;;
    *) echo "❌ 架构不支持: $ARCH"; exit 1 ;;
esac

echo "🔍 正在搜索最新版 Lazygit..."
URL_LATEST="https://github.com/jesseduffield/lazygit/releases/latest"
REAL_URL=$(curl -Ls -o /dev/null -w %{url_effective} "$URL_LATEST")
TAG=$(basename "$REAL_URL")
VERSION=${TAG#v}

FILE="lazygit_${VERSION}_Linux_${BIN_ARCH}.tar.gz"
URL="https://github.com/jesseduffield/lazygit/releases/download/${TAG}/${FILE}"

echo "📥 正在下载 $FILE 到当前目录..."
curl -L -O "$URL"

echo "📦 正在安装..."
tar -xzf "$FILE" lazygit
sudo install -m 755 lazygit /usr/local/bin/lazygit

rm -f "$FILE" lazygit

echo "✅ lazygit 安装完成。"
lazygit --version
```

> 安装btop
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

> 安装eza
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

> 安装neovim
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

> 安装tmux
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

> 安装yazi
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