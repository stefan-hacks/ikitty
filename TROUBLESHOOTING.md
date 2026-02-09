# Kitty Terminal - Troubleshooting & FAQ

## 🔧 Common Issues & Solutions

### Issue 1: Keybindings Not Working

#### Symptom
Pressing keyboard shortcuts does nothing or triggers wrong actions.

#### Possible Causes & Solutions

**A. System-level key capture**
```bash
# Check if your OS is capturing the keys
# macOS: System Preferences → Keyboard → Shortcuts
# Linux: Settings → Keyboard → Custom Shortcuts
# Windows: Check global hotkeys
```

**B. Terminal application capturing keys**
```bash
# If running tmux/screen inside Kitty
# They may intercept certain key combinations

# Solution: Use different keys or remap inside tmux
# In ~/.tmux.conf:
unbind C-b
set -g prefix C-a
```

**C. Conflicting Kitty keybindings**
```bash
# Debug which keys are mapped
kitty @ debug-config | grep "map ctrl+shift+f"

# Check for conflicts
kitty @ debug-config | grep "next_layout"
```

**D. Shell capturing keys (Readline/ZSH)**
```bash
# Keys like Ctrl+W might be captured by shell
# Check your ~/.zshrc or ~/.bashrc

# Disable shell binding if needed:
# In ~/.zshrc:
bindkey -r '^W'  # Removes Ctrl+W binding
```

**Solution Steps:**
1. Test in fresh Kitty window: `kitty --override 'map f1 debug_config'`
2. Check system shortcuts
3. Temporarily disable shell configurations
4. Check Kitty config for typos

---

### Issue 2: Layouts Not Changing

#### Symptom
Pressing `Ctrl+Shift+F` or direct layout keys doesn't change layout.

#### Solution

**A. Only one layout enabled**
```bash
# Edit kitty.conf
# WRONG:
enabled_layouts splits

# CORRECT:
enabled_layouts splits,stack,tall,fat,grid,horizontal,vertical
```

**B. Reload config after changes**
```
Ctrl+Alt+R
# Or restart Kitty
```

**C. Currently in wrong mode**
```bash
# Some layouts require minimum windows
# Grid layout needs at least 2 windows
# Stack layout needs at least 2 windows

# Create test windows:
Ctrl+Shift+Enter  # Create new window
Ctrl+Shift+Enter  # Create another
# Now try layout switching
```

---

### Issue 3: Fonts Look Wrong/Missing Icons

#### Symptom
Strange characters, missing symbols, or broken powerline.

#### Solution

**A. Install Nerd Font**
```bash
# macOS
brew tap homebrew/cask-fonts
brew install font-hack-nerd-font

# Ubuntu/Debian
sudo apt install fonts-hack-ttf
# Then download Nerd Font variant manually

# Arch
sudo pacman -S ttf-hack

# Manually install:
# Download from https://www.nerdfonts.com/
# Install .ttf files to:
# macOS: ~/Library/Fonts/
# Linux: ~/.local/share/fonts/
# Windows: C:\Windows\Fonts\
```

**B. Update font cache (Linux)**
```bash
fc-cache -fv
```

**C. Verify font in Kitty**
```bash
kitty + list-fonts | grep Hack

# Should show:
# Hack Nerd Font
# Hack Nerd Font Mono
# etc.
```

**D. Check font configuration**
```conf
# In kitty.conf, ensure exact name:
font_family      Hack Nerd Font Mono
# NOT just "Hack" or "Hack Nerd"
```

**E. Test with different font temporarily**
```bash
kitty --override 'font_family=monospace'
# If this works, font name is wrong
```

---

### Issue 4: Theme/Colors Not Loading

#### Symptom
Terminal looks plain or colors are wrong.

#### Solution

**A. Theme file missing**
```bash
# Check if file exists
ls ~/.config/kitty/current-theme.conf

# If missing, download Catppuccin Mocha:
cd ~/.config/kitty
curl -O https://raw.githubusercontent.com/catppuccin/kitty/main/themes/mocha.conf
mv mocha.conf current-theme.conf
```

**B. Include path wrong**
```conf
# In kitty.conf, check:
include current-theme.conf  # Relative path, OR
include ~/.config/kitty/current-theme.conf  # Absolute path
```

**C. Theme file has errors**
```bash
# Test loading manually
kitty @ set-colors --all ~/.config/kitty/current-theme.conf
```

**D. Use built-in theme temporarily**
```conf
# Comment out custom theme:
# include current-theme.conf

# Add basic colors:
background #1e1e2e
foreground #cdd6f4
cursor #f5e0dc
```

---

### Issue 5: Transparency/Blur Not Working

#### Symptom
Background stays opaque despite opacity settings.

#### Solution

