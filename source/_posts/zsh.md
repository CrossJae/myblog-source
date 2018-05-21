---
title: zsh theme
date: 2017-11-10 22:47:23
tags: [zsh,vim]
---

1. 基本修改方式
  * 修改zsh配置文件
  ```
  $ vim ~/.zshrc
  ```
  * 修改配置文件中的主题，ys是比较流行的主题，可以进入网站查看主题 [https://zshthem.es/](https://zshthem.es/)
  ```
  ZSH_THEME="ys"
  ```
  * 进入主题的配置文件目录，查看所有的主题，主题配置文件的命名都是`themeName.zsh-theme`。
  ```
  $ cd ~/.oh-my-zsh/themes
  $ ls
  ```
  * 修改主题配置文件
  ```
  $ vim ys.zsh-theme
  ```
  * 修改保存后， **重启** zsh生效，或者source配置文件
  ```
  $ source ~/.zshrc
  ```
2. 建立自己的主题（以ys主题为模版）
  1. 复制一个ys主题配置文件
  ```
  $ cp ys.zsh-theme yourname.zsh-theme
  ```
  2. 修改我们的主题
  ```
  $ vim yourname.zsh-theme
  ```
  3. 修改主题配置中的git相关，和时间相关语句
  ```
  // git
  YS_VCS_PROMPT_PREFIX2=" 🌸   %{$fg[cyan]%}"
  // 时间
  PROMPT="
  %{$terminfo[bold]$fg[cyan]%}#%{$reset_color%} \
  %(#,%{$bg[yellow]%}%{$fg[black]%}%n%{$reset_color%},%{$fg[cyan]%}%n) \
  %{$fg[white]%}@ \
  %{$fg[green]%}%m \
  %{$fg[white]%}in \
  %{$terminfo[bold]$fg[yellow]%}%~%{$reset_color%}\
  ${hg_info}\
  ${git_info}\
  %{$fg[white]%}[%D %T] $exit_code
  %{$terminfo[bold]$fg[red]%}⚡️   %{$reset_color%}"
  ```
  4. 保存后修改zshrc配置文件
  ```
  $ vim ~/.zshrc
  ```
  5. 修改主题名称
  ```
  ZSH_THEME="10crossjae"
  ```
  6. 退出配置文件，使其生效
  ```
  $ source ~/.zshrc
  ```
