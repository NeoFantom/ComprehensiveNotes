# Ubuntu and WSL

- [Ubuntu and WSL](#ubuntu-and-wsl)
  - [Ubuntu](#ubuntu)
    - [System](#system)
    - [Users](#users)
  - [Softwares](#softwares)
  - [WSL](#wsl)
    - [Issues](#issues)

## Ubuntu

### System

1. Confirm *aarch64 (ARM)* or *x64*: `cat /proc/cpuinfo`
1. Show *message of the day* (motd)
   1. See [answer at Ask Ubuntu](https://askubuntu.com/questions/319528/how-to-see-the-details-which-ubuntu-shows-at-the-time-of-login-anytime).
      1. Use `cat /etc/motd` 
      1. or, better: `for i in /etc/update-motd.d/*; do if [ "$i" != "/etc/update-motd.d/98-fsck-at-reboot" ]; then $i; fi; done`
      1. To see this message everytime, add one of the above to end of `.bashrc` file.
   1. Add to end of `.bashrc` file: `/usr/bin/landscape-sysinfo`
   1. Add to end of `.bashrc` file: `run-parts /etc/update-motd.d` . This also worked fine.

### Users

1. Add new user: in root mode `adduser [username]`
1. Change user `su [username]`
1. Check user list `cut -d: -f1 /etc/passwd`
1. Change passwd `<sudo> passwd [username]` or no username to config current user.
1. Add user to sudoers: in root mode, `sudo adduser [username] sudo`
1. Rename username
   1. To change username (it is probably best to do this without being logged in): `sudo usermod -l newUsername oldUsername`
   1. This however, doesn't rename the home folder. To change home-folder, use `sudo usermod -d /home/newHomeDir -m newUsername`

## Softwares

1. Zsh
   1. Install.
      1. Try command `zsh`, Ubuntu will show install command.
      1. `sudo apt install zsh`
   1. [Oh My Zsh](https://ohmyz.sh/)
      1. `sh -c "$(wget https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh -O -)"`
      1. Change theme: change theme name in `~/.zshrc`
      1. Installed in non-root user, [change theme for root](https://askubuntu.com/questions/521469/oh-my-zsh-for-the-root-and-for-all-user).
   1. Change **default shell** to Zsh `chsh -s $(which zsh)`
      1. Change to bash `chsh -s /bin/bash` or `chsh -s /bin/bash YOUR_USERNAME`
   1. Uninstall Zsh `sudo apt-get --purge remove zsh`
1. Miniconda
   1. Install `wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh`
   1. `bash Miniconda3-latest-Linux-x86_64.sh`
      1. or maybe better `bash miniconda.sh -b -u -p ~/miniconda3`
   1. Uninstall. In order to uninstall miniconda, simply remove the miniconda folder, `rm -r ~/miniconda/`

## WSL

1. Set WSL default user, in PS `ubuntu config --default-user [username]`
1. Set starting directory, probably better in root user.
   1. `explorer.exe [some folder]` open some Linux folder in Windows.
   1. Remember the path to your home folder in Windows explorer.
   1. settings-Ubuntu-general, set starting directory to the remembered folder.

### Issues

1. WSL keeps failing at all. Error when executing `wsl` in PowerShell, or starting WSL: `The attempted operation is not supported for the type of object referenced`
   1. NoLsp.exe solution  https://github.com/microsoft/WSL/issues/4177#issuecomment-597736482
      1. Download [NoLsp.exe](http://www.proxifier.com/tmp/Test20200228/NoLsp.exe)
      1. Execute `NoLsp.exe c:\windows\system32\wsl.exe`
   1. Another discussion https://github.com/microsoft/WSL/issues/5351