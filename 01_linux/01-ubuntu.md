# Ubuntu

## Basic To-Dos

- `touch .hushlogin` - Hide home screen message

- `sudo apt update -y` > `sudo apt upgrade -y` > `sudo apt autoremove -y`

### Change ubuntu hostname(computer name)

```bash
sudo nano /etc/wsl.conf
# Ensure network section script is added
[boot]
systemd=true

[wsl2]
guiApplications = true

[network]
hostname = ubuntu
generateHosts = false


# Also replace name in
sudo nano /etc/hostname
sudo nano /etc/hosts
```

## Essential Packages

```bash
# Core development tools
sudo apt install -y build-essential git python3 python3-pip \
sshpass openssh-client neovim wget curl


# Enhanced shell tools
sudo apt install -y tmux tree colordiff bat eza tldr
```

### Package Installation Notes

- Use `pipx` for Python applications (e.g., yt-dlp)

  ```bash
  pipx ensurepath
  pipx install yt-dlp
  ```

###
Enable right click to open folder here with Ubuntu
- Open windows terminal
- Open settings
- Set the default profile to 1 ubuntu. Try 2nd ubuntu icon if the first one does not work.
