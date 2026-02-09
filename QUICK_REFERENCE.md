# Kitty Terminal - Quick Reference Card

## 🔥 Essential Keybindings (Master These First)

```
┏━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┓
┃  TABS                                    ┃
┣━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┫
┃  New tab...................... Ctrl+T    ┃
┃  Close tab.................... Ctrl+Shift+W
┃  Next tab..................... Ctrl+Tab  ┃
┃  Previous tab................. Ctrl+Shift+Tab
┃  Go to tab 1-9................ Alt+1 to Alt+9
┃  Go to tab 10................. Alt+0    ┃
┃  Move tab left................ Ctrl+Shift+Page Up
┃  Move tab right............... Ctrl+Shift+Page Down
┗━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┛

┏━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┓
┃  WINDOWS / PANES                         ┃
┣━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┫
┃  Vertical split............... Alt+\    ┃
┃  Horizontal split............. Alt+-    ┃
┃  Close window................. Ctrl+Shift+Q
┃  Navigate left................ Alt+H    ┃
┃  Navigate down................ Alt+J    ┃
┃  Navigate up.................. Alt+K    ┃
┃  Navigate right............... Alt+L    ┃
┃  Resize taller................ Alt+Shift+K
┃  Resize shorter............... Alt+Shift+J
┃  Resize wider................. Alt+Shift+H
┃  Resize narrower.............. Alt+Shift+L
┃  Reset all sizes.............. Ctrl+Shift+E
┗━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┛

┏━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┓
┃  LAYOUTS                                 ┃
┣━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┫
┃  Cycle next layout............ Ctrl+Shift+F
┃  Cycle previous layout........ Ctrl+Shift+D
┃  Toggle fullscreen............ F11      ┃
┃  Rotate layout................ Ctrl+Alt+Space
┃  Toggle stack layout.......... Ctrl+Shift+Space
┃                                          ┃
┃  Go to Tall layout............ Ctrl+Shift+Alt+T
┃  Go to Stack layout........... Ctrl+Shift+Alt+S
┃  Go to Fat layout............. Ctrl+Shift+Alt+F
┃  Go to Grid layout............ Ctrl+Shift+Alt+G
┃  Go to Horizontal layout...... Ctrl+Shift+Alt+H
┃  Go to Vertical layout........ Ctrl+Shift+Alt+V
┗━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┛

┏━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┓
┃  CLIPBOARD                               ┃
┣━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┫
┃  Copy......................... Ctrl+Shift+C
┃  Paste........................ Ctrl+Shift+V
┃  Paste........................ Shift+Insert
┗━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┛

┏━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┓
┃  SCROLLING                               ┃
┣━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┫
┃  Scroll to top................ Ctrl+Shift+Home
┃  Scroll to bottom............. Ctrl+Shift+End
┃  Previous prompt.............. Ctrl+Alt+Home
┃  Next prompt.................. Ctrl+Alt+End
┃  Clear screen................. Ctrl+Shift+Delete
┗━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┛

┏━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┓
┃  SPECIAL FEATURES                        ┃
┣━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┫
┃  Nvim scrollback.............. Ctrl+Shift+H
┃  Last command output.......... Ctrl+Shift+G
┃  URL hints.................... Ctrl+Shift+U
┃  Broadcast mode............... Ctrl+Shift+B
┃  Reload config................ Ctrl+Alt+R
┃  Edit config.................. Ctrl+Shift+Alt+,
┃  Debug config................. Ctrl+Shift+Alt+D
┗━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┛

┏━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┓
┃  FONTS                                   ┃
┣━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┫
┃  Increase font size........... Ctrl+=   ┃
┃  Decrease font size........... Ctrl+-   ┃
┃  Reset font size.............. Cmd+0    ┃
┗━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┛
```

## 📐 Layout Types Explained

```
SPLITS Layout (Manual Control)
┌────────┬──────────┐
│        │          │
│        │          │  ← You control all splits
│        │          │    with Alt+\ and Alt+-
├────────┴──────────┤
│                   │
└───────────────────┘

TALL Layout
┌─────────────┬─────┐
│             │  2  │  ← Main window on left
│      1      ├─────┤    Stack on right
│             │  3  │
└─────────────┴─────┘

FAT Layout
┌───────────────────┐
│         1         │  ← Main window on top
├─────────┬─────────┤    Stack on bottom
│    2    │    3    │
└─────────┴─────────┘

STACK Layout
┌───────────────────┐
│                   │  ← Only one window visible
│         1         │    Others hidden
│                   │    (Use Ctrl+Shift+= to switch)
└───────────────────┘

GRID Layout
┌─────────┬─────────┐
│    1    │    2    │  ← Automatic grid
├─────────┼─────────┤    arrangement
│    3    │    4    │
└─────────┴─────────┘

HORIZONTAL Layout
┌───────────────────┐
│         1         │  ← Windows stacked
├───────────────────┤    horizontally
│         2         │
├───────────────────┤
│         3         │
└───────────────────┘

VERTICAL Layout
┌─────┬─────┬─────┐
│  1  │  2  │  3  │  ← Windows stacked
│     │     │     │    vertically
└─────┴─────┴─────┘
```

