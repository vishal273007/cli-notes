# VS Code Settings and Tips

## Basic Commands

### Open VS Code
- `code .` - Open current directory in VS Code
- `code filename.txt` - Open specific file in VS Code
- `cursor .` - Open current directory in Cursor
- `windsurf .` - Open current directory in Windsurf

## Core Shortcuts

### Navigation
- `Ctrl + `` ` - Toggle terminal
- `Ctrl + ,` - Open Settings
- `Ctrl + P` - Quick open files
- `Ctrl + Shift + P` - Command palette

### Editing
- `Alt + ↑/↓` - Move line up/down
- `Ctrl + D` - Select next occurrence
- `Ctrl + Shift + D` - Duplicate line
- `Alt + Z` - Toggle word wrap
- `Ctrl + /` - Toggle line comment

### Multi-cursor
- Hold `Alt` + Click - Add cursor
- `Ctrl + Alt + ↑/↓` - Add cursor above/below
- `Ctrl + Shift + L` - Select all occurrences

## Editor Configuration

### UI Settings
- **Minimap**: View > Appearance > Minimap > Toggle
- **Sticky Scroll**: 
  - Search: `sticky scroll`
  - Toggle `Editor > Sticky Scroll: Enabled`
- **Hover Behavior**:
  - Search: `hover sticky`
  - Toggle `Editor > Hover: Sticky`

### Formatting
- **Format on Save**: 
  - Search: `format on save`
  - Toggle `Editor: Format On Save`
- **Word Wrap**:
  - Search: `word wrap`
  - Set to `on` or `wordWrapColumn`

## Workspace Settings

### File Organization
```
project/
├── 01_HTML/
│   └── 01_Basics/
│       ├── 01_first.html
│       └── 02_anchor.html
└── .vscode/
    └── settings.json
```

### Excluding Files
Add to `settings.json`:
```json
{
    "files.exclude": {
        "**/.vscode": true,
        "**/gitignore": true,
        "**/*.class": true
    },
    "explorer.compactFolders": false
}
```

### Git Integration
1. Create `.gitignore` in root
2. Add:
   ```
   .vscode/
   *.class
   ```

## JSON Settings Reference

### settings.json
```json
{
    // Font settings
    "editor.fontFamily": "Consolas, 'Courier New', monospace",
    "editor.fontSize": 14,
    
    // Terminal settings
    "terminal.integrated.fontFamily": "FiraCode Nerd Font Medium",
    "terminal.integrated.fontWeight": "normal",
    "terminal.integrated.fontWeightBold": "normal",
    
    // Editor behavior
    "editor.suggest.overline": false,
    "editor.matchBrackets": "never",
    "editor.wordWrap": "on",
    
    // Code Runner
    "code-runner.clearPreviousOutput": true,
    "code-runner.runInTerminal": false
}
```

## Live Server Setup

