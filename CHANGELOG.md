# Changelog

All notable changes to Newspaper are documented here. The format follows
[Keep a Changelog](https://keepachangelog.com/en/1.1.0/), and the project
adheres to [Semantic Versioning](https://semver.org) as described in
[VERSIONING.md](VERSIONING.md).

## [Unreleased]

Nothing yet.

## [1.0.1] — 2026-09-01

Compatibility fixes for the community directory's automated review.

### Fixed

- Link underline tinting no longer uses `color-mix()`; the hairline
  underline colour now comes from the accent variables, which render
  identically and work on older engines.
- Raised `minAppVersion` to 1.5.0 so the declared floor matches the
  support level of the `text-decoration-*` properties the underline
  styling relies on.
- Removed placeholder-style wording ("coming soon") from the README's
  installation section, flagged by the automated review.

## [1.0.0] — 2026-09-01

Initial release.

### Added

- Serif reading typography: Charter / Iowan Old Style / Georgia system
  stack, 1.7 leading, ~42 em measure, old-style figures in running text and
  lining tabular figures in tables and code.
- Editorial heading scale with tightened display tracking; note title as a
  masthead with hairline rule; `H2` column-divider rules; `H5` in small
  caps; `H6` as an uppercase kicker.
- Newspaper furniture: pull-quote blockquotes, double-rule `---` dividers,
  financial-page tables, hairline callout boxes with uppercase labels,
  newspaper-style underlined links.
- Warm light palette (ivory paper, warm near-black ink, clay/claret accent)
  and warm charcoal dark palette; muted ink-like section colours for
  callouts in both modes.
- Quiet interface: Georgia serif chrome at small sizes, opaque warm window
  frame (no grey glass with Translucent window), warm caret and selection,
  reduced corner radii, warm scrollbars.