**A. Compositor required (Linux)**
```bash
# X11 requires compositor like picom or compton
sudo apt install picom

# Start picom
picom --config ~/.config/picom/picom.conf &

# Or use in ~/.xinitrc:
picom -b
```

**B. Wayland support**
```bash
# Most Wayland compositors support transparency
# Check if using Wayland:
echo $XDG_SESSION_TYPE
# Should output: wayland
```

**C. macOS - should work natively**
```bash
# If not working, check:
# System Preferences → Accessibility → Display
# Ensure "Reduce transparency" is OFF
```

**D. Background blur settings**
```conf
# Requires compositor with blur support
# Try without blur first:
background_blur 0
background_opacity 0.95

# If that works, increase blur gradually:
background_blur 1
background_blur 5
background_blur 10
```

**E. GPU/Driver issues**
```bash
# Check GPU acceleration:
kitty @ debug-config | grep -i gl

# Try software rendering:
kitty --override 'disable_gl=yes'
```

---

### Issue 6: Kitty-Scrollback.nvim Not Working

#### Symptom
`Ctrl+Shift+H` does nothing or shows error.

#### Solution

**A. Verify Neovim installed**
```bash
nvim --version
# Should be 0.9.0 or higher
```

**B. Check plugin installation**
```bash
# Path should exist:
ls ~/.local/share/nvim/lazy/kitty-scrollback.nvim/

# If missing, install with lazy.nvim:
# In Neovim, run:
:Lazy install kitty-scrollback.nvim
```

**C. Verify Python in plugin**
```bash
ls ~/.local/share/nvim/lazy/kitty-scrollback.nvim/python/
# Should contain: kitty_scrollback_nvim.py
```

**D. Check path in config**
```conf
# Ensure path matches your installation:
action_alias kitty_scrollback_nvim kitten /home/YOUR_USERNAME/.local/share/nvim/lazy/kitty-scrollback.nvim/python/kitty_scrollback_nvim.py
```

**E. Test manually**
```bash
# From terminal:
kitty @ kitten /path/to/kitty_scrollback_nvim.py

# Should open scrollback in nvim
```

**F. Check shell integration**
```conf
# Ensure this is set:
shell_integration enabled
```

---

### Issue 7: Window Borders Not Showing

#### Symptom
Can't see which window is active.

#### Solution

**A. Border width too small**
```conf
# Increase border width:
window_border_width 2pt
# Or even:
window_border_width 3pt
```

**B. Colors too similar to background**
```conf
# Use high contrast colors:
active_border_color #00ff00    # Bright green
inactive_border_color #ff0000  # Red for testing

# Or try:
active_border_color #ffffff    # White
inactive_border_color #444444  # Dark gray
```

**C. Minimal borders disabled**
```conf
# Check this setting:
draw_minimal_borders yes

# Try:
draw_minimal_borders no
```

**D. Single window has no border**
```conf
# This is normal behavior
# Add border to single window:
single_window_margin_width 5
```

---

### Issue 8: Mouse Actions Not Working

#### Symptom
Clicking URLs or selecting text doesn't work.

#### Solution

**A. Application capturing mouse**
```bash
# Applications like Vim/Tmux may capture mouse
# In Vim, disable mouse:
:set mouse=

# In tmux:
set -g mouse off
```

**B. Check mouse mappings**
```conf
# Verify these are set:
mouse_map left click ungrabbed mouse_click_url_or_select
mouse_map middle press ungrabbed paste_from_selection
```

**C. URL detection disabled**
```conf
# Ensure:
detect_urls yes
allow_hyperlinks yes
```

**D. Terminal not in focus**
```bash
# Click window to focus first
# Then try mouse actions
```

---

### Issue 9: Remote Control Not Working

#### Symptom
`kitty @` commands fail or show "connection refused".

#### Solution

**A. Remote control not enabled**
```conf
# Add to kitty.conf:
allow_remote_control yes
listen_on unix:/tmp/kitty
```

**B. Socket file missing**
```bash
# Check if socket exists:
ls -la /tmp/kitty

# If missing, restart Kitty
```

**C. Wrong socket path**
```bash
# Find actual socket:
ls /tmp/mykitty*

# Use correct socket:
kitty @ --to unix:/tmp/mykitty-1234 ls
```

**D. Permissions issue**
```bash
# Check socket permissions:
ls -la /tmp/kitty

# Fix if needed:
chmod 600 /tmp/kitty
```

**E. Multiple Kitty instances**
```bash
# List all sockets:
ls /tmp/mykitty*

# Connect to specific instance:
kitty @ --to unix:/tmp/mykitty-12345 ls
```

---

### Issue 10: Performance Problems/Lag

#### Symptom
Slow rendering, input lag, or stuttering.

#### Solution

**A. Reduce visual effects**
```conf
# Disable transparency:
background_opacity 1.0
background_blur 0

# Disable cursor trail:
cursor_trail 0

# Reduce dim opacity:
inactive_text_alpha 1.0
```

