# Winget
微软推出的基于命令行的包管理器，类似于 Chocolatey。

## 资料

- [WinGet](https://learn.microsoft.com/en-us/windows/package-manager/)
- [winget-cli](https://github.com/microsoft/winget-cli)
- [WinGet命令](https://learn.microsoft.com/zh-cn/windows/package-manager/winget/#commands)

## 命令

```sh
winget search <packageName>

winget install <Package ID>

winget uninstall <Package ID>

winget upgrade <Package ID>

# 升级到特定的版本
winget upgrade <Package ID> -v <version> 

# 升级所有应用
winget upgrade --all 

# 将本机安装的 Package 导出成 json 文件，加上 --include-versions 表示导出时需要包括版本
winget export -o <OutputPath> --include-versions

# 加上 --ignore-unavailable 跳过无法安装的部分，避免阻塞整个流程
winget import -i <JsonPath> --ignore-versions --ignore-unavailable

```

