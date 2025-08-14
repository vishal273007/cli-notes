# Fish Shell

## Installation

```bash
# Add repository
sudo apt-add-repository ppa:fish-shell/release-3
sudo apt update

# Install fish
sudo apt install fish -y

# Set as default shell
chsh -s $(which fish)
```

### Oh My Posh Setup

```bash
# Install Oh My Posh
curl -s https://ohmyposh.dev/install.sh | bash

# Setup Agnoster theme

wget https://raw.githubusercontent.com/JanDeDobbeleer/oh-my-posh/main/themes/agnoster.omp.json -O ~/agnoster.omp.json

# Add to Fish config
fish_add_path ~/.local/bin
eval "$(~/.local/bin/oh-my-posh init fish --config ~/agnoster.omp.json)"
```


## TMUX Configuration

### Startup Script

Create `~/.tmux-start.sh`:

```bash
#!/bin/bash
tmux new-session \; split-window -h \; select-pane -L
```

### Auto-start TMUX

Add to `config.fish`:

```bash
if status is-interactive
and not set -q TMUX
    exec ~/.tmux-start.sh
end
```

### Common TMUX Commands

- `Ctrl + b %` - Vertical split
- `Ctrl + b →/←` - Navigate panes
- `Ctrl + b :resize-pane -L 15` - Resize pane
- Mouse support: `setw -g mouse on` in `.tmux.conf`
