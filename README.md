# Kitty Terminal Configuration - Complete Guide

A highly optimized Kitty terminal configuration with advanced window management, beautiful theming, and powerful productivity features.

## Table of Contents

- [Installation](#installation)
- [Quick Start](#quick-start)
- [Performance Features](#performance-features)
- [Visual Customization](#visual-customization)
- [Tab Management](#tab-management)
- [Window/Pane Management](#windowpane-management)
- [Advanced Window Management](#advanced-window-management)
- [Layout System](#layout-system)
- [OS Window Management](#os-window-management)
- [Navigation & Focus](#navigation--focus)
- [Clipboard Operations](#clipboard-operations)
- [Scrolling & History](#scrolling--history)
- [URL Handling](#url-handling)
- [Mouse Support](#mouse-support)
- [Nvim Integration](#nvim-integration)
- [Remote Control](#remote-control)
- [Troubleshooting](#troubleshooting)
- [Tips & Tricks](#tips--tricks)

---

## Installation

### Prerequisites

```bash
# Install Kitty terminal
# macOS
brew install kitty

# Ubuntu/Debian
sudo apt install kitty

# Arch Linux
sudo pacman -S kitty

# Install Hack Nerd Font (required)
# Download from: https://www.nerdfonts.com/font-downloads
```

### Setup

1. **Backup your current config:**
   ```bash
   cp ~/.config/kitty/kitty.conf ~/.config/kitty/kitty.conf.backup
   ```

2. **Install the new config:**
   ```bash
   cp kitty.conf ~/.config/kitty/kitty.conf
   ```

3. **Download Catppuccin Mocha theme OR SET IT USING kitty +kitten themes:**
   ```bash
   cd ~/.config/kitty
   curl -O https://raw.githubusercontent.com/catppuccin/kitty/main/themes/mocha.conf
   mv mocha.conf current-theme.conf
   ```

4. **Reload Kitty:**
   - Press `Ctrl+Alt+R`
   - Or restart Kitty

---

## Quick Start

### Essential Keybindings

| Action | Keybinding |
|--------|-----------|
| New tab | `Ctrl+T` |
| Close tab | `Ctrl+Shift+W` |
| Vertical split | `Alt+\` |
| Horizontal split | `Alt+-` |
| Navigate windows | `Alt+H/J/K/L` |
| Cycle layouts | `Ctrl+Shift+F` |
| Reload config | `Ctrl+Alt+R` |

---

## Performance Features

### Optimized Rendering

- **Repaint Delay:** Reduced to 10ms for smoother rendering
- **Input Delay:** Lowered to 3ms for better responsiveness
- **Monitor Sync:** Screen redraws synced to your monitor's refresh rate

```conf
repaint_delay 10
input_delay 3
sync_to_monitor yes
```

### Cursor Effects

- **Cursor Trail:** Visual trail showing last 3 cursor positions
- **Trail Decay:** Smooth fade from 10% to 40% opacity

```conf
cursor_trail 3
cursor_trail_decay 0.1 0.4
```

---

## Visual Customization

### Window Appearance

- **Minimal borders:** 1pt thin borders around windows
- **No title bar:** OS decorations hidden for clean look
- **Active window:** Bright green border (`#00ff00`)
- **Inactive windows:** Dark gray border (`#282828`)

### Transparency & Blur

- **Background opacity:** 95% opaque (5% transparent)
- **Inactive opacity:** 70% for inactive text
- **Background blur:** Slight blur effect for aesthetics

```conf
background_opacity 0.95
inactive_text_alpha 0.7
background_blur 1
```

### Spacing

```conf
window_margin_width 5      # Outer margin
single_window_margin_width 0
window_padding_width 2     # Inner padding
```

### Font Configuration

- **Font:** Hack Nerd Font (13pt)
- **Ligatures:** Enabled for programming symbols
- **Auto-styling:** Bold, italic, and bold-italic automatically selected

#### Font Size Adjustment

| Action | Keybinding |
|--------|-----------|
| Increase size | `Ctrl+=` |
| Decrease size | `Ctrl+-` |
| Reset to default | `Cmd+0` |

---

## Tab Management

### Tab Bar Style

- **Position:** Top of window
- **Style:** Powerline with angled separators
- **Active tab:** Bold italic `[1: title]`
- **Inactive tabs:** Normal `2: title`

### Tab Navigation

| Action | Keybinding |
|--------|-----------|
| New tab | `Ctrl+T` |
| Close tab | `Ctrl+Shift+W` |
| Next tab | `Ctrl+Tab` |
| Previous tab | `Ctrl+Shift+Tab` |
| Go to tab 1-9 | `Alt+1` to `Alt+9` |
| Go to tab 10 | `Alt+0` |

### Tab Management

| Action | Keybinding |
|--------|-----------|
| Move tab left | `Ctrl+Shift+Page Up` |
| Move tab right | `Ctrl+Shift+Page Down` |
| New tab (same dir) | `Ctrl+Shift+N` |

---

## Window/Pane Management

### Creating Splits

| Action | Keybinding |
|--------|-----------|
| Horizontal split | `Alt+-` |
| Vertical split | `Alt+\` |
| New window (same dir) | `Ctrl+Shift+Enter` |

Both split commands open in the current working directory.

### Navigating Between Windows

Use Vim-style navigation:

| Direction | Keybinding |
|-----------|-----------|
| Left | `Alt+H` |
| Down | `Alt+J` |
| Up | `Alt+K` |
| Right | `Alt+L` |

Alternative arrow key navigation:

| Direction | Keybinding |
|-----------|-----------|
| Left | `Ctrl+Shift+Left` |
| Down | `Ctrl+Shift+Down` |
| Up | `Ctrl+Shift+Up` |
| Right | `Ctrl+Shift+Right` |

### Resizing Windows

#### Fine Resizing (Default increments)

| Action | Keybinding |
|--------|-----------|
| Taller | `Alt+Shift+K` |
| Shorter | `Alt+Shift+J` |
| Wider | `Alt+Shift+H` |
| Narrower | `Alt+Shift+L` |

#### Coarse Resizing (10-step increments)

| Action | Keybinding |
|--------|-----------|
| Taller | `Ctrl+Shift+Alt+Down` |
| Shorter | `Ctrl+Shift+Alt+Up` |
| Wider | `Ctrl+Shift+Alt+Right` |
| Narrower | `Ctrl+Shift+Alt+Left` |

#### Interactive Resizing

Press `Ctrl+Shift+R` to enter resize mode, then use arrow keys to resize. Press `Esc` to exit.

### Moving Windows

Move windows within the current tab:

| Direction | Keybinding |
|-----------|-----------|
| Up | `Shift+Ctrl+Alt+K` |
| Down | `Shift+Ctrl+Alt+J` |
| Left | `Shift+Ctrl+Alt+H` |
| Right | `Shift+Ctrl+Alt+L` |

Other movement options:

| Action | Keybinding |
|--------|-----------|
| Move to top | `Ctrl+Shift+M` |
| Move forward | `Ctrl+Shift+,` |
| Move backward | `Ctrl+Shift+.` |

---

## Advanced Window Management

### Window Control

| Action | Keybinding |
|--------|-----------|
| Close window | `Ctrl+Shift+Q` |
| Detach window | `Ctrl+Shift+X` |
| Swap window | `Ctrl+Shift+Alt+Space` |
| Reset sizes | `Ctrl+Shift+E` |

**Note:** Detach window moves the current window to a new tab.

### Move to Screen Edges

Position windows at screen boundaries:

| Edge | Keybinding |
|------|-----------|
| Left edge | `Ctrl+Shift+Alt+Left` |
| Right edge | `Ctrl+Shift+Alt+Right` |
| Top edge | `Ctrl+Shift+Alt+Up` |
| Bottom edge | `Ctrl+Shift+Alt+Down` |

---

## Layout System

Kitty uses a powerful layout system that determines how windows are arranged. Think of layouts as different tiling patterns.

### Available Layouts

1. **Splits** - Manual splitting (flexible)
2. **Tall** - One main window on left, stack on right
3. **Fat** - One main window on top, stack on bottom
4. **Stack** - All windows stacked, only one visible at a time
5. **Grid** - Windows arranged in a grid pattern
6. **Horizontal** - Windows stacked horizontally
7. **Vertical** - Windows stacked vertically

### Cycling Layouts

| Action | Keybinding |
|--------|-----------|
| Next layout | `Ctrl+Shift+F` |
| Previous layout | `Ctrl+Shift+D` |
| Toggle stack | `Ctrl+Shift+Space` |

### Direct Layout Selection

Jump directly to a specific layout:

| Layout | Keybinding |
|--------|-----------|
| Tall | `Ctrl+Shift+Alt+T` |
| Stack | `Ctrl+Shift+Alt+S` |
| Fat | `Ctrl+Shift+Alt+F` |
| Grid | `Ctrl+Shift+Alt+G` |
| Horizontal | `Ctrl+Shift+Alt+H` |
| Vertical | `Ctrl+Shift+Alt+V` |
| Splits | `Ctrl+Shift+Alt+P` |

### Layout Actions

| Action | Keybinding |
|--------|-----------|
| Rotate layout | `Ctrl+Alt+Space` |
| Mirror layout | `Ctrl+Alt+M` |
| Toggle mirror | `Ctrl+Alt+Shift+Space` |
| Balance bias | `Ctrl+Alt+B` |
| Fullscreen | `F11` |

### Stack Layout Management

When using the stack layout:

| Action | Keybinding |
|--------|-----------|
| Focus visible window | `Ctrl+Shift+=` |
| Previous window | `Ctrl+Shift+-` |

---

## OS Window Management

OS windows are separate terminal windows (not tabs or panes).

| Action | Keybinding |
|--------|-----------|
| New OS window | `Ctrl+Shift+Alt+N` |
| Next OS window | `Ctrl+Shift+Alt+]` |
| Previous OS window | `Ctrl+Shift+Alt+[` |
| Close OS window | `Ctrl+Shift+Alt+W` |

---

## Navigation & Focus

### Focus Window by Number

Quickly jump to a specific window:

| Window | Keybinding |
|--------|-----------|
| Window 1 | `Ctrl+1` |
| Window 2 | `Ctrl+2` |
| Window 3 | `Ctrl+3` |
| ... | ... |
| Window 9 | `Ctrl+9` |
| Window 10 | `Ctrl+0` |

### Marks and Navigation

Create marks to jump between specific points:

| Action | Keybinding |
|--------|-----------|
| Create mark | `Ctrl+Shift+;` |
| Remove mark | `Ctrl+Shift+A` |
| Jump to prev mark | `Ctrl+Shift+Up` |
| Jump to next mark | `Ctrl+Shift+Down` |

---

## Clipboard Operations

### System Clipboard

| Action | Keybinding |
|--------|-----------|
| Copy | `Ctrl+Shift+C` |
| Paste | `Ctrl+Shift+V` |
| Paste | `Shift+Insert` |

### Internal Buffers

Kitty has internal clipboard buffers for advanced copy/paste:

| Action | Keybinding |
|--------|-----------|
| Copy to buffer 'a' | `Ctrl+Shift+Alt+C` |
| Paste from buffer 'a' | `Ctrl+Shift+Alt+V` |

---

## Scrolling & History

### Line Scrolling

| Action | Keybinding |
|--------|-----------|
| Scroll up (line) | `Ctrl+Shift+Page Up` |
| Scroll down (line) | `Ctrl+Shift+Page Down` |

### Jump to Edges

| Action | Keybinding |
|--------|-----------|
| Scroll to top | `Ctrl+Shift+Home` |
| Scroll to bottom | `Ctrl+Shift+End` |

### Prompt Navigation

| Action | Keybinding |
|--------|-----------|
| Previous prompt | `Ctrl+Alt+Home` |
| Next prompt | `Ctrl+Alt+End` |

### Clear Screen

| Action | Keybinding |
|--------|-----------|
| Clear screen & scrollback | `Ctrl+Shift+Delete` |

---

## URL Handling

### Features

- **Auto-detection:** URLs automatically detected and underlined
- **Style:** Curly underline for visual clarity
- **Supported protocols:** HTTP, HTTPS, FTP, SSH, Git, Mailto, and more

### Open URLs

| Action | Keybinding |
|--------|-----------|
| Open URL hints | `Ctrl+Shift+U` |
| Click URL | `Ctrl+Click` |

When you press `Ctrl+Shift+U`, letters appear next to each URL. Type the letter to open that URL.

---

## Mouse Support

### Basic Mouse Actions

| Action | Mouse Gesture |
|--------|---------------|
| Select text | Click + Drag |
| Select word | Double-click |
| Select line | Triple-click |
| Paste selection | Middle-click |
| Show command output | Right-click |

### Advanced Mouse

| Action | Mouse Gesture |
|--------|---------------|
| Move window | `Ctrl+Shift+Left Drag` |

---

## Nvim Integration

### Kitty-Scrollback.nvim

Browse and search terminal output in Neovim with full text editing capabilities.

| Action | Keybinding |
|--------|-----------|
| Browse scrollback | `Ctrl+Shift+H` |
| Last command output | `Ctrl+Shift+G` |
| Clicked command | `Ctrl+Shift+Right-click` |

**Requirements:**
- Neovim installed
- kitty-scrollback.nvim plugin installed at:
  `~/.local/share/nvim/lazy/kitty-scrollback.nvim/`

### Features

- Full Vim navigation and search in terminal history
- Copy text easily with Vim commands
- Syntax highlighting for command output
- Filter and search through large outputs

---

## Remote Control

### Configuration

Remote control is enabled via Unix socket:

```conf
allow_remote_control yes
listen_on unix:/tmp/kitty
```

### Usage

Control Kitty from the command line or scripts:

```bash
# Get list of windows
kitty @ ls

# Create new window
kitty @ launch --type=window

# Send text to a window
kitty @ send-text "echo hello\n"

# Set window title
kitty @ set-window-title "My Window"

# Close window
kitty @ close-window

# Get colors
kitty @ get-colors

# Set colors dynamically
kitty @ set-colors background=#1e1e2e
```

### Example Scripts

**Auto-split for development:**
```bash
#!/bin/bash
# Open editor in left pane, terminal in right
kitty @ launch --location=vsplit nvim
kitty @ focus-window --match neighbor:left
```

**Send command to all windows:**
```bash
#!/bin/bash
# Broadcast a command
for window in $(kitty @ ls | jq -r '.[].tabs[].windows[].id'); do
    kitty @ send-text --match id:$window "clear\n"
done
```

---

## Broadcast Kitten

Send input to multiple windows simultaneously (like tmux synchronize-panes).

| Action | Keybinding |
|--------|-----------|
| Toggle broadcast | `Ctrl+Shift+B` |

Use cases:
- Configure multiple servers simultaneously
- Run the same command in multiple environments
- Synchronized testing across panes

---

## Configuration Management

| Action | Keybinding |
|--------|-----------|
| Reload config | `Ctrl+Alt+R` |
| Edit config | `Ctrl+Shift+Alt+,` |
| Debug config | `Ctrl+Shift+Alt+D` |

### Edit Config

Press `Ctrl+Shift+Alt+,` to open `kitty.conf` in your default editor.

### Debug Mode

Press `Ctrl+Shift+Alt+D` to see:
- Current configuration values
- Active keybindings
- Layout information
- Debug logging

---

## Troubleshooting

### Fonts Not Displaying Correctly

1. **Install Hack Nerd Font:**
   ```bash
   # macOS
   brew tap homebrew/cask-fonts
   brew install font-hack-nerd-font
   
   # Linux - download from nerdfonts.com
   ```

2. **Verify font installation:**
   ```bash
   kitty + list-fonts | grep Hack
   ```

3. **Update font cache (Linux):**
   ```bash
   fc-cache -fv
   ```

### Theme Not Loading

1. **Check theme file exists:**
   ```bash
   ls ~/.config/kitty/current-theme.conf
   ```

2. **Download Catppuccin Mocha:**
   ```bash
   cd ~/.config/kitty
   curl -O https://raw.githubusercontent.com/catppuccin/kitty/main/themes/mocha.conf
   mv mocha.conf current-theme.conf
   ```

3. **Or comment out the include:**
   ```conf
   # include current-theme.conf
   ```

### Keybindings Not Working

1. **Check for conflicts:**
   ```bash
   kitty @ debug-config
   ```

2. **Test in isolation:**
   ```bash
   kitty --override 'map ctrl+shift+f next_layout'
   ```

3. **Check terminal mode:**
   Some keybindings may be captured by shell or applications.

### Nvim Integration Not Working

1. **Verify plugin installation:**
   ```bash
   ls ~/.local/share/nvim/lazy/kitty-scrollback.nvim/
   ```

2. **Check Python path:**
   ```bash
   which python3
   ```

3. **Install lazy.nvim plugin manager:**
   Follow instructions at: https://github.com/folke/lazy.nvim

### Performance Issues

1. **Reduce transparency:**
   ```conf
   background_opacity 1.0
   background_blur 0
   ```

2. **Disable cursor trail:**
   ```conf
   cursor_trail 0
   ```

3. **Increase delays:**
   ```conf
   repaint_delay 20
   input_delay 5
   ```

### Splits Not Working

1. **Check layout enabled:**
   ```conf
   enabled_layouts splits,stack,tall
   ```

2. **Verify working directory:**
   ```bash
   # Ensure shell integration is working
   echo $KITTY_INSTALLATION_DIR
   ```

---

## Tips & Tricks

### 1. Quick Project Setup

Create a startup script:

```bash
#!/bin/bash
# ~/bin/dev-setup.sh

# Open editor in main pane
kitty @ launch --location=vsplit --cwd=~/projects/myapp nvim

# Split horizontally for terminal
kitty @ launch --location=hsplit --cwd=~/projects/myapp

# Focus on editor
kitty @ focus-window --match neighbor:left
```

Then map it:
```conf
map ctrl+shift+p launch ~/bin/dev-setup.sh
```

### 2. Session Management

Save your layout:
```bash
kitty @ ls > ~/kitty-session.json
```

Restore later:
```bash
# Parse and recreate layout from saved session
# (Requires custom scripting)
```

### 3. Dynamic Color Schemes

Switch themes on the fly:
```bash
# Dark mode
kitty @ set-colors ~/.config/kitty/themes/dark.conf

# Light mode  
kitty @ set-colors ~/.config/kitty/themes/light.conf
```

### 4. Workspace Layouts

Create layout presets:

```conf
# Add to kitty.conf
map ctrl+shift+alt+1 combine : goto_layout tall : launch --location=vsplit
map ctrl+shift+alt+2 combine : goto_layout stack : launch
map ctrl+shift+alt+3 combine : goto_layout grid : launch : launch : launch
```

### 5. Smart Window Titles

Auto-set window titles based on current command:

```bash
# Add to .bashrc or .zshrc
precmd() {
  echo -ne "\033]0;${PWD##*/}\007"
}
```

### 6. Quick Notes Window

Open a scratchpad:
```conf
map ctrl+shift+grave launch --type=overlay --hold nvim ~/notes/scratch.md
```

### 7. Multi-Directory Development

Open related projects in tabs:
```bash
#!/bin/bash
kitty @ launch --type=tab --cwd=~/projects/frontend
kitty @ launch --type=tab --cwd=~/projects/backend  
kitty @ launch --type=tab --cwd=~/projects/docs
kitty @ set-tab-title --match index:1 "Frontend"
kitty @ set-tab-title --match index:2 "Backend"
kitty @ set-tab-title --match index:3 "Docs"
```

### 8. Conditional Layouts

Different layouts for different tab counts:

```bash
# In your shell config
kitty_smart_layout() {
  local count=$(kitty @ ls | jq '[.[].tabs[].windows] | length')
  if [ $count -lt 3 ]; then
    kitty @ goto-layout tall
  else
    kitty @ goto-layout grid
  fi
}
```

### 9. Background Opacity Hotkey

Toggle transparency:
```conf
# Add action alias
action_alias transparent_toggle toggle_opacity 0.95 1.0

# Map to key
map ctrl+shift+o transparent_toggle
```

### 10. URL Handler Customization

Open URLs in specific applications:
```conf
# Open GitHub URLs in browser, others in terminal
protocol_handler git+https launch --type=background gh browse
```

---

## Advanced Workflows

### Full-Stack Development Layout

```
┌─────────────────┬──────────────┐
│                 │              │
│   Code Editor   │  File Tree   │
│   (Neovim)      │    (lf)      │
│                 │              │
├─────────────────┴──────────────┤
│                                │
│   Terminal / Server Logs       │
│                                │
└────────────────────────────────┘
```

Setup:
1. Press `Alt+\` to split vertically (editor | file tree)
2. Navigate to left: `Alt+H`
3. Press `Alt+-` to split horizontally (editor over terminal)
4. Press `Ctrl+Shift+Alt+T` to switch to tall layout
5. Adjust sizes with `Alt+Shift+H/L`

### DevOps Multi-Server Management

```
┌──────────┬──────────┬──────────┐
│ Server 1 │ Server 2 │ Server 3 │
│          │          │          │
├──────────┼──────────┼──────────┤
│ Server 4 │ Server 5 │ Server 6 │
│          │          │          │
└──────────┴──────────┴──────────┘
```

Setup:
1. Create 6 windows with `Ctrl+Shift+Enter` (5 times)
2. Press `Ctrl+Shift+Alt+G` to switch to grid layout
3. SSH into each server
4. Press `Ctrl+Shift+B` to broadcast commands

### Monitoring Dashboard

```
┌─────────────────────────────────┐
│   Main Logs (htop/btm)          │
│                                 │
├────────────┬────────────────────┤
│  Docker    │    Git Status      │
│  Stats     │    + Push/Pull     │
└────────────┴────────────────────┘
```

Setup:
1. Press `Ctrl+Shift+Alt+F` for fat layout
2. In top pane: `htop` or `bottom`
3. In bottom-left: `docker stats`
4. In bottom-right: `watch -n 1 'git status'`

---

## Keyboard Shortcuts Cheat Sheet

### Most Used (Learn These First)

| Action | Keybinding |
|--------|-----------|
| New tab | `Ctrl+T` |
| Close tab/window | `Ctrl+Shift+W` |
| Vertical split | `Alt+\` |
| Horizontal split | `Alt+-` |
| Navigate windows | `Alt+H/J/K/L` |
| Resize windows | `Alt+Shift+H/J/K/L` |
| Next layout | `Ctrl+Shift+F` |
| Reset window sizes | `Ctrl+Shift+E` |
| Reload config | `Ctrl+Alt+R` |
| Copy | `Ctrl+Shift+C` |
| Paste | `Ctrl+Shift+V` |

### Print This Reference Card

```
╔══════════════════════════════════════════════╗
║        KITTY QUICK REFERENCE CARD            ║
╠══════════════════════════════════════════════╣
║ TABS                                         ║
║ New tab.................... Ctrl+T           ║
║ Close tab.................. Ctrl+Shift+W     ║
║ Next/Prev tab.............. Ctrl+(Shift+)Tab ║
║ Go to tab N................ Alt+N (1-9)      ║
╠══════════════════════════════════════════════╣
║ WINDOWS                                      ║
║ Vertical split............. Alt+\            ║
║ Horizontal split........... Alt+-            ║
║ Navigate................... Alt+H/J/K/L      ║
║ Resize..................... Alt+Shift+H/J/K/L║
║ Close window............... Ctrl+Shift+Q     ║
╠══════════════════════════════════════════════╣
║ LAYOUTS                                      ║
║ Cycle layouts.............. Ctrl+Shift+F     ║
║ Fullscreen................. F11              ║
║ Reset sizes................ Ctrl+Shift+E     ║
║ Rotate..................... Ctrl+Alt+Space   ║
╠══════════════════════════════════════════════╣
║ CLIPBOARD                                    ║
║ Copy....................... Ctrl+Shift+C     ║
║ Paste...................... Ctrl+Shift+V     ║
╠══════════════════════════════════════════════╣
║ SYSTEM                                       ║
║ Reload config.............. Ctrl+Alt+R       ║
║ Scrollback (nvim).......... Ctrl+Shift+H     ║
║ URL hints.................. Ctrl+Shift+U     ║
║ Broadcast mode............. Ctrl+Shift+B     ║
╚══════════════════════════════════════════════╝
```

---

## Version History

- **v1.0** - Initial configuration with basic features
- **v2.0** - Added advanced window management and layouts
- **v3.0** - Integrated kitty-scrollback.nvim
- **v4.0** - Current version with full feature set

---

## Contributing

Found an issue or have a suggestion?

1. Test your changes thoroughly
2. Document new keybindings
3. Ensure no conflicts with existing bindings
4. Share your improvements!

---

## Resources

- [Kitty Documentation](https://sw.kovidgoyal.net/kitty/)
- [Catppuccin Theme](https://github.com/catppuccin/kitty)
- [Kitty-scrollback.nvim](https://github.com/mikesmithgh/kitty-scrollback.nvim)
- [Hack Nerd Font](https://www.nerdfonts.com/)
- [Kitty Remote Control](https://sw.kovidgoyal.net/kitty/remote-control/)

---

## License

This configuration is provided as-is. Feel free to modify and share!

---

## Credits

Created with ❤️ for productive terminal workflows.

Special thanks to:
- Kovid Goyal for Kitty
- The Catppuccin team for the beautiful theme
- The Nerd Fonts project
- The kitty-scrollback.nvim developers

---

**Happy Terminal Hacking! 🚀**
