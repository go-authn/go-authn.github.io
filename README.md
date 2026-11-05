# go-authn.github.io

The landing page for [go-authn](https://github.com/go-authn), built with Hugo
and deployed by GitHub Actions.

The layout is the `go-*` family template: `layouts/partials/styles.html` for
the whole design system, `layouts/partials/theme-toggle.html` for the three-way
theme toggle (system / light / dark, defaulting to system), and a
`layouts/index.html` on the reference's skeleton (#16). From `[[params.repos]]`
in `hugo.toml` it renders the list of repository links and the counts; the
road section is drawn from `[[params.phases]]`, each card showing the first
sentence of its `blurb`, cut at 140 characters. There is no card per
repository, so what each repository is belongs in its own README.

That stylesheet is **byte-identical** to the copies `go-fileshare`, `go-pkgx`
and `go-pdfkit` carry, and its colours come from `[params.brand]` — whose every
default is the cyan this org uses, so this site declares no brand block at all
and renders what it has always rendered. That property is checked rather than
claimed: build `go-pkgx`'s stylesheet with its `[params.brand]` commented out
and the emitted `<style>` block is identical to this one's.

The per-repo fields are described at the top of `hugo.toml`, each saying
whether the page renders it. Only `name` and `cov` are: `cov` is what CI
*enforces*, not what somebody measured on a laptop, and the stats line names
every repository whose gate is exactly `100%`. `ci`, `godoc`, `kind` and `type`
are kept as facts about each repository and are not shown.
