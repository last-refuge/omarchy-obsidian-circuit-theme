# Submit Obsidian Circuit to the Omarchy theme gallery

The theme repository is the installation source. The gallery listing is a separate pull request to [omacom/omarchy-site](https://github.com/omacom/omarchy-site#adding-your-theme).

## Prepared files

- Root `preview.png`: a real 16:9 desktop capture with a terminal and an editor, using the Obsidian Circuit wallpaper and theme.
- `docs/gallery/obsidian-circuit.webp`: the gallery copy, 1200 × 675 and under 100 KB.
- `docs/gallery/entry.html`: the figure block linking to this theme repository.

## Gallery pull request

Fork and clone `omacom/omarchy-site`, and create a branch for the listing. Copy `docs/gallery/obsidian-circuit.webp` from this repository to `assets/themes/obsidian-circuit.webp` in the site repository. Insert the contents of `docs/gallery/entry.html` into `themes/index.html` in alphabetical order by **Obsidian Circuit**.

Follow the site repository's current instructions and any applicable `AGENTS.md`. At preparation time, its README specifies Node 24 or newer and Python 3.13. Run `npm ci`, `npm run port`, `npm run lint`, `npm run typecheck`, and `npm test`; check the build and parity checks as well. Commit the gallery image and source entry, plus generated changes explicitly required by the current site instructions. Open a pull request titled **Add Obsidian Circuit community theme**.

Suggested PR body:

> Adds Obsidian Circuit to the community theme gallery with a 1200 × 675 WebP preview and an alphabetical entry linking to its public installation repository. The theme includes a Starship-derived palette, custom shell surfaces, and four AI-generated wallpapers. The preview is a real Omarchy desktop capture with a terminal and editor, using the theme's wallpaper.
>
> Theme repository: https://github.com/last-refuge/omarchy-obsidian-circuit-theme
>
> Validation: include the site checks actually run on the submission branch.

## Theme registry

The official [theme registry](https://github.com/omacom/omarchy-theme-registry#submit-your-theme) also documents an issue-based submission flow. Its [submission form](https://github.com/omacom/omarchy-theme-registry/issues/new?template=submit-theme.yml) accepts the public repository URL, runs automated validation, and opens a listing PR on success. If validation needs changes, fix the theme repository and comment `/recheck` on the issue.

The root palette, backgrounds, preview, README, and license are arranged to support that validation. Optional patch/documentation files may be ignored by theme installers and are not automatically executed. Listing in either gallery does not make the theme a bundled Omarchy default.
