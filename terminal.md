# Terminal

> Try multiple resources (ChatGPT, Claude, Google) when solving a problem.
> Read official docs(documentation) and use keyboard-only in Linux.
> Codeium: Ctrl + I (to open and ask queries)

## Windows Terminal Theme

- `Settings(Ctrl + ,)` -> `Default profile` -> `Color Schemes` -> Choose `Dracula`.
- Add Dracula theme terminal:
- add theme code in profile.json file in `"schemes": [ code here ],` (ask theme code from multiple ai assistant).
- code:

```bash
{
    "name": "Dracula",
    "background": "#282A36",
    "black": "#21222C",
    "blue": "#BD93F9",
    "brightBlack": "#6272A4",
    "brightBlue": "#D6ACFF",
    "brightCyan": "#A4FFFF",
    "brightGreen": "#69FF94",
    "brightPurple": "#FF92DF",
    "brightRed": "#FF6E6E",
    "brightWhite": "#FFFFFF",
    "brightYellow": "#FFFFA5",
    "cursorColor": "#F8F8F2",
    "cyan": "#8BE9FD",
    "foreground": "#F8F8F2",
    "green": "#50FA7B",
    "purple": "#FF79C6",
    "red": "#FF5555",
    "selectionBackground": "#44475A",
    "white": "#F8F8F2",
    "yellow": "#F1FA8C"
}
```

### Hide Windows Terminal right status/scroll bar -  

```json
"profiles": {
    "defaults": {
        // other settings
        },
        // other lines
        "useAcrylic": true,
        "scrollbarState": "hidden"  // Add this line here
    },
  "list": []
```

### Settings

- Settings > Startup tab > Default profile > Ubuntu

### Default profile

- Color Scheme: Dracula
### Open Ubuntu in current folder:
    - Terminal > Settings > Profile Name: Ubuntu
    - Left-side Profiles > Ubuntu.
    - Command line: wsl.exe [Right-click: Opens in current folder]
    - Starting directory: \\wsl$\Ubuntu\home\ubuntu [Search to launch in home]

    
- Font face: FiraCode Nerd Font
- Font-size/Font-weight: 11 / Medium

- Cursor shape - bar: Set in default and Ubuntu both tab
- Transparency- Background Opacity: 80%, Enable acrylic material
- Padding: 12

- Delete a profile: Settings --> Profile --> Scroll --> Delete profile.

**Fira Code font download** : Search fira code download > Google font > Get font > Download all > Extract > Static folder files > select all and right click > Install.

### Startup section > Launch parameters

- Launch mode: Focus/Default
- Launch size: Column: 130, Row: 35
- Launch positions: `Center on launch` (OR) `X:405, Y: 220`.

- In Interaction section, disable `Warn when closing more than one tab`.

- **`F11`**: Full screen

### Update windows apps with `winget`

winget is package manager for windows. It is similar to `apt` in linux. Package manager is powerful way to manage windows apps. Install apps with `winget install` and update with `winget upgrade`. It is recommended to use because faster way to install apps than download and install manually.

```bash
winget upgrade --all (similar to `apt upgrade -y`)
```

_Reset Terminal:_

- `Installed apps` > Search `terminal` > `Advance options` > `Reset`.


