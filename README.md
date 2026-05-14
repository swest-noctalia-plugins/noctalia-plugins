# noctalia-plugins
# SwestBinds

Personal [Noctalia](https://github.com/noctalia-dev/noctalia) plugin repository by **theswest**.
Keyboard shortcuts and Fish shell alias viewer for [Noctalia](https://github.com/noctalia-dev/noctalia) that automatically detects and displays keybindings for Hyprland or Niri compositors, plus your Fish shell aliases and abbreviations.

## Plugins
![Preview](preview.png)

| Plugin | Description | Version |
|--------|-------------|---------|
| [SwestBinds](./swbinds) | Keyboard shortcuts and Fish shell alias viewer for Hyprland and Niri | 1.0.0 |
## Features

<<<<<<<< HEAD:README.md
## License
========
## Installation
- **Automatic compositor detection** (Hyprland or Niri)
- **Recursive config parsing** - follows all `source` (Hyprland) and `include` (Niri) directives
- **Glob pattern support** - parses `~/.config/hypr/*.conf` style includes
- **Fish shell aliases and abbreviations** - parsed from your `config.fish`
- **Search** - filter keybinds and aliases instantly
- **Smart key formatting** - XF86 keys display as readable names (Vol Up, Bright Down, etc.)
- **Color-coded modifier keys** (Super, Ctrl, Shift, Alt)
- **Flexible column layout** (1-4 columns)
- **Auto-height** - adjusts to content automatically
- **IPC support** - toggle with a global hotkey

Copy the plugin folder into your Noctalia plugins directory:
## Installation

```bash
cp -r swbinds ~/.config/noctalia/plugins/
```

## Usage
>>>>>>>> 5350b17 (Add READMEs):swbinds/README.md

### Bar Widget
Add the plugin to your bar configuration in Noctalia settings. Click the keyboard icon to open the panel.

### Global Hotkey

**Hyprland** — add to your config:
```bash
bind = $mod, F1, exec, qs -c noctalia-shell ipc call plugin:swbinds toggle
```

**Niri** — add to your config:
```kdl
binds {
    Mod+F1 { spawn "qs" "-c" "noctalia-shell" "ipc" "call" "plugin" "togglePanel" "swbinds"; }
}
```

## Config Format

### Hyprland

```bash
# 1. APPLICATIONS
bind = $mainMod, T, exec, alacritty #"Terminal"
bind = $mainMod, B, exec, firefox #"Browser"

# 2. WINDOW MANAGEMENT
bind = $mainMod, Q, killactive, #"Close window"
```

- Categories: `# N. CATEGORY NAME`
- Descriptions: `#"description"` at end of line
- Source includes are followed automatically

### Niri

```kdl
binds {
    // #"Applications"
    Mod+T hotkey-overlay-title="Terminal" { spawn "alacritty"; }

    // #"Window Management"
    Mod+Q hotkey-overlay-title="Close window" { close-window; }
}
```

- Categories: `// #"Category Name"`
- Descriptions: `hotkey-overlay-title="description"`
- Include directives are followed automatically

### Fish Aliases

Aliases and abbreviations are read from `~/.config/fish/config.fish`:

```fish
alias gimme='paru -S'
alias nomore='paru -Rns'
abbr -a gs git status
```

> **Note:** Aliases saved with `alias --save` are stored in `~/.config/fish/functions/` and will not be picked up. Define them directly in `config.fish` instead.

## Settings

- **Window width** — 400–3000px
- **Height** — Auto or manual (300–2000px)
- **Columns** — 1–4 columns
- **Config paths** — Custom paths for Hyprland, Niri, and Fish configs
- **Show Fish aliases** — toggle alias display on or off
- **Mod key variable** — set your Super key variable (e.g. `$mainMod`)
- **Refresh** — force reload all keybindings and aliases

## Requirements

- Noctalia Shell 4.7.6+
- Hyprland or Niri compositor

## Credits

Based on [Keybind Cheatsheet](https://github.com/noctalia-dev/noctalia-plugins/tree/main/keybind-cheatsheet) by **blacku**, published in the official Noctalia plugins repo. This fork is maintained by **theswest**.

## License
