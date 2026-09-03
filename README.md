# go-authn.github.io

The landing page for [go-authn](https://github.com/go-authn), built with Hugo
and deployed by GitHub Actions.

The layout is the `go-*` family template: a single self-contained
`layouts/index.html` with inline `:root` variables, a three-way theme toggle
(system / light / dark, defaulting to system), and a grid of repo cards drawn
from `[[params.repos]]` in `hugo.toml`.

The CI badge on a card renders only where a workflow actually exists — `ci =
true` is set per repo rather than assumed, so the page never shows an empty
"no status" badge.
