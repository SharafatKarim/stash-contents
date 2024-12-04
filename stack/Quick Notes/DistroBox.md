---
tags:
  - Software-Development
  - docker
Last Updated: 2022-12-12T10:37
Author: https://www.notion.so/685c212b8dda43ae86b79d2ad364e212?pvs=21
Created: 2022-12-12T09:22
Public: true
Featured: false
---
# Start

First configure docker or podman

# Installation

Follow your rpo

# Startup

## Choose a distro

for a list of compatible images and container managers, please consult the man page,

```Bash
man distrobox-compatibility
man distrobox
```

## Installing distro

Syntax is,

```Bash
distrobox-create --name CONTAINER-NAME --image OS-NAME:VERSION
```

an example,

```Bash
distrobox-create --name ubuntu --image ubuntu
```

## List all

```Bash
distrobox list
```

## Enter into one

```Bash
distrobox enter ubuntu
```

> Ubuntu specific,  
> First upgrade and then update like,  
>   
> `sudo apt upgrade` and `sudo apt update`

> Message:  
>   
> `'notify-send' must be installed for zsh-auto-notify to work`  
> Solution:  
> For ubuntu based distro,  
>   
> `sudo apt install libnotify-bin`

## System export app

To export app to the system,

```Bash
distrobox-export --app foliate
```

# Removal

First stop container, by,

```Bash
distrobox stop CONTAINER-NAME
```

then, remove like,

```Bash
distrobox rm CONTAINER-NAME
```