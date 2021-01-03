# Personal Linux Environment Setup

Just a collection of various setups I use. As of writing, this is
based on Ubuntu 20.04.

## Vim

Saved in `~/.vimrc`.

```vim
syntax on
set tabstop=4
set shiftwidth=4
set expandtab
set hlsearch
```

## Git

Saved in `.gitconfig`. Fields `<github_token>`, `<email_address>`,
and `<name>` should be replaced accordingly.

```
[url "https://<github_token>@github.com"]
    insteadOf = https://github.com

[user]
    email = <email_address>
    name = <name>

[merge]
    ff = no
    commit = no

[core]
    editor = vim

[alias]
    graph = log --graph --oneline
```

## Bash

### Git Prompt

Added to `.bashrc`. Uses [bash-git-prompt][bash_git_prompt_url]
together with the included customized theme named `Link_Ubuntu.bgptheme`.

```sh
# bash git prompt
if [ -f ~/.bash-git-prompt/gitprompt.sh ]; then
    GIT_PROMPT_ONLY_IN_REPO=0
    GIT_PROMPT_THEME=Link_Ubuntu
    source ~/.bash-git-prompt/gitprompt.sh
fi
```

### Trimmed Directory Path

Additionally, the following is added for directory trimming.

```sh
# Trim directory path
PROMPT_DIRTRIM=1
```

### Colored Less

Saved in `~/.LESS_TERMCAP`.

```sh
export LESS_TERMCAP_mb=$(tput bold; tput setaf 6)
export LESS_TERMCAP_md=$(tput bold; tput setaf 2)
export LESS_TERMCAP_me=$(tput sgr0)
export LESS_TERMCAP_so=$(tput bold; tput setaf 0; tput setab 7)
export LESS_TERMCAP_se=$(tput rmso; tput sgr0)
export LESS_TERMCAP_us=$(tput smul; tput bold; tput setaf 3)
export LESS_TERMCAP_ue=$(tput rmul; tput sgr0)
export LESS_TERMCAP_mr=$(tput rev)
export LESS_TERMCAP_mh=$(tput dim)
export LESS_TERMCAP_ZN=$(tput ssubm)
export LESS_TERMCAP_ZV=$(tput rsubm)
export LESS_TERMCAP_ZO=$(tput ssupm)
export LESS_TERMCAP_ZW=$(tput rsupm)
export GROFF_NO_SGR=1
```

Additionally, in order to be activated the following should be added to `~/.bashrc`.

```sh
# Get color support for 'less'
export LESS="--RAW-CONTROL-CHARS"

# Use colors for less, man, etc.
if [ -f ~/.LESS_TERMCAP ]; then
    source ~/.LESS_TERMCAP
fi
```

[bash_git_prompt_url]: https://github.com/magicmonty/bash-git-prompt
