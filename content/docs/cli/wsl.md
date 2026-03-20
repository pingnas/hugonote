# wsl

## 导出
```sh
# 体积小
 wsl --export aaa D:\linux\aaa.tar.gz --format tar.gz

# 体积大
 wsl --export aaa e:\aaa.tar
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


# 转发

# 获取WSL的内部IP
hostname -I
# 在Windows中设置转发
netsh interface portproxy add v4tov4 listenport=[外部访问端口] listenaddress=0.0.0.0 connectport=[WSL内部端口] connectaddress=[WSL内部IP]
# netsh interface portproxy add v4tov4 listenport=8080 listenaddress=0.0.0.0 connectport=80 connectaddress=172.20.10.5 
# netsh interface portproxy add v4tov4 listenport=8317 listenaddress=0.0.0.0 connectport=8317 connectaddress=172.19.187.220

```


## 获取当前机器 IP
```sh
hostname -I | awk '{print $1}'
# 172.19.187.220
```

## 使用 tar 进行迁移

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

