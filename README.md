# totly-site

Marketing, privacy policy and terms site for [Totly](https://totly.plusmobileapps.com), built with
[MkDocs Material](https://squidfunk.github.io/mkdocs-material/).

## Local preview

```bash
pip install mkdocs-material
mkdocs serve
```

## Deploy

`.github/workflows/deploy.yml` builds the site on every push to `main`, adds the
[`well-known/`](well-known/README.md) app-association files, and publishes `site/` to the
`gh-pages` branch. In the repo's **Settings → Pages**, set the source to the `gh-pages` branch, keep
the custom domain `totly.plusmobileapps.com` (from `docs/CNAME`) and turn on *Enforce HTTPS*. The
domain needs a `CNAME` DNS record pointing at `plusmobileapps.github.io`.
