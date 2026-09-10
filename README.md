# go-authn.github.io

The landing page for [go-authn](https://github.com/go-authn), built with Hugo
and deployed by GitHub Actions.

The layout is the `go-*` family template: a single self-contained
`layouts/index.html` with inline `:root` variables, a three-way theme toggle
(system / light / dark, defaulting to system), and a grid of repo cards drawn
from `[[params.repos]]` in `hugo.toml`.

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