### Installation
1. Install Node.js from [nodejs.org](https://nodejs.org/)
2. Verify installation:
   ```bash
   node --version
   npm --version
   ```
3. Install Live Server extension in VS Code

### Usage
- Right-click HTML file > "Open with Live Server"
- Or use command palette: "Live Server: Open with Live Server"

## Cursor Editor Features

### Agent Modes
1. **Ask Mode** - Get explanations about code
2. **Edit Mode** - Make direct code changes
3. **Agent Mode** - Full programming partner:
   - Handles complex, multi-step tasks
   - Combines Ask and Edit features
   - Provides explanations with changes
   - Suggests improvements

### Tips
- Use `@` to reference code
- Highlight code before asking questions
- Use natural language for requests

## Troubleshooting

### Extension Issues
1. Open Extensions view (`Ctrl+Shift+X`)
2. Disable extensions one by one
3. Restart editor after each change
4. Identify problematic extension

### Workspace Trust
To manage workspace trust:
1. Search: `workspace trust`
2. Navigate to: `Security > Workspace > Trust: Enabled`
3. Adjust settings as needed
- Install `cursor` (not `code .`) after installation.

## Cursor Shortcuts

- Ctrl + K = `Toggle inline / Terminal prompt bar` (Open command palette/AI command bar)
- Ctrl + L = `Ask(Open Chat) / Add selection to new chat`
- Ctrl + I = Agent(Composer{code generation}) - Opens the AI code generation in Chat. Used for generating new code or modifying existing code

- `Tab` = Accept suggestion
- `Ctrt + ->` = Accept next word

### Cursor Tips

- Enable `remember my preference` when using search web in cursor for chat.
- Use `Ctrl+K` for learning and assistant while coding. i.e. select one or whole lines of code and ask to add comments or change.
- Use `Context` like web or files options for more controlled assistance.

### Cursor Settings

- Change left Activity Bar orientation panel: `Ctrl + ,` > search "activity bar orientation" > Vertical.

- Change terminal shell to powershell: `Ctrl + ,` > search "terminal.integrated.defaultProfile" > change to "PowerShell".

- Well, it's all over. Now recreating account by deleting account to get free credits. Use the feature while the services are new till they are showing generosity to users, because they will soon implement the security to prevent free usage abuse.

- Delete account and re-login or Use `temp-mail` to check if credit resets. Developers know about free usage abuse. They will implement the security as people get used to using cursor.

- Cursor settings > import settings to copy VS Code settings.

___

### Windsurf

- Customize files in system folders: Open AI code editor as Administrator and do required edits with prompt.
- auto execution policy - `turbo`  to auto run commands.
- in windsurf, when running any command automatically, click on show/run command on the top right corner of command. then click on delete button on the main command line so it will automatically continue running.

- See free Credits usage: Windsurf - Settings at bottom right corner of chat window > Plan Info tab at bottom-left corner of the popup.

- Use `Ctrl + I` for AI code generation and `Ctrl + L`  for AI chat.

- Do not use the AI chat for long editing, instead use it for debugging and learning.

- As Cursor has been completely blocked, now stick with `Windsurf` for tiny credits and free low capable AI Assistant.

- Now use `Windsurf` with less free credits. Cursor, no longer usable for free users.

- Remember that AI editors with models like Claude, GPT 4o is incredibly impressive and very powerful, but very limited for free usage. So ensure to use it for important and complex tasks only.

- Now Windsurf gave few free credits with temp mail at 10:20 PM around. Credits was 0, so I opened Windsurf manually in Chrome, then signed out existing account, then created new account then opened Windsurf and logged in again, then it gave few credits.

<!--------------------------------------------------------------------------------------------------------------------------->

## MARKDOWN GUIDE

### Heading/Title

- `#` MAIN TOPIC
- `##` SUBTOPIC
- `###` SMALLER SECTION

### Text Styling

- `**Bold Text**`
- `_Italic Text_`
- `**_Bold and Italic_**`
- (`xyz`) for Highlight or main quote, tick will not be visible on the markdown viewer.

### Lists

`-`, `1.xyz` : Unordered Lists and Ordered Lists

### Horizontal Line

 `---`: for horizontal line

### Note

`>` for important notes

## Eclipse
<!-- ==== -->

### Basic Settings

- **Change theme**: Go to Windows --> Preferences --> General --> Appearance --> Theme: `DevStyle` Theme.
- **`Change font`**: ...Appearance --> Colors and Fonts --> Basic --> Text Font --> JetBrains Mono. Then Font style "Regular" and leave size default.

- **`Auto format source code`**: Go to Windows --> Preferences --> Java --> Editor --> Save Actions. Check "Perform the selected actions on save", Check "Format source code", Check "Format all lines", and Check "Organize imports".
- **`Enable autosave before run`**: Search for "build" in setting and enable "Save automatically before manual build".
- **`Nested Project Explorer`**: Project Explorer > three vertical dots > Package Presentation > Select Hierarchical.

___

**Disable forced comment formatting**:

- search formatter in settings.
- click edit(beside active profile).
- go to comment tab
- uncheck enable line comment formatting and block comment formatting.
- change the name from built-in to your any name.

- Change Output layout to right side of code editor: Hold the top edge of output windows and drag it to the position you want.

___

**Eclipse Marketplace**:

- Use the eclipse market place to download useful plugins and theme and many more. `Help --> Eclipse Marketplace` the use the search bar for your specific queries.

- Delete the .metadata folder in the username/eclipse-workspace to reset layout and font. it will fix the .project not found while opening the project.

## Eclipse Shortcuts

- **`Ctrl + Shift + F`**: To format code automatically.
- **`Ctrl + F11`**: Shortcut to run the code immediately.


<!------------------------------------------------------------------------------------------------------>

```text
Windsurf Chat:

Chat (question) - Gives knowledge and does not change code directly.
Code (give command) - directly edit the open code after clicking apply.
```

### VS Code Settings (settings.json)

#### Word Selection Highlight
Subtle, non-intrusive highlights for better code readability:

```json
"workbench.colorCustomizations": {
  "terminal.background": "#00000000",
  "editor.selectionHighlightBackground": "#6A995533",
  "editor.selectionHighlightBorder": "#6A995555",
  "editor.wordHighlightBackground": "#6A995522",
  "editor.wordHighlightStrongBackground": "#6A995522"
}