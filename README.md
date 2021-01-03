# Personal Linux Environment Setup

Just a collection of various setups I use. As of writing, this is
based on Ubuntu 20.04.

## Vim

Saved in `.vimrc`.

```
syntax on
set tabstop=4
set shiftwidth=4
set expandtab
set hls
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

```
# bash git prompt start
if [ -f "$HOME/.bash-git-prompt/gitprompt.sh" ]; then
    GIT_PROMPT_ONLY_IN_REPO=0
    GIT_PROMPT_THEME=Link_Ubuntu
    source $HOME/.bash-git-prompt/gitprompt.sh
fi
# bash git prompt end
```

### Directory Trimming

Additionally, the following is added for directory trimming.

```
# Trim directory path
PROMPT_DIRTRIM=1
```

[bash_git_prompt_url]: https://github.com/magicmonty/bash-git-prompt
