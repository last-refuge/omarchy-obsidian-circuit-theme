# Validation

Validated on 2026-11-03 using Omarchy **4.5.0-rc3-1**.

## Theme package

- `colors.toml` and `shell.toml` parse as TOML. Required semantic colors are present and every supplied color is a six-digit hexadecimal value.
- The palette declares dark mode. The top bar and launcher card backgrounds have alpha 1.0.
- All four wallpapers decode successfully. They are byte-for-byte copies of the original generated PNGs; the sizes in [Artwork](ARTWORK.md) match their PNG headers.
- The repository contains no symlinks, machine-specific installation paths, private screenshots, or backup configuration files.
- Relative links in the documentation resolve to files in this repository.

## Omarchy staging

The actual `omarchy theme set obsidian-circuit` pipeline was exercised with `OMARCHY_THEME_HEADLESS=1` inside a Bubblewrap filesystem. Temporary config, state, and cache directories were mounted at the standard user paths; the rest of the host was read-only, network access was disabled, and the real desktop configuration was not changed. A repository-installed theme was used so Omarchy's installed-theme filtering was exercised as well as template generation.

The staged output includes generated Foot, Alacritty, Ghostty, Kitty, Hyprland, Neovim, VS Code, btop, and shell configurations. Generated TOML and JSON files parse, the checked generated files have no unresolved template tokens, and all four backgrounds are staged.

This is a staging/template check, not a claim that every supported application has been launched. The live desktop verifies the wallpaper, shell surface colors, opaque bar, and optional dock appearance on the tested Omarchy release.

## Optional dock

The patch base matches upstream Omarchy `v4.5.0-rc3`'s `DockWindow.qml`, Git blob `855f82c044e10d809db2e7d0ec35a44e0cc0b9db`.

The patch passes a dry run with `--fuzz=0`, applies exactly to the base, produces the same file as the verified live customization, and reverses back to the original file byte-for-byte. Qt's `qmlformat` parses the patched QML successfully. No packaged Omarchy source file is modified by the instructions.

## Preview

`preview.png` is a 1920 × 1080 capture from a temporary virtual display in a real running Omarchy/Hyprland session. The display contained only a terminal showing theme demonstration content and Neovim showing this repository's palette file. No personal windows or notifications are present. Neovim is focused to show the theme's orange active-window border. The screenshot includes the optional dock styling.

The gallery copy is 1200 × 675, WebP quality 80, stripped of metadata, and 59,944 bytes. The original-resolution screenshot is also stripped of metadata. The temporary preview windows and display were removed after capture.

Gallery instructions checked: https://github.com/omacom/omarchy-site#adding-your-theme
