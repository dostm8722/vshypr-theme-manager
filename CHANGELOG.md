# Changelog

All notable changes to vsHypr Theme Manager are documented here.

---

## [1.0.0] — 2026-03-28

### First release

**Theme engine (`vshypr-theme-manager.py`)**
- Apply a unified color scheme to 16 applications in a single command
- Non-destructive CSS injection using `/* theme-changer: begin/end */` marker blocks — manual config edits are always preserved
- Two-level backup system: `original/` snapshot (written once, never overwritten) + timestamped snapshot before every apply
- Dynamic theme generation from any wallpaper via `matugen` (`dynamic-dark` / `dynamic-light`)
- Wallpaper apply via `awww` with smooth transitions
- Auto-restart Nautilus and Dolphin after apply to pick up new colors immediately

**Supported applications**
- Kitty — full `theme.conf` generation
- Waybar — CSS variables, module styles, and keyframe animations
- SwayNC — CSS custom properties with `:root {}` and RGB component format
- Hyprland — generates `theme.conf`, verifies `@source` directive
- Hyprlock — `key = value` injection
- Hyprswitch — CSS injection
- Rofi — 5 `.rasi` files themed simultaneously
- EWW — template rendering for dark and light variants
- Wlogout — template + SVG icon colorization
- vsFetch — direct `config.json` key update
- GTK4 / libadwaita — full `@define-color` override set
- GTK3 — `@define-color` + `gtk-theme-name=Adwaita` for variable resolution
- Qt5ct — 21 QPalette roles
- Qt6ct — KDE color scheme format
- kdeglobals — `[Colors:*]` sections replacement
- Kvantum — custom theme with patched SVG and `[GeneralColors]` block

**Themes included (44)**
- Dark: Catppuccin, Dracula, Tokyo Night, Nord Dark, Nord Darker, Everforest, Kanagawa, Graphite, GitHub Dark Colorblind, Sweet Mars, Very Darkest, Yorha, Midoriya, Arc Aurora Dark
- Arch variants: Arch, Arch Dark, Arch Lightly, Arch Magenta, Arch Manjaro, Arch Manjaro Dark, Arch Manjaroish, Arch Manjaro Light, Arch Purple, Arch Smooth, Arch Vampire, Arch Yellow
- Original: Abyssal Bloom, Aurora Fields, Austral Azure, Austral Marine, Azure Dunes, Blueprint Frost, Crimson Dusk, Ember Grove, Flick Aurora, Moss Forest, Neon Canopy, Skyfoam Glow, Steel Ember, Verdant Harvest
- Light: Catppuccin Latte, Nord Light
- Dynamic: dynamic-dark, dynamic-light (generated via matugen)

**GUI (`vshypr-theme-manager`)**
- GTK3 Python app with 7 tabs: Setup, Config, Set Theme, Wallpaper, Assets, vsHub, About
- **Setup tab** — lists all supported apps and dependencies with live install status; installs selected tools via `yay` or `paru`
- **Config tab** — set wallpapers directory, theme-changer data directory; patch `WALLPAPER_DIR` in `rofi-picker.sh`
- **Set Theme tab** — visual grid with wallpaper thumbnails, color palette swatches, per-theme Apply and `+ WP` buttons; highlights active theme
- **Wallpaper tab** — file picker with 16:9 preview; applies wallpaper independently of the active theme
- **Assets tab** — installs bundled Rofi `.rasi` configs, Wlogout layout + SVG icons, and Hyprland `wallpaper.sh` to correct `~/.config/` locations; per-item and bulk install
- **vsHub tab** — discovery and install panel for the vs tool ecosystem
- **About tab** — version info and links

**Rofi picker (`rofi-picker.sh`)**
- Visual theme picker with wallpaper thumbnail and inline color palette per theme
- `Enter` — apply theme only
- `Alt+Enter` — apply theme with wallpaper (static: bundled wallpaper; dynamic: opens wallpaper grid)
- Sections: dark themes / light themes / dynamic

**Bundled assets**
- Rofi: `config.rasi`, `spotlight.rasi`, `launchpad.rasi`, `config-keybinds.rasi`, `wallpaper-grid.rasi`, `theme-picker.rasi`, `wallpaper-picker.rasi`
- Wlogout: layout + SVG icons (lock, logout, suspend, hibernate, reboot, shutdown)
- Hyprland: `wallpaper.sh` startup script for `awww-daemon`

**Distribution**
- Designed for AUR distribution
- All user data lives in `~/.config/vshypr-theme-manager/`
- `.desktop` entry and app icon included
