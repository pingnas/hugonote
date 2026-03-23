# lazygit

用于 git 命令的简单终端界面

## 资料
- [lazygit仓库](https://github.com/jesseduffield/lazygit)
- [按键绑定文档](https://github.com/jesseduffield/lazygit/blob/master/docs/keybindings/Keybindings_zh-CN.md)
- [如何使用Lazygit 大幅提升使用Git 的效率](https://chishengliu.com/zh-tw/posts/lazygit-tutorial/)
## 常用

> 全局快捷键
```sh
# 上下切换左半边的区块
h和l

# 上下移动光标
k和j

# 搜索
/

# 左半边区块的分页，左右切换
[ ]

# 复制文件名（Files 区块）、Branch 名称（Local branches 区块）、或是commit hash（commits 区块）到剪贴板。
Ctrl + o

# 退出Lazygit
q
```


> 左半边Files 区块
```sh
# 为选定的文件切换暂存状态
<space>

# 切换工作区中所有文件的已暂存/未暂存状态
a

# 如果选中的是一个文件，则会进入到预览视图，以便可以暂存单个代码块/行。如果选中的是一个目录，则会折叠/展开这个目录
<enter>

# 使用 Git 编辑器提交变更
C

# 修补最后一次提交
A

# 查看选中文件的放弃变更选项
d

# 清空所有文件还没有被commit 的所有变更，当想重来的时候用的。
D

# 打开stash 选项。
S
```

> 左半边Local branches 区块
```sh
# 切换到该branch
<space>

# 从该branch checkout 出一个新的branch。
n

# Fetch 该branch 在remote 的新commits。
f

#将检出的分支变基到所选的分支上
r

# 重新命名branch
R

# Pull 该branch。
p

# Push 该branch。
P

# 开启GitHub open pull request（创建拉取请求） 的页面。
o

# 查看该branch 的commit。使用Esc返回。
<enter>
```

> 左半边Commits 区块
```sh
# 查看该commit 改了哪些档案。使用Esc返回。
<enter>

# 打开外部编辑器更改commit message。
R

# 删掉该commit
d

# 打开reset 选项
g

# 创一个对该commit 的fixup!commit。
F

# Squash 所有在该commit 之上的fixup!commits。
S
```

> 左半边Stash 区块
```sh
# 将存储项应用到工作目录并删除存储项。
g

# 将贮藏项应用到您的工作目录。
<space>

# 从贮藏列表中删除该贮藏项
d
```

> 右半边预览区块
```sh
# 进入多行选取模式。
v

# 把该行，或是多行（用多行选取模式选取的话）加入或移除自staging area
<space>

# 回到左半边的区块
Esc
```
