# Aliases and config file

Dir: `~/.config/fish/aliases.fish`

```bash
# Add 'source ~/.config/fish/aliases.fish' to the main config.fish file for external aliases file.
source ~/.config/fish/aliases.fish

# File and Directory Navigation
alias c='clear'                   # Clear the terminal screen.
alias cl='clear'                  # Another clear alias.
alias cls='clear'                 # Clear alias for Windows.

alias fish="cd ~/.config/fish/"   # Navigate to the Fish shell configuration folder.
alias downloads="cd /mnt/d/Downloads"  # Navigate to Windows Downloads folder.
alias desktop="cd /mnt/c/Users/Vishal\ Vishwakarma/Desktop"  # Navigate to Windows Desktop folder.
alias users="cd /mnt/c/Users/Vishal\ Vishwakarma"  # Navigate to Vishal Vishwakarma's home directory in Windows.

# Git Aliases
alias gs="git status"             # Check the status of the Git repository.
alias gcp="git add . && git commit -m 'updated' && git push"  # Stage, commit, and push changes in one command.
alias gl="git log --oneline --graph --decorate"  # Show a concise and visual Git history.

# Tmux
alias tmux="~/.tmux-start.sh"     # Start tmux using a custom script.

# SSH to Windows
alias sshwindows="~/.ssh_login_windows.fish"   # SSH login to Windows.
alias sqlplus="~/.sqlplus_remote_login.fish"   # SQLPlus remote login alias.

# bat (cat) and eza/exa (ls - Enhanced File Listings with icons)
alias cat='batcat'                 # Use bat as a replacement for cat.

# Use eza as the ls replacement with icons and custom exclusions
function ls --wraps eza
    eza --icons --ignore-glob="snap|*.class" $argv
end

alias ll="eza -l --icons"          # Long format with icons.
alias la="eza -la --icons"         # List all files (including hidden) with icons.
alias lt="eza --tree --icons"      # Display files in a tree structure with icons.
alias l.="eza -d .* --icons"       # List hidden directories with icons.

# Programming Languages
alias python="python3"  # Use Python 3 by default.

# Network
# alias ip='ipconfig.exe | grep "IPv4 Address" | grep "192.168."'  # Filtered IPv4 address for 192.168...
alias ip="ipconfig.exe | awk '/IPv4 Address/ && !/169.254/ {print \$0} /Default Gateway/ && \$NF ~ /[0-9]/ {print \$0}'"

# Other Custom Aliases
alias update='sudo apt update && sudo apt upgrade -y'  # Update and upgrade system packages.
```
<!-- ================================================================== -->

## Fish Configuration File

Add to `~/.config/fish/config.fish`:

```bash
# Check if the shell session is interactive
if status is-interactive
    # Commands specific to interactive sessions can go here.
end

# Bind tab key to accept-autosuggestion
bind \t accept-autosuggestion

# =========================================================================
# Fish Greeting
set -g fish_greeting ""

# Source additional aliases from an external file.
source ~/.config/fish/aliases.fish

# Reload the Fish shell configuration.
alias sf 'source ~/.config/fish/config.fish'

# =========================================================================
# Oh My Posh Initialization
# Initialize Oh My Posh with the specified theme configuration.
oh-my-posh init fish --config ~/agnoster.omp.json | source

# Alternative initialization for Oh My Posh with a cached theme configuration.
eval "$(~/.local/bin/oh-my-posh init fish --config ~/.cache/oh-my-posh/themes/agnoster.omp.json)"

# =========================================================================
# Environment variables
# Environment variable in fish "set -x PATH $PATH:/mnt..." (set -x VAR value) (export VAR=value - in bash/zsh).
# -x flag for child processes, and -gx flag for increase scope to global.

set -gx PATH $PATH /snap/bin # environment variable for neovim
set -x PATH $PATH:/mnt/c/Windows/System32 # env for ipconfig.exe | grep IPv4

# for using Windows path adb from Linux:
set -x PATH $PATH /mnt/c/tools/platform-tools

# fastboot alias for fastboot.exe
alias fastboot="fastboot.exe"

# =========================================================================
# sqlplus function with custom commands in c:\tools\commands.sql and 'cl scr and set linesize 100'
function sqlplus
    sshpass -p '12513365@Ms' ssh -t "vishal vishwakarma@vishal" "sqlplus system/tiger @C:\\tools\\commands.sql"
end

# Keep ubuntu running in background
nohup sleep infinity &>/dev/null &; disown

# function to run java program as 'run <filename>.java'
function run
    javac $argv[1] && java (basename $argv[1] .java)
end

# Set windows host browser as wsl browser as as well for live server
set -x BROWSER "/mnt/c/Program Files/Google/Chrome/Application/chrome.exe"

# ssh for nord 4
function sshnord4
    sshpass -p 'ssh@nord4' ssh -p 8022 u0_a363@192.168.0.142
end

# =========================================================================

# shortcut for running adv java programs with 'run' from '../lib/run.sh'
# in the dir /home/vishal/AdvJava/lib/(run.sh and ojdbc8.jar)
# function run
    # ../lib/run.sh $argv
# end

# run.sh file content in AdvJava/lib/ folder
# ```bash
# #!/bin/bash
# SCRIPT_DIR="$( cd "$( dirname "${BASH_SOURCE[0]}" )" && pwd )"

# SRC_DIR="$SCRIPT_DIR/../src"
# BIN_DIR="$SCRIPT_DIR/../bin"

# javac -d "$BIN_DIR" "$SRC_DIR/$1" && java -cp "$BIN_DIR:$SCRIPT_DIR/ojdbc8.jar" "$(basename "$1" .java)"
# ```
```
