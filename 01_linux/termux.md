# Termux

**Open Solid Explorer and navigate to `/data/data/com.termux/files/home/` the copy the .termux folder to take termux backup.**
**Similarly, copy .config folder to take fish shell backup. Save backup folders in OneDrive to access from any device**

**Navigate to termux root data folders and allow write permission to copied backup files from attributes in solid explorer.**

### Keep Termux Running in Background
- About App > Battery > Enable Run in Background.
- Recent > Lock in Recent.

## Basic to-dos

```bash
termux-change-repo > asia
termux-setup-storage
pkg update -y   and   pkg upgrade -y

# Install all packages first
chsh -s fish # fish as default shell 

cd /  # root storage 
cd /sdcard/  # main storage


which <pkg name> # show pkg path
pkg show <PKG name> # details about a package
```

___

### Packages

```bash
pkg install python git nodejs openssh curl wget openjdk-17 which fish -y # alias cat = bat
```

```bash
- termux-reload-settings # load the changes
- vol-up + k # hide/unhide termux bottom toolbar.
- termux-open file.txt / file.img # open files with termux
- termux-wake-lock/unlock # keep running/close after lock screen 
```

### Termux margin settings

- Just copy the backup folder of .termux to restore the settings.

```bash
nano ~/.termux/termux.properties
terminal-margin-horizontal=20
terminal-margin-vertical=10
```

### Font change

```bash
mkdir NerdFont > cd NerdFont > wget font_link > ls > unzip FiraCode.zip > rename mv font.ttf ~/.termux
```

### Termux Dracula Theme

>touch colors.properties

```bash
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

## Fish Config for Alias and Environment Variables

```bash
if status is-interactive
    # Commands to run in interactive sessions can go here
end

sshd

alias c='clear'
alias cl='clear'
alias cls='clear'

bind \t accept-autosuggestion
set -g fish_greeting ""
alias sf 'source ~/.config/fish/config.fish'

alias ip "ifconfig 2>/dev/null | awk '/inet / && \$2 !~ /127.0.0.1/ {i>
alias fish="cd ~/.config/fish/"

# ADB/Fastboot alias for MMRL Module Repo
alias adb='su -c adb'
alias fastboot='su -c fastboot'
```
## Fish Prompt
- `fish_config`: prompt tab > Informative Vcs (~ [1]$)
