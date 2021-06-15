# Ubuntu and WSL

## Ubuntu

### System

1. Confirm *aarch64 (ARM)* or *x64*: `cat /proc/cpuinfo`

### Users

1. Add new user: in root mode `adduser [username]`
1. Change user `su [username]`
1. Check user list `cut -d: -f1 /etc/passwd`
1. Add user to sudoers: in root mode, `sudo adduser [username] sudo`

## Softwares

1. Zsh
   1. Change default shell to Zsh `chsh -s $(which zsh)`
1. Miniconda
   1. `wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh`
   1. `bash Miniconda3-latest-Linux-x86_64.sh`
      1. or maybe better `bash miniconda.sh -b -u -p ~/miniconda3`

## WSL

1. Set Ubuntu default user, in PS `ubuntu config --default-user [username]`

### Issues

1. Error when executing `wsl` in PowerShell, or starting WSL: `The attempted operation is not supported for the type of object referenced`
   1. NoLsp.exe solution  https://github.com/microsoft/WSL/issues/4177#issuecomment-597736482
      1. Download [NoLsp.exe](http://www.proxifier.com/tmp/Test20200228/NoLsp.exe)
      1. Execute `NoLsp.exe c:\windows\system32\wsl.exe`
   1. Another discussion https://github.com/microsoft/WSL/issues/5351