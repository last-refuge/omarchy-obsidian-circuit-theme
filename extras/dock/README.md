# Optional Obsidian Circuit dock

This optional patch adds a borderless graphite backing plate, orange hover accents, an orange app-grid glyph, and orange running-app markers to a user-owned clone of Omarchy's dock. It does not change your pinned applications, dock position, or auto-hide preference.

**Target:** the dock shipped with Omarchy **4.5.0-rc3**. The patch is kept small and uses the active theme's colors. Its source and license are credited in [Attribution](../../docs/ATTRIBUTION.md).

## Apply

Install and select the theme first. Then keep a separate checkout of this repository, because a normal theme installation need not retain optional extras:

```bash
git clone https://github.com/last-refuge/omarchy-obsidian-circuit-theme.git
cd omarchy-obsidian-circuit-theme
omarchy plugin clone omarchy.dock
```

The clone command switches to a user-owned plugin named `<username>.dock`. If that clone already exists, do not overwrite it. Review its current changes and make a backup before applying this appearance patch.

From the repository root, check the patch and then apply it with a backup:

```bash
dock_dir="$HOME/.config/omarchy/plugins/$(id -un).dock"
patch --dry-run --fuzz=0 -d "$dock_dir" -p1 < extras/dock/obsidian-dock.patch
patch --backup --suffix=.before-obsidian-circuit --fuzz=0 -d "$dock_dir" -p1 < extras/dock/obsidian-dock.patch
omarchy restart shell
```

If the dry run fails, stop before applying the patch. The installed dock differs from the target version; compare it with the patch or wait for an updated patch. The patch does not need to be applied again when switching wallpapers.

## Remove

Restore the cloned file from the backup created above:

```bash
dock_dir="$HOME/.config/omarchy/plugins/$(id -un).dock"
cp "$dock_dir/DockWindow.qml.before-obsidian-circuit" "$dock_dir/DockWindow.qml"
omarchy restart shell
```

This restores the clone's pre-patch appearance. If you made other changes to that file afterward, compare the backup before replacing it.
