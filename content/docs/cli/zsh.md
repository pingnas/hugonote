# zsh

## oh-my-zsh
> .zshrc
```sh
if [[ -r "${XDG_CACHE_HOME:-$HOME/.cache}/p10k-instant-prompt-${USER}.zsh" ]]; then
  source "${XDG_CACHE_HOME:-$HOME/.cache}/p10k-instant-prompt-${USER}.zsh"
fi

[[ -f ~/.p10k.zsh ]] && source ~/.p10k.zsh
export ZSH="$HOME/.oh-my-zsh"

ZSH_THEME="powerlevel10k/powerlevel10k"

export LANG=en_US.UTF-8

plugins=(
    git                
    z                  
    sudo               
    extract            
    web-search         
    zsh-autosuggestions      
    zsh-syntax-highlighting  
    zsh-completions          
)

source $ZSH/oh-my-zsh.sh

[ -d "/opt/nvim-linux-x86_64/bin" ] && export PATH="$PATH:/opt/nvim-linux-x86_64/bin"
[ -d "/opt/nvim-linux-arm64/bin" ] && export PATH="$PATH:/opt/nvim-linux-arm64/bin"

alias v="nvim"
alias vi="nvim"
alias vim="nvim"

if command -v eza > /dev/null; then
    alias ls='eza --icons --group-directories-first'
    alias ll='eza -lh --icons --git --group-directories-first'
    alias la='eza -lah --icons --git --group-directories-first'
    alias tree='eza --tree --icons'
else
    alias l="ls -lah"
fi
alias lg="lazygit"
alias y="yazi"  

alias ..="cd .."
alias ...="cd ../.."
alias ....="cd ../../.."
alias -- -='cd -'  

alias cls="clear"
alias ip="ip -color=auto"
alias ping="gping" 

alias vf='nvim $(fzf)'

zstyle ':completion:*' matcher-list 'm:{a-zA-Z}={A-Za-z}' 'r:|[._-]=* r:|=*' 'l:|=* r:|=*'

zstyle ':completion:*' use-cache yes
zstyle ':completion:*' cache-path "$ZSH_CACHE_DIR"
```

> .p10k.zsh

https://github.com/romkatv/powerlevel10k/tree/master/config 
随便挑个
