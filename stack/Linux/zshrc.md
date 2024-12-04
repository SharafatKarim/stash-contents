---
Owner: Sharafat Karim
Last edited time: 2022-12-21T21:27
---
```Bash
# # Lines configured by zsh-newuser-install
# HISTFILE=~/.histfile
# HISTSIZE=1000
# SAVEHIST=1000
# bindkey -e
# # End of lines configured by zsh-newuser-install
# # The following lines were added by compinstall
# zstyle :compinstall filename '/home/qogir/.zshrc'
#
# autoload -Uz compinit
# compinit
# # End of lines added by compinstall

source ~/.bashrc

source ~/antigen.zsh

# Load the oh-my-zsh's library.
antigen use oh-my-zsh

# Bundles from the default repo (robbyrussell's oh-my-zsh).
antigen bundle git
# antigen bundle heroku
antigen bundle pip
# antigen bundle lein
antigen bundle command-not-found

# Syntax highlighting bundle.
antigen bundle zsh-users/zsh-syntax-highlighting

# Load the theme.
antigen theme refined

antigen bundle MichaelAquilina/zsh-auto-notify
antigen bundle zsh-users/zsh-autosuggestions

# Tell Antigen that you're done.
antigen apply

# Created by `pipx` on 2022-10-23 02:44:08
# export PATH="$PATH:/home/sharafat/.local/bin"

# Ryby gems
export PATH="$PATH:/home/sharafat/.local/share/gem/ruby/3.0.0/bin/"
```