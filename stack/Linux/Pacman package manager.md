---
Owner: Sharafat Karim
Last edited time: 2022-12-21T20:37
---
# Sync

First let’s sync,

`sudo pacman -Sy`

To do system update and upgrade,

`sudo pacman -Syu`

> [!important]  
> instead of “-Syu”, do “-Syyu” to force update  

# Installation

To install a package,

`sudo pacman -S` `_package-name_`

To install as dependency,

`sudo pacman -S --asdeps` _`package-name`_

To install if it’s not installed (—needed) and without confirmation (—norconfirm)

`sudo pacman -S --needed --noconfirm` `_package-name_`

> [!important]  
> Here package-name means the name of the specific package you want to install  

---

> **Now, what to install?**

> [!info] Useful Linux Applications  
> This list's formatting is "Applications name" and "short description".  
> [https://sharafat.pages.dev/useful-linux-applications/](https://sharafat.pages.dev/useful-linux-applications/)  

---

Install with all optional dependencies as dependency,

`sudo pacman -S --asdeps --needed $(pacman -Si` _````````````` ```````````` ``````````` `````````` ````````` ```````` ``````` `````` ````` ```` ``` `` `package-name` `` ``` ```` ````` `````` ``````` ```````` ````````` `````````` ``````````` ```````````` `````````````_ `| sed -n '/^Opt/,/^Conf/p' | sed '$d' | sed 's/^Opt.*://g' | sed 's/^\s*//g' | tr '\n' ' ')`

or, copy from here,

```Bash
sudo pacman -S --asdeps --needed $(pacman -Si package-name | sed -n '/^Opt/,/^Conf/p' | sed '$d' | sed 's/^Opt.*://g' | sed 's/^\s*//g' | tr '\n' ' ')
```

# Listing packages

To get all software's list (explicitly installed + dependency),

> _system package + manually installed later + dependency_

`pacman -Q`

> [!important]  
> Also try “pacman -Q package-name”  

To get only explicitly installed applications

> _system package + manually installed later + not dependency_

`pacman -Qe`

To get only explicitly installed app without system packages

> _not system package + manually installed later + not dependency_

`pacman -Qet`

To get only dependency, aka orphans,

> _not system package + not manually installed later + dependency_

`pacman -Qdt`

> [!important]  
> sudo permission isn’t required!  

- Output to a text file!
    
    Run, something like, `pacman -Qet > packages.txt`
    

# Removing packages

To remove, just -R is fine,

`sudo pacman -R` _````````````` ```````````` ``````````` `````````` ````````` ```````` ``````` `````` ````` ```` ``` `` `package-name` `` ``` ```` ````` `````` ``````` ```````` ````````` `````````` ``````````` ```````````` `````````````_

And to remove orphans,

`sudo -S pacman -R --noconfirm $(pacman -Qdtq)`

# Further assistance

> [!info] pacman  
> The pacman package manager is one of the major distinguishing features of Arch Linux.  
> [https://wiki.archlinux.org/title/Pacman](https://wiki.archlinux.org/title/Pacman)