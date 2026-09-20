# Birko-Framework.github.io

The landing site for the **[Birko-Framework](https://github.com/Birko-Framework)** organisation —
served at **<https://birko-framework.github.io/>**.

## What this is

One self-contained `index.html`. No build step, no bundler, no dependencies — nothing to install
and nothing to break between a commit and the live page. Pushing to `main` is the whole deploy.

| File | Purpose |
|---|---|
| `index.html` | The entire site — markup, styles and ~60 lines of script |
| `.nojekyll` | Tells GitHub Pages to serve the files as-is, skipping the Jekyll build |

## Design tokens

The CSS custom properties at the top of `index.html` are **transcribed** from
[`Birko.DesignTokens/tokens.json`](https://github.com/Birko-Framework/Birko.Framework/blob/main/Birko.DesignTokens/tokens.json)
— the single source of truth that the web CSS and the Avalonia AXAML are both generated from. The
light values come from the `tokens.css` sheet, the dark ones from `themes/dark.css`.

⚠ **Nothing regenerates this file.** The framework's generator writes `tokens.css` for consumers
that bundle it; this page deliberately inlines a subset instead, so it stays a single file with no
build. If a token changes upstream, change it here too. The alternative — importing the generated
sheet — would mean a build step and a sync job for a page that renders four colours.

## Facts quoted on the page

These come from the framework repo and will drift. To re-measure, from the root of a
`Birko.Framework` checkout:

```sh
ls -d Birko.* | wc -l          # 178 dirs = 177 libraries + the Birko.Framework aggregator
ls -d tests/Birko.*/ | wc -l   # 167 test projects
```

The per-area counts in the *Projects* section:

```sh
ls -d Birko.* | sed 's/^Birko\.//' | cut -d. -f1 | sort | uniq -c | sort -rn
```

Storage-backend and component counts come from the framework `README.md`; the code samples are
taken from the [wiki](https://github.com/Birko-Framework/Birko.Framework/wiki), where a CI job
compiles every snippet against the current framework.

## Enabling Pages

Settings → Pages → Source: **Deploy from a branch** → `main` / `/ (root)`.

A repo named `<org>.github.io` serves at the org root, so no path prefix and no custom domain
configuration is needed.

## Related

The organisation's profile README — what renders at the top of
<https://github.com/Birko-Framework> — lives in the
[`.github`](https://github.com/Birko-Framework/.github) repo, not here.
