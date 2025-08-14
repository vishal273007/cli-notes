# Nvim Setup

> Write the code in Nvim and debug in the Cursor.

## Nvim

```bash
# Install latest nvim via snap
sudo snap install nvim --classic
```
- `nvim .` - open current dir in nvim

## NvChad Setup

<!-- Section Separator -->

### Installation

```bash
# Clean Nvim - Linux / MacOS (unix)
rm -rf ~/.config/nvim
rm -rf ~/.local/state/nvim
rm -rf ~/.local/share/nvim

# Install NcChad
git clone https://github.com/NvChad/starter ~/.config/nvim && nvim

# Run after Installation finishes
:MasonInstallAll

# Install language servers
:TSInstall java html css javascript

# Update
:Lazy sync
```

### Common Commands

- `Space th` - Themes
- `Space v/h` - Terminal split
- `Space ch` - Cheatsheet
- `Space /` - Toggle comment
- `Space fa/ff` - Find files
- `Tab` - Switch buffer

- `<C-g>` - (Control + g) Accept code completion

### Package Management

- `:Lazy sync` then use:
  - `H` - Check health
  - `I` - Install
  - `U` - Update
  - `S` - Sync
  - `C` - Clean

### Tips

- While in insert mode, hold Ctrl and use hjkl navigation keys to move cursor without leaving insert mode
- `Ctrl + w` then hjkl to switch between windows, or press `Ctrl + w` twice for switching between two windows
- In editor: press Esc then `Space h` to open terminal (it opens in insert mode)
- `Ctrl + h/l` to switch windows in nvim, `a` to insert after cursor (`i` to insert before cursor)

### Troubleshooting

- After AI-suggested changes in code editor, run `:MasonInstallAll` followed by `:Lazy sync` in nvim
- For fixing issues, open the files directory with an AI code editor for context-aware problem solving
- Java LSP setup note (28-Feb-2024): Successfully configured using Claude 3.7 Sonnet through Windsurf

- To use Codeium autocompletion plugin after reinstallation, use the :Codeium Auth enter API key.
