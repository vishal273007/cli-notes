# Termux

## Basic to-dos

```bash
termux-change-repo > asia
termux-setup-storage
pkg update -y && pkg upgrade -y

pkg install fish -y && chsh -s fish # install and set fish as default shell 
# `fish_config` -> prompt tab -> Informative Vcs (~ [1]$)
```
___

### Packages

```bash
# Install all packages first
pkg install python git openssh busybox curl wget which eza bat tree -y

# verify installation with path
which busybox 

Use 3C Toolbox Task Manager to see how much CPU sshd and busybox ftp is consuming in/with Termux.
```


### Clean Space

```bash
# Verify size before and after cleaning
du -h -d 0 ../usr/

#Check what is consuming the space in termux
du -h -d 1 ../usr | sort -hr | head -n 5
du -h -d 1 ~ | sort -hr | head -n 5 # Home folder

# Remove heavy compiler tools
apt remove clang llvm lld libcompiler-rt ndk-sysroot ..... -y

# Remove unused
apt autoremove
apt clean
```


### Termux margin settings

```bash
# nano ~/.termux/termux.properties
terminal-margin-horizontal=20
terminal-margin-vertical=10
```

### Font change

```bash
mkdir NerdFont > cd NerdFont > wget font_link > ls > unzip FiraCode.zip > mv font.ttf ~/.termux
```

### Termux Dracula Theme

```bash
# nano ~/.termux/colors.properties
# paste the following
background=#282A36
foreground=#F8F8F2
cursor=#F8F8F2

color0=#21222C
color1=#FF5555
color2=#50FA7B
color3=#F1FA8C
color4=#BD93F9
color5=#FF79C6
color6=#8BE9FD
color7=#F8F8F2

color8=#6272A4
color9=#FF6E6E
color10=#69FF94
color11=#FFFFA5
color12=#D6ACFF
color13=#FF92DF
color14=#A4FFFF
color15=#FFFFFF
```

## config.fish file

```bash
if status is-interactive
    # Commands to run in interactive sessions can go here
end

termux-wake-lock # run command while screen off

sshd
# Busybox ftp - Just install busybox and add this line in config file - Done!
pgrep -f "tcpsvd.*9999" >/dev/null || busybox tcpsvd -vE 0.0.0.0 9999 busybox ftpd -w /sdcard &  # & - run in background (for any foreground tasks)

alias c='clear'
alias cls='clear'

bind \t accept-autosuggestion
set -g fish_greeting ""
alias sf 'source ~/.config/fish/config.fish'

alias ip "ifconfig 2>/dev/null | awk '/inet / && \$2 !~ /127.0.0.1/ {i>
alias fish="cd ~/.config/fish/"

# ADB/Fastboot alias for MMRL Module Repo
alias adb='su -c adb'
alias fastboot='su -c fastboot'


# eza - replacement of ls
function ls --wraps eza
    eza --icons --ignore-glob="snap|*.class" $argv
end

alias ll="eza -l --icons"          # Long format with icons.
alias la="eza -la --icons"         # List all files (including hidden) with icons.
alias lt="eza --tree --icons"      # Display files in a tree structure with icons.
alias l.="eza -d .* --icons"       # List hidden directories with icons.

# bat (cat) and eza/exa (ls - Enhanced File Listings with icons)
alias cat='batcat'              # Use bat as a replacement for cat
```


## Termux Autostart on boot

1. Install Termux:Boot from F-Droid.
2. Open the Termux:Boot app once to enable it.
3. Disable battery optimization for Termux and Termux:Boot.
4. Run `mkdir -p ~/.termux/boot` in Termux.
5. Create `~/.termux/boot/start-termux` with:
   ```bash
   #!/data/data/com.termux/files/usr/bin/sh
   termux-wake-lock
   sshd
   pgrep -f "tcpsvd.*9999" >/dev/null || busybox tcpsvd -vE 0.0.0.0 9999 busybox ftpd -w /sdcard &   
   ```
6. Make it executable: `chmod +x ~/.termux/boot/start-termux`.
7. Reboot. Termux will run in background with notification (may take ~60s after unlock).

## Termux Battery consumption by constant autorun

- Idle (background, no wakelock): Negligible drain, ~0-1% per hour.

- FTP server (background with wakelock): 2-10% per hour, varies by device/activity.


