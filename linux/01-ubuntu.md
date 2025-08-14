# Ubuntu

## Basic To-Dos

- `touch ~/.hushlogin` - Hide home screen message

## Essential Packages

```bash
# Core Development Tools
sudo apt install -y \
    git python openjdk-17 nodejs \
    openssh sshpass neovim wget curl

# Enhanced Shell Tools
sudo apt install -y \
    fish tmux eza bat fzf tree tldr neofetch colordiff

# Development & System Tools
sudo apt install -y \
    pip pipx snapd build-essential \
    make net-tools unzip adb fastboot platform-tools
```

### Package Installation Notes

- Use `pipx` for Python applications (e.g., yt-dlp)

  ```bash
  pipx ensurepath
  pipx install yt-dlp
  ```

- For .deb packages:

  ```bash
  wget app_url.deb
  sudo apt install ./app.deb
  # OR
  sudo dpkg -i app.deb
  ```

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

###
Enable right click to open folder here with Ubuntu
- Open windows terminal
- Open settings
- Set the default profile to 1 ubuntu. Try 2nd ubuntu icon if the first one does not work.