**B. Adjust timing**
```conf
# Increase delays:
repaint_delay 20
input_delay 10

# Disable sync:
sync_to_monitor no
```

**C. GPU acceleration issues**
```bash
# Check GPU usage:
kitty @ debug-config | grep -i gpu

# Try software rendering:
kitty --override 'disable_gl=yes'

# Or force GPU:
kitty --override 'disable_gl=no'
```

**D. Font rendering**
```conf
# Disable ligatures:
disable_ligatures always

# Use simpler font:
font_family monospace
```

**E. Reduce window count**
```bash
# Too many windows can slow things down
# Close unused windows: Ctrl+Shift+Q
# Or switch to Stack layout: Ctrl+Shift+Alt+S
```

**F. Check system resources**
```bash
# Monitor Kitty process:
top -p $(pgrep kitty)

# Check if other apps consuming resources
htop
```

---

## ❓ Frequently Asked Questions

### Q1: Can I use Kitty on Windows?

**A:** Not natively, but you can use WSL2:

```bash
# In WSL2:
sudo apt install kitty

# Then run:
kitty

# For GUI, ensure WSLg is enabled (Windows 11)
# Or use X server (Windows 10): VcXsrv, Xming
```

For native Windows, alternatives:
- Windows Terminal
- Alacritty
- WezTerm

---

### Q2: How do I make Kitty my default terminal?

**macOS:**
```bash
# System Preferences → General → Default terminal
# Select Kitty

# Or via command:
defaults write com.apple.LaunchServices/com.apple.launchservices.secure LSHandlers -array-add '{LSHandlerContentType=public.unix-executable;LSHandlerRoleAll=net.kovidgoyal.kitty;}'
```

**Linux (Ubuntu/Debian):**
```bash
sudo update-alternatives --config x-terminal-emulator
# Select kitty

# Or set as default for GNOME:
gsettings set org.gnome.desktop.default-applications.terminal exec kitty
```

**Linux (Arch):**
```bash
# Edit ~/.bashrc or ~/.zshrc:
export TERMINAL=kitty
```

---

### Q3: Can I use Kitty with Tmux?

**A:** Yes, but there's overlap in functionality.

```bash
# Kitty has built-in:
# - Window management (tabs, panes)
# - Session management (via remote control)
# - Scrollback
# - Copy/paste

# Tmux adds:
# - Detachable sessions
# - Remote session access
# - Even more flexibility

# Use together:
kitty -e tmux

# Best practice:
# Use Kitty for local window management
# Use tmux only for:
#   - Remote sessions
#   - Detachable long-running tasks
#   - Pair programming
```

---

### Q4: How do I save and restore window layouts?

**A:** Currently no built-in session management, but you can:

**Option 1: Use remote control to save state**
```bash
#!/bin/bash
# save_layout.sh
kitty @ ls > ~/kitty-session.json
```

**Option 2: Startup script**
```bash
#!/bin/bash
# startup_layout.sh
kitty @ launch --type=tab --cwd=~/projects/frontend
kitty @ launch --type=tab --cwd=~/projects/backend
kitty @ launch --type=window --cwd=~/projects/frontend
kitty @ set-tab-title --match index:1 "Frontend"
kitty @ set-tab-title --match index:2 "Backend"
```

**Option 3: Use tmux inside Kitty for session management**

---

### Q5: Can I use custom fonts for specific characters?

**A:** Yes, with symbol_map:

```conf
# Main font:
font_family      Hack Nerd Font

# Use specific font for emojis:
symbol_map U+1F600-U+1F64F Apple Color Emoji

# Use specific font for box drawing:
symbol_map U+2500-U+257F DejaVu Sans Mono

# Japanese characters:
symbol_map U+3000-U+30FF,U+4E00-U+9FAF Noto Sans CJK JP
```

---

### Q6: How do I create custom keybindings?

**A:** Add to kitty.conf:

```conf
# Simple command:
map ctrl+shift+z send_text all echo "Hello World"\n

# Multiple commands:
map f1 combine : launch --type=overlay htop : send_text all

# Custom action alias:
action_alias my_split launch --location=vsplit --cwd=current
map ctrl+shift+s my_split

# Chain multiple actions:
map f2 combine : goto_layout tall : launch --location=vsplit : resize_window wider 3

# Conditional based on layout:
map f3 toggle_layout stack
```

---

### Q7: Can I have different configs for different projects?

**A:** Yes, with kitty instance naming:

```bash
# Create project-specific config:
mkdir -p ~/.config/kitty/projects/myapp

# Create kitty.conf in that directory:
echo "include ~/.config/kitty/kitty.conf" > ~/.config/kitty/projects/myapp/kitty.conf
echo "background #ff0000" >> ~/.config/kitty/projects/myapp/kitty.conf

# Launch with specific config:
kitty --config ~/.config/kitty/projects/myapp/kitty.conf
```

