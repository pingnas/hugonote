# uv

一个用 Rust 编写的、速度极快的 Python 包和项目管理器。

## 命令
```sh
# 安装
curl -LsSf https://astral.sh/uv/install.sh | sh

# 升级
uv self update

```

> Python 版本 https://docs.astral.sh/uv/guides/install-python/#next-steps
```sh
# 安装 Python 版本。
uv python install

# 查看可用的 Python 版本。
uv python list 

# 查找已安装的 Python 版本。
uv python find 

# 将当前项目锁定为使用特定的 Python 版本。
uv python pin

# 卸载 Python 版本。
uv python uninstall
```

> Scripts https://docs.astral.sh/uv/guides/scripts/
```sh
# 执行独立的 Python 脚本

# 运行脚本。
uv run

# 向脚本添加依赖项。
uv add --script

# 移除脚本中的依赖项。
uv remove --script
```

> 项目 https://docs.astral.sh/uv/guides/projects/
```sh
# 创建一个新的Python项目。
uv init

# 向项目中添加依赖项。
uv add

# 从项目中移除一个依赖项。
uv remove

# 将项目的依赖项与环境同步。
uv sync

# 为项目的依赖项创建锁定文件。
uv lock

# 在项目环境中运行命令。
uv run

# 查看项目的依赖关系树。
uv tree

# 将项目构建到分发存档中。
uv build

# 将项目发布到软件包索引。
uv publish
```

> 工具 https://docs.astral.sh/uv/guides/tools/
```sh
# 运行和安装发布到 Python 包索引的工具，例如ruff或black。

# 在临时环境中运行工具。
uvx/ uv tool run

# 安装一个用户级工具。
uv tool install

# 卸载工具。
uv tool uninstall

# 列出已安装的工具。
uv tool list

# 更新 shell 以包含工具可执行文件。
uv tool update-shell
```

> pip
```sh
# 创建虚拟环境（替换venv和virtualenv）
# https://docs.astral.sh/uv/pip/environments/

# 创建一个新的虚拟环境。
uv venv




# 在环境中管理软件包（替换pip和 pipdeptree）
# https://docs.astral.sh/uv/pip/packages/

# 将软件包安装到当前环境中。
uv pip install
# 显示已安装软件包的详细信息。
uv pip show
# 列出已安装的软件包及其版本。
uv pip freeze
# 检查当前环境中是否安装了兼容的软件包。
uv pip check
# 列出已安装的软件包。
uv pip list
# 卸载软件包。
uv pip uninstall
# 查看环境的依赖关系树。
uv pip tree




# 锁定环境中的软件包（替换pip-tools）
# https://docs.astral.sh/uv/pip/compile/

# 将需求编译成锁定文件。
uv pip compile
# 将环境与锁定文件同步。
uv pip sync
```



> Utility
```sh
# 删除缓存条目。
uv cache clean
# 删除过期的缓存条目。
uv cache prune
# 显示 UV 缓存目录路径。
uv cache dir
# 显示 UV 工具目录路径。
uv tool dir
# 显示已安装的 Python 版本路径。
uv python dir
# 将 uv 更新到最新版本。
uv self update
```