# Skills


## 参考
- [skills](https://github.com/vercel-labs/skills)
- [skills.sh](https://skills.sh/)


## 命令

### 添加skills
```sh
# GitHub 简写 (owner/repo)
npx skills add vercel-labs/agent-skills

# 完整 GitHub URL
npx skills add https://github.com/vercel-labs/agent-skills

# 仓库中某项技能的直接路径
npx skills add https://github.com/vercel-labs/agent-skills/tree/main/skills/web-design-guidelines

# GitLab URL
npx skills add https://gitlab.com/org/repo

# Any git URL
npx skills add git@github.com:vercel-labs/agent-skills.git

# Local path
npx skills add ./my-local-skills

```

> `-g, --global` 安装到用户目录而不是项目目录(默认是项目目录)


> `-a, --agent <agents...>` 指定目标Agents : https://github.com/vercel-labs/skills?tab=readme-ov-file#supported-agents


> `-s, --skill <skills...>` 按名称安装特定技能（使用“*”安装所有技能）
> 
```sh
# 安装特定技能  
npx skills add vercel-labs/agent-skills --skill frontend-design --skill skill-creator 

# 安装名称中包含空格的技能（必须加引号）  
npx skills add owner/repo --skill "Convex Best Practices"  

# 非交互式安装 (安装 frontend-design 到 用户目录，指定给claude-code使用 ，无需提示 )
npx skills add vercel-labs/agent-skills --skill frontend-design -g -a claude-code -y  

# 安装所有技能到特定agent  
npx skills add vercel-labs/agent-skills --skill '*' -a claude-code  

# 安装特定技能到所有agent
npx skills add vercel-labs/agent-skills --agent '*' --skill frontend-design
```


> `-l, --list` 列出可用技能而不安装
>
```sh
# 列出仓库中的技能  
npx skills add vercel-labs/agent-skills --list  
```


> `--copy` 复制文件而不是符号链接到Agents目录
>
```txt
符号链接（默认）
为每个agent创建指向规范副本的符号链接。单一数据源，便于更新。  

复制
为每个agent创建独立副本。在符号链接不支持时使用。
```


> `-y, --yes` 跳过所有确认提示


> `--all` 无需提示，为所有agent安装所有技能
>
```sh
# 安装仓库中所有技能到所有agent
npx skills add vercel-labs/agent-skills --all  
```

### 其它命令

```sh
# 列出已安装的技能（别名：ls）
npx skills list

# 列出所有已安装的技能（项目和全局）
npx skills list

# 仅列出全局技能
npx skills ls -g

# 按特定agent筛选
npx skills ls -a claude-code -a cursor





# 通过交互方式或关键词搜索技能
npx skills find [query]	

# 交互式搜索（fzf 风格）  
npx skills find

# 按关键词搜索  
npx skills find typescript  




# 检查已安装技能是否有更新  
npx skills check

# 将所有技能更新至最新版本  
npx skills update




# 在当前目录创建 SKILL.md 文件  
npx skills init

# 在子目录中创建新技能  
npx skills init my-skill  



# 交互式移除（从已安装技能中选择）  
npx skills remove

# 按名称移除特定技能  
npx skills remove web-design-guidelines

# 移除多个技能  
npx skills remove frontend-design web-design-guidelines

# 从全局范围移除  
npx skills remove --global web-design-guidelines

# 仅从特定代理移除  
npx skills remove --agent claude-code cursor my-skill

# 移除所有已安装技能（无需确认）  
npx skills remove --all

# 从特定代理移除所有技能  
npx skills remove --skill '*' -a cursor

# 从所有代理移除特定技能  
npx skills remove my-skill --agent '*'

# 使用 'rm' 别名  
npx skills rm my-skill



-g, --global	        从全局范围（~/）而非项目中移除  
-a, --agent         	从特定代理中移除（使用“*”表示全部）  
-s, --skill         	指定要移除的技能（使用“*”表示全部）  
-y, --yes           	跳过确认提示  
--all	                --skill '*' --agent '*' -y 的简写
```



## skills

- [Vibe-Skills](https://github.com/foryourhealth111-pixel/Vibe-Skills)
- 