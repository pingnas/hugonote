# wsl

## 命令
```sh
# 版本
wsl --list --online

# 安装debian
wsl --install -d Debian
```


## 导出
```sh
# 体积小
wsl --export aaa D:\linux\aaa.tar.gz --format tar.gz

# 体积大
wsl --export aaa e:\aaa.tar
```

## [添加 wsl.conf 条目以控制 Windows 互操作行为 \[GH 1493\]](https://learn.microsoft.com/en-us/windows/wsl/release-notes#build-17713)

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

## win转发netsh命令
需要管理员运行，必须蓝色的那个powershell

```sh
# 清空所有规则
netsh interface portproxy reset


# 删除特定的一条规则
netsh interface portproxy delete v4tov4 listenport=[端口号] listenaddress=[监听地址]
# netsh interface portproxy delete v4tov4 listenport=8080 listenaddress=0.0.0.0


# 查询
netsh interface portproxy show all



# 在Windows中设置转发
netsh interface portproxy add v4tov4 listenport=[外部访问端口] listenaddress=0.0.0.0 connectport=[WSL内部端口] connectaddress=[WSL内部IP]
# netsh interface portproxy add v4tov4 listenport=8080 listenaddress=0.0.0.0 connectport=80 connectaddress=172.20.10.5 
# netsh interface portproxy add v4tov4 listenport=8317 listenaddress=0.0.0.0 connectport=8317 connectaddress=172.19.187.220

```


## 获取 WSL 虚拟机自己的内部 IP 地址
```sh
hostname -I | awk '{print $1}'
# 172.19.187.220
hostname -I
```

## 使用 tar 进行迁移文件夹

```sh
# 在发行版 A 中
tar -cvzf my_files.tar.gz /path/to/your/folder

# 假设你在发行版 B
tar -xvzf my_files.tar.gz

# 快速清理现有的 .Identifier 文件
find . -name "*:Zone.Identifier" -type f -delete
# 或者如果文件名直接显示为 .Identifier
find . -name "*.Identifier" -type f -delete

rm -rf 文件夹名
rm 文件名.txt
```

