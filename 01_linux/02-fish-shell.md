# Fish Shell

## Installation

```bash
sudo apt install fish -y
```

Set as default shell
```bash
chsh -s $(which fish)
```

## Oh My Posh Setup

```bash
# 1. Create local bin and install Oh My Posh there
mkdir -p ~/.local/bin
curl -s https://ohmyposh.dev/install.sh | bash -s -- -d ~/.local/bin

# 2. Add Oh My Posh to PATH (add this line to config.fish)
set -gx PATH "$HOME/.local/bin" $PATH

# 3. Copy Agnoster themes to .poshthemes
mkdir -p ~/.poshthemes
cp agnoster.omp.json agnosterplus.omp.json ~/.poshthemes/

# 4. Initialize Oh My Posh with Agnoster theme (add this below PATH line in config.fish)
oh-my-posh init fish --config ~/.poshthemes/agnoster.omp.json | source

# 5. Restart fish or execute
exec fish
```

> Note: Ensure `agnoster.omp.json` and `agnosterplus.omp.json` are downloaded before copying.

---

## TMUX Configuration

### Startup Script

Create `~/.tmux-start.sh`:

```bash
#!/bin/bash
tmux new-session \; split-window -h \; select-pane -L
```

### Auto-start TMUX

Add to `config.fish`:

```fish
if status is-interactive
and not set -q TMUX
    exec ~/.tmux-start.sh
end
```

### Common TMUX Commands

* `Ctrl + b %` - Vertical split
* `Ctrl + b →/←` - Navigate panes
* `Ctrl + b :resize-pane -L 15` - Resize pane
* Mouse support: `setw -g mouse on` in `.tmux.conf`
