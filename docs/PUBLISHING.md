# Publishing Broadsheet to the Obsidian community themes

This is the path from this repository to **Settings → Appearance → Themes**
in everyone's Obsidian. Follow it top to bottom; nothing here needs to be
done until in-vault testing is finished.

Source of truth: Obsidian's official
[Submit your theme](https://docs.obsidian.md/Themes/App+themes/Submit+your+theme)
and
[Theme guidelines](https://docs.obsidian.md/Themes/App+themes/Theme+guidelines)
pages. The checklists below were verified against them on 2026-09-01.

## 1 · Requirements — current status

Files Obsidian requires at the repository root:

| Requirement | Status |
| --- | --- |
| `manifest.json` with `name`, `version` (SemVer), `minAppVersion`, `author` | ✅ present |
| `theme.css` | ✅ present |
| `README.md` (an excerpt appears on the theme's listing page) | ✅ present |
| `LICENSE` (required; determines how others may use the theme) | ✅ MIT |
| Screenshot, recommended **512 × 288 px** | ✅ `screenshot.png` |

Guidelines the CSS must follow:

| Guideline | Status |
| --- | --- |
| No remote assets or network calls — fonts/images must work offline | ✅ system font stacks only; no `url()`, no `@import` |
| No `!important` declarations | ✅ none |
| Prefer Obsidian's CSS variables over complex selectors | ✅ variable-first throughout |
| Low-specificity selectors | ✅ |
| Theme name: no "Obsidian" in it, not already taken | ✅ "Broadsheet" — verified free against all 719 community themes on 2026-09-01 |

## 2 · Test in a real vault (do this first)

1. Copy `manifest.json` and `theme.css` into
   `<vault>/.obsidian/themes/Broadsheet/` in a **sandbox vault**, then in
   your main vault.
2. Walk through both **light and dark** modes:
   - editing view and reading view, with and without Readable line length;
   - headings `H1`–`H6`, links, tags, quotes, tables, callouts (several
     types), task lists, code blocks, embeds, footnotes;
   - the chrome: file explorer, search, tabs, settings, command palette,
     graph view;
   - core plugins you use (canvas, daily notes, outline, backlinks);
   - on mobile, if you use Obsidian mobile.
3. Fix what looks off; bump the version per [VERSIONING.md](../VERSIONING.md)
   as you go.
4. Optional but recommended before submission: retake `screenshot.png` and
   the `docs/assets/` images as **real in-app captures** of your test vault.
   The current images are previews rendered from the theme's palette and
   type styles, not screenshots of Obsidian itself.

## 3 · Cut the first release

When testing is done:

```bash
# 1. Make sure manifest.json says the version you're releasing (1.0.0)
# 2. Move the CHANGELOG "Unreleased" notes under the release heading
# 3. Then:
git tag 1.0.0
git push origin 1.0.0
```

The [release workflow](../.github/workflows/release.yml) publishes a GitHub
release with `manifest.json` and `theme.css` attached. Verify on the
repository's Releases page that both files are on the release — that is
what Obsidian downloads.

## 4 · Submit to the directory

1. Sign in at [community.obsidian.md](https://community.obsidian.md) with
   your Obsidian account.
2. Link your GitHub account (`mladenpr`) to verify repository ownership.
3. Add the theme, pointing at this repository.
4. The directory processes `manifest.json` at the HEAD of the default
   branch (`main`) and runs an automated review. The theme isn't
   installable until any automated-review errors are resolved.
5. Address feedback by updating the repository and publishing a **new
   release with an incremented version** — that is how reviewers and, later,
   users receive changes.

## 5 · After acceptance

- Ship fixes as PATCH releases and additions as MINOR releases
  ([VERSIONING.md](../VERSIONING.md)); users get updates automatically via
  the matching release tags.
- Keep [CHANGELOG.md](../CHANGELOG.md) current — it's the record users and
  reviewers read.
- Never delete or re-tag a published release; supersede it with a new
  version.
