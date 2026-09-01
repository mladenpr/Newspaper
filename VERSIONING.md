# Versioning

Newspaper follows [Semantic Versioning](https://semver.org) in the form
`MAJOR.MINOR.PATCH` (for example `1.2.0`). This matches what Obsidian
requires for community themes: the version lives in `manifest.json` and every
release is a GitHub release whose **tag is exactly the version number, with
no `v` prefix** (`1.2.0`, not `v1.2.0`).

## What each part means for a theme

A theme has no API, but users build on it anyway — with CSS snippets, with
the Style Settings they are used to, and with their own eyes. Version
numbers communicate how much of that an update may disturb.

**PATCH** (`1.0.0 → 1.0.1`) — fixes, no intentional change of look:

- Fixing a selector that broke on an Obsidian update.
- Correcting a colour, spacing, or contrast bug.
- Typos in comments or documentation-only changes shipped with a release.

**MINOR** (`1.0.1 → 1.1.0`) — additions and refinements that stay
backwards-compatible:

- Styling elements the theme didn't cover before (a plugin's pane, a new
  Obsidian feature).
- New optional looks (e.g. Style Settings support).
- Subtle visual refinements that don't change the theme's character.
- Raising `minAppVersion` because a new feature needs a newer Obsidian.

**MAJOR** (`1.1.0 → 2.0.0`) — changes a user will notice immediately or
that can break their customizations:

- Palette or typography overhauls; a redesign of the theme's character.
- Renaming or removing the theme's own CSS custom properties
  (`--newsprint-*`), which user snippets may reference.
- Dropping support for an Obsidian version users may still run.

## Release procedure

1. Update `version` in `manifest.json` (and `minAppVersion` if the release
   relies on newer Obsidian features).
2. Move the relevant entries in `CHANGELOG.md` from **Unreleased** to a new
   section for the version, dated `YYYY-MM-DD`.
3. Commit to `main` (via PR), then tag exactly the version:

   ```bash
   git tag 1.1.0
   git push origin 1.1.0
   ```

4. The [release workflow](.github/workflows/release.yml) verifies the tag
   matches `manifest.json`, then publishes a GitHub release with
   `manifest.json` and `theme.css` attached — the two files Obsidian
   downloads for installs and updates.

No terminal handy? The same workflow can be run manually from
**GitHub → Actions → Release theme → Run workflow** on `main`: it reads
the version from `manifest.json`, creates the matching tag, and publishes
the release.

Notes that keep releases working:

- The community directory reads `manifest.json` from the HEAD of the
  default branch, and users receive the files attached to the release whose
  tag matches that version — so the tagged commit must be on `main` and the
  two must agree.
- Never re-tag or delete a published release; ship a new PATCH instead.
