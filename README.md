# go-authn.github.io

The landing page for [go-authn](https://github.com/go-authn), built with Hugo
and deployed by GitHub Actions.

The layout is the `go-*` family template: `layouts/partials/styles.html` for
the whole design system, `layouts/partials/theme-toggle.html` for the three-way
theme toggle (system / light / dark, defaulting to system), and a
`layouts/index.html` whose grid of repo cards is drawn from `[[params.repos]]`
in `hugo.toml`.

That stylesheet is **byte-identical** to the copies `go-fileshare`, `go-pkgx`
and `go-pdfkit` carry, and its colours come from `[params.brand]` — whose every
default is the cyan this org uses, so this site declares no brand block at all
and renders what it has always rendered. That property is checked rather than
claimed: build `go-pkgx`'s stylesheet with its `[params.brand]` commented out
and the emitted `<style>` block is identical to this one's.

Three per-repo flags in `hugo.toml` exist so the page never asserts something
it has not checked:

- `ci` — the CI badge renders only where a workflow actually exists, so the page
  never shows an empty "no status" badge.
- `godoc` — the card title links to pkg.go.dev only where a module is
  *published*; a command has no such page, and neither has a module that has not
  been released yet, so those cards link to the repository instead. The
  repository link is on every card either way, under the version.
- `cov` — what CI *enforces*, not what somebody measured on a laptop: an exact
  `100%` where the gate refuses anything less, and the recorded floor (`≥85%`)
  otherwise. The standard is 100% for every repo; not all of them meet it, and
  one number across all the cards was false the moment a command joined the org.
