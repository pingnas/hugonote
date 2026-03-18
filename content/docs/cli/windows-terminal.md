# Windows Terminal
微软的一款现代化、快速、高效、强大且实用的终端应用程序

## 参考

- [terminal](https://github.com/microsoft/terminal)
- [Windows 终端](https://apps.microsoft.com/detail/9n0dx20hk701?hl=en-US&gl=US)
- [PowerShell](https://github.com/PowerShell/PowerShell)
- [PowerShell7](https://learn.microsoft.com/en-us/powershell/scripting/install/install-powershell-on-windows?view=powershell-7.5)
- [PSReadLine](https://github.com/PowerShell/PSReadLine)
- [Oh My Posh](https://ohmyposh.dev/)
- [PSCompletions (psc)](https://pscompletions.abgox.com/zh-CN/readme/)


## PowerShell

### Oh My Posh

```sh
# 安装
winget install JanDeDobbeleer.OhMyPosh --source winget  

# 修改字体
https://ohmyposh.dev/docs/installation/fonts


# 修改配置文件
https://ohmyposh.dev/docs/installation/prompt
code $PROFILE


# 使用主题
https://ohmyposh.dev/docs/installation/customize
oh-my-posh init pwsh --config "stelbent-compact.minimal" | Invoke-Expression

```


### PSCompletions (psc)

一个补全管理器，为 PowerShell 带来更出色、更简便的 Tab 补全体验。

```sh
code $PROFILE

# 修改配置文件
Import-Module PSCompletions
```