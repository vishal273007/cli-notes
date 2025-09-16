# Ubuntu

## Basic To-Dos

- `touch ~/.hushlogin` - Hide home screen message

## Essential Packages

```bash
# Core development tools
sudo apt install -y build-essential git python3 python3-pip \
    openjdk-17-jdk nodejs npm sshpass neovim wget curl

# Install OpenSSH client (default installed already), and server if needed
sudo apt install -y openssh-client
# sudo apt install -y openssh-server  # uncomment if you want SSH server inside WSL

# Enhanced shell tools
sudo apt install -y fish tmux tree colordiff bat eza tldr

# Optional Python utilities
sudo apt install -y pipx snapd
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
