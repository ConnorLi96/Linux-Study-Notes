- Step1: enter in the home path
```
cd  
```
- Step2: edit bash_profile file
```
vim .bash_profile 
```
- Step3: copy all content into the .bash_profile 
```
# some more ls aliases
alias ll='ls -lF'
alias la='ls -A'
alias l='ls -alhF'
alias ..='cd .. && l'
alias ...='cd ../.. && l'
alias ~='cd ~ && l'

PS1="\$([[ \$? != 0 ]] && echo \"\[\033[1;37m\][\[\033[1;31m\]X\[\033[1;37m\]]\")\[\033[1;36m\]\u\[\033[1;32m\]@\[\033[1;34m\]\h\[\033[1;31m\]:\[\033[1;35m\]\w \[\033[1;36m\]\$(/bin/ls -1 | /usr/bin/wc -l | /usr/bin/sed \"s: ::g\")\[\033[1;33m\]> \[\033[0m\]"

export LS_OPTIONS='--color=auto' # 如果没有指定，则自动选择颜色
export CLICOLOR='Yes' #是否输出颜色
export LSCOLORS='Exfxcxdxbxegedabagacad' #指定颜色
export GOPATH=/Users/laodouya/gopath
eval `keychain --eval --agents ssh --inherit any id_rsa`
```

- Step4: make it effective
```
source .bash_profile
```
