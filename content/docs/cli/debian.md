# Wsl debian

## base
```sh
# 更新索引并安装：核心下载(curl/wget)、编辑器(vim)、代码管理(git)、编译环境(build-essential)、
# HTTPS证书(ca-certificates)、网络诊断(ping/dig)、系统监控(htop)、JSON处理(jq)、
# 终端复用(tmux)、解压(unzip)以及Debian源管理必备(lsb-release/gnupg)
sudo apt update && sudo apt install -y \
  curl wget vim git build-essential ca-certificates \
  iputils-ping dnsutils htop jq tmux unzip \
  lsb-release gnupg \
  && sudo apt autoremove -y && sudo apt clean

# 安装完成后清理一下缓存以节省空间
sudo apt autoremove -y && sudo apt clean
```
