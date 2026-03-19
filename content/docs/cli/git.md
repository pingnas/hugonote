# Git

## ssh key
```sh
ssh-keygen -t ed25519 -C "1@email.com" -f ~/.ssh/1 # 生成名为 "1" 的 Ed25519 密钥对，并保存在 ~/.ssh/ 目录下

cat ~/.ssh/1.pub # 查看并复制公钥 "1" 的内容

ssh -T git@1.github.com
```