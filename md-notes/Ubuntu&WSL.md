# Ubuntu and WSL

## Ubuntu

### System

1. Confirm *aarch64 (ARM)* or *x64*: `cat /proc/cpuinfo`

### Users

1. Add new user: in root mode `adduser [username]`
1. Change user `su [username]`
1. Check user list `cut -d: -f1 /etc/passwd`
1. Add user to sudoers: in root mode, `sudo adduser [username] sudo`

## WSL

### Issues

1. Error when executing `wsl` in PowerShell, or starting WSL: `The attempted operation is not supported for the type of object referenced`
   1. NoLsp.exe solution  https://github.com/microsoft/WSL/issues/4177#issuecomment-597736482
   1. Another discussion https://github.com/microsoft/WSL/issues/5351