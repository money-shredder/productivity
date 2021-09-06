# Command Line

## SSH

## Tmux

## Ubuntu

### Install common tools

```zsh
sudo apt install zsh tmux htop less colordiff python3.8 python3-pip
```

### Add sudo user

```bash
adduser <username>
usermod -aG sudo <username>
```

### ZSH error

Error upon login:
```zsh
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = (unset),
	LC_TERMINAL_VERSION = "3.4.8",
	LC_CTYPE = "UTF-8",
	LC_TERMINAL = "iTerm2",
	LANG = (unset)
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = (unset),
	LC_TERMINAL_VERSION = "3.4.8",
	LC_CTYPE = "UTF-8",
	LC_TERMINAL = "iTerm2",
	LANG = (unset)
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
```

Fix: 
```
sudo apt install locales && locale-gen "en_US.UTF-8"
```