## 🎯 Common Workflows

### Development Setup
```
1. Start Kitty
2. Ctrl+T (new tab for frontend)
3. Ctrl+T (new tab for backend)
4. Alt+\ (split vertically for editor|terminal)
5. Ctrl+Shift+Alt+T (switch to tall layout)
6. Alt+H (focus left pane)
7. Type: nvim (start coding)
```

### Multi-Server Management
```
1. Create 4 windows: Ctrl+Shift+Enter (x3)
2. Ctrl+Shift+Alt+G (grid layout)
3. SSH into each server
4. Ctrl+Shift+B (enable broadcast)
5. Type commands (sent to all servers)
6. Ctrl+Shift+B (disable broadcast)
```

### Research & Notes
```
1. Alt+\ (vertical split)
2. Left pane: nvim notes.md
3. Right pane: browser/research
4. Ctrl+Shift+H (open scrollback in nvim)
5. Copy relevant info to notes
```

## 💡 Pro Tips

### Tip #1: Focus by Number
Instead of navigating with Alt+H/J/K/L:
- `Ctrl+1` jumps to window 1
- `Ctrl+2` jumps to window 2
- etc.

### Tip #2: Interactive Resize
`Ctrl+Shift+R` enters resize mode:
- Use arrow keys to resize
- Press Esc when done
- More precise than Alt+Shift

### Tip #3: Layout Rotation
In any layout, `Ctrl+Alt+Space` rotates:
```
Before:           After:
┌────┬────┐      ┌────┬────┐
│ 1  │ 2  │  →   │ 4  │ 1  │
├────┼────┤      ├────┼────┤
│ 3  │ 4  │      │ 3  │ 2  │
└────┴────┘      └────┴────┘
```

### Tip #4: Quick Detach
`Ctrl+Shift+X` moves current window to new tab
- Useful for isolating a task
- Better than copy/paste

### Tip #5: Broadcast for Consistency
Use `Ctrl+Shift+B` to:
- Update multiple servers
- Run same tests in parallel
- Synchronized configuration

## 🔍 Troubleshooting Quick Fixes

### Keybinding Not Working?
```bash
# Check what's mapped to that key
kitty @ debug-config | grep "your_key"
```

### Reset to Default Layout?
```
Ctrl+Shift+E  # Resets window sizes
Ctrl+Shift+F  # Cycle to preferred layout
```

### Lost Window in Stack?
```
Ctrl+Shift+=  # Focus visible window
Ctrl+Shift+-  # Cycle through stack
```

### Config Changes Not Applied?
```
Ctrl+Alt+R  # Reload configuration
```

## 📋 Window Focus Methods Compared

| Method | Keys | Use Case |
|--------|------|----------|
| Vim nav | `Alt+H/J/K/L` | Small number of windows |
| Arrow nav | `Ctrl+Shift+Arrows` | Alternative preference |
| Number | `Ctrl+1-9` | Jump directly to window |
| Swap | `Ctrl+Shift+Alt+Space` | Reorganize layout |

## 🎨 Visual Customization Variables

Located in kitty.conf:

```bash
background_opacity 0.95      # Transparency (0.0-1.0)
inactive_text_alpha 0.7      # Dim inactive windows
background_blur 1            # Blur amount
window_margin_width 5        # Outer spacing
window_padding_width 2       # Inner spacing
font_size 13.0              # Base font size

# Border colors
active_border_color #00ff00
inactive_border_color #282828
```

Quick toggle transparency:
```conf
# Add to kitty.conf
map f12 set_background_opacity 1.0
map f11 set_background_opacity 0.95
```

## 🚀 Advanced Remote Control Examples

### Open URL in Split
```bash
kitty @ launch --type=window --location=vsplit \
  w3m https://example.com
```

### Set Tab Colors
```bash
kitty @ set-tab-color --match title:Frontend \
  --foreground red
```

### Auto-layout by Time
```bash
# In cron or startup script
hour=$(date +%H)
if [ $hour -lt 12 ]; then
  kitty @ goto-layout tall
else
  kitty @ goto-layout stack
fi
```

### Monitor and Auto-restart
```bash
#!/bin/bash
while true; do
  kitty @ launch --type=overlay \
    --hold htop
  sleep 60
done
```

## 📖 Learn More

- Full README.md for complete documentation
- kitty.conf for all configuration options
- https://sw.kovidgoyal.net/kitty/ - Official docs

---

**Print this card and keep it handy!** 🖨️

*Last updated: 2024*
