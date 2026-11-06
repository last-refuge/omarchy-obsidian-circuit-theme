# Validation

Validated on 2026-11-03 using Omarchy **4.5.0-rc3-1**.

## Theme package

- `colors.toml` and `shell.toml` parse as TOML. Required semantic colors are present and every supplied color is a six-digit hexadecimal value.
- The palette declares dark mode. The top bar and launcher card backgrounds have alpha 1.0.
- All four wallpapers are WebP (quality 82, metadata stripped), decode successfully, and match the sizes in [Artwork](ARTWORK.md).
- The repository contains no symlinks, machine-specific installation paths, private screenshots, or backup configuration files.
- Relative links in the documentation resolve to files in this repository.

## Omarchy staging

The actual `omarchy theme set obsidian-circuit` pipeline was exercised with `OMARCHY_THEME_HEADLESS=1` inside a Bubblewrap filesystem. Temporary config, state, and cache directories were mounted at the standard user paths; the rest of the host was read-only, network access was disabled, and the real desktop configuration was not changed. A repository-installed theme was used so Omarchy's installed-theme filtering was exercised as well as template generation.

The staged output includes generated Foot, Alacritty, Ghostty, Kitty, Hyprland, Neovim, VS Code, btop, and shell configurations. Generated TOML and JSON files parse, the checked generated files have no unresolved template tokens, and all four backgrounds are staged. That run used the original PNG versions of the wallpapers and has not been repeated since they were re-encoded as WebP, a format Omarchy's wallpaper tools accept.

This is a staging/template check, not a claim that every supported application has been launched. The live desktop verifies the wallpaper, shell surface colors, and opaque bar on the tested Omarchy release.

## Preview

`preview.png` is a metadata-stripped 1920 × 1080 capture from a temporary virtual output in a separate Hyprland 0.56.2 session running the packaged Omarchy 4.5.0-3 shell. The session used a Bubblewrap-isolated home, runtime directory, and D-Bus. The packaged `omarchy.bar` and `omarchy.dock` plugins were selected; no personal dock clone or dock patch was loaded. The user's live shell configuration, dock clone, workspace layouts, theme files, and background link were unchanged, verified against a recorded baseline.

The display contained only a Foot terminal showing public theme demonstration content and Neovim showing the theme's `colors.toml`. It uses `backgrounds/1-obsidian-circuit.webp`, with Neovim focused to show the orange active-window border. The stock dock has its normal app-grid icon and running-app indicator, without the removed graphite plate. No mouse pointer, notifications, personal windows, or private information are present. The image was visually inspected after capture. The temporary compositor, virtual output, shell, and demonstration processes were stopped afterwards.

The gallery copy is 1200 × 675, WebP quality 80, stripped of metadata, and 50,646 bytes. It is copied byte-for-byte to the gallery PR's `assets/themes/obsidian-circuit.webp`.

Gallery instructions checked: https://github.com/omacom/omarchy-site#adding-your-theme

## Registry submission validation

The unmodified official `scripts/submit.ts` from `omacom/omarchy-theme-registry` commit `d0d1a9423ced911f173288b56193c4851109f9f6` validated the published theme at commit `e07a091e58d0ba24b18f253c31729e38c8091a93` with **zero errors and zero warnings**. It generated the entry for install name `obsidian-circuit`. The generated JSON also passes the registry's Prettier check.

The validator confirms a marketplace install includes the palette, all four wallpapers, root preview, `shell.toml`, README, and license. Organization ownership could not be verified through public membership; the submission report discloses this for maintainer review. The entry and full report are in [registry PR #202](https://github.com/omacom/omarchy-theme-registry/pull/202).

## Website gallery validation

[Gallery PR #683](https://github.com/omacom/omarchy-site/pull/683) adds the screenshot and alphabetical source entry. The site imports Obsidian Circuit exactly once between Nujabes and Oligarchy. The built page contains a clickable card linking to this repository, and its copied image matches the verified WebP byte-for-byte.

Local checks passed: `npm ci`, `npm run port`, `npm run lint`, `npm run typecheck`, `npm test`, `bin/build-news`, `npm run build`, and `npm run parity`. Tests ran with Node 24.22.2 and Python 3.13.18: 66 JavaScript/TypeScript tests and 50 Python tests passed. Parity verified all 8,900 addresses respond and all 2,525 passthrough files are byte-identical. These are local results; upstream review and CI are separate.