Or use environment-based config:

```bash
# In kitty.conf:
include ${KITTY_PROFILE}.conf

# Launch:
KITTY_PROFILE=work kitty
# This loads work.conf
```

---

### Q8: How do I copy to clipboard from within terminal apps?

**A:** Multiple methods:

**Method 1: OSC 52 (works over SSH)**
```bash
# Most modern apps support this
# Neovim, tmux, etc.

# In Neovim:
set clipboard=unnamedplus

# In tmux:
set -g set-clipboard on
```

**Method 2: Kitty's selection**
```bash
# Select text with mouse
# Then Ctrl+Shift+C
```

**Method 3: Kitty hints**
```bash
# Ctrl+Shift+U for URL hints
# Shows letters to copy items
```

**Method 4: Remote control**
```bash
# From script:
echo "text" | kitty @ send-text --match all
```

---

### Q9: Can I use Kitty for serial port communication?

**A:** Yes:

```bash
# Connect to serial port:
kitty -e 'screen /dev/ttyUSB0 115200'

# Or use minicom:
kitty -e 'minicom -D /dev/ttyUSB0'

# For better experience:
# Disable flow control in kitty.conf:
# (Not directly supported, use tool settings)
```

---

### Q10: How do I make Kitty start with specific tabs/windows?

**A:** Use startup session:

**Create session file:**
```bash
# ~/.config/kitty/startup.conf
# Tab 1: Development
launch --type=tab --cwd=~/projects/myapp --tab-title="Dev"
launch --location=vsplit

# Tab 2: Monitoring  
launch --type=tab --tab-title="Monitor"
launch htop

# Tab 3: Database
launch --type=tab --cwd=~/database --tab-title="DB"
```

**Launch with session:**
```bash
kitty --session ~/.config/kitty/startup.conf
```

**Or in kitty.conf:**
```conf
startup_session ~/.config/kitty/startup.conf
```

---

### Q11: Can I change opacity dynamically?

**A:** Yes, with remote control:

```bash
# Decrease opacity:
kitty @ set-background-opacity 0.8

# Increase opacity:
kitty @ set-background-opacity 1.0

# Create keybinding:
# In kitty.conf:
map f11 set_background_opacity 1.0
map f12 set_background_opacity 0.9
```

**Create toggle script:**
```bash
#!/bin/bash
# toggle_opacity.sh
current=$(kitty @ get-colors | grep background_opacity | awk '{print $2}')
if [ "$current" = "1.0" ]; then
    kitty @ set-background-opacity 0.9
else
    kitty @ set-background-opacity 1.0
fi
```

---

### Q12: How do I debug what Kitty is doing?

**A:** Several methods:

```bash
# Method 1: Debug config
kitty @ debug-config

# Method 2: Verbose mode
kitty -v

# Method 3: Check logs
# macOS:
tail -f ~/Library/Logs/kitty/kitty.log

# Linux:
tail -f ~/.local/share/kitty/kitty.log

# Method 4: Test specific setting
kitty --override 'font_size=20' -e echo "test"

# Method 5: Print all settings
kitty @ get-colors
kitty @ ls
```

---

## 🚨 Emergency Fixes

### Kitty Won't Start

```bash
# Check if running:
ps aux | grep kitty

# Kill all instances:
killall kitty

# Start with default config:
kitty --config NONE

# Check for config errors:
kitty --debug-config

# Reset config:
mv ~/.config/kitty/kitty.conf ~/.config/kitty/kitty.conf.backup
kitty  # Will use defaults
```

### Config File Corrupted

```bash
# Validate syntax:
# Kitty doesn't have validation, but check for:
# - Unmatched quotes
# - Invalid option names
# - Wrong paths

# Use defaults:
kitty --config NONE

# Rebuild incrementally:
# Start with minimal config
# Add sections one at a time
# Reload after each: Ctrl+Alt+R
```

### Terminal Completely Broken

```bash
# Reset everything:
rm -rf ~/.config/kitty/
rm -rf ~/.local/share/kitty/

# Reinstall:
# macOS:
brew reinstall kitty

# Linux:
sudo apt reinstall kitty

# Start fresh
kitty
```

---

## 📞 Getting More Help

### Official Resources
- Documentation: https://sw.kovidgoyal.net/kitty/
- GitHub Issues: https://github.com/kovidgoyal/kitty/issues
- GitHub Discussions: https://github.com/kovidgoyal/kitty/discussions

### Community
- Reddit: r/KittyTerminal
- Discord: Check GitHub for invite link

### Reporting Bugs
```bash
# Gather information:
kitty --version
kitty @ debug-config > debug.txt
# Include this in bug report
```

---

**Still stuck? Check the main README.md for more detailed feature explanations!**
