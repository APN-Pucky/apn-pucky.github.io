# alexander-neuwirth.com

Source for [alexander-neuwirth.com](https://alexander-neuwirth.com/), the
research website of Alexander Puck Neuwirth. Built with
[Jekyll](https://jekyllrb.com/) and hosted on GitHub Pages: fully static
output, no client-side JavaScript.

## Structure

- `_publications/`, `_software/`, `_research/`, `_notes/` — Markdown content
  collections, one file per entry. Add a new entry by adding a new file
  with the right front matter; see an existing file in each directory for
  the expected fields.
- `_layouts/`, `_includes/` — page templates and shared partials (nav,
  footer, SEO meta, JSON-LD for `Person`/`ScholarlyArticle`/`SoftwareSourceCode`).
- `assets/css/style.css` — the entire stylesheet: plain CSS, no
  preprocessor or framework, light/dark via `prefers-color-scheme`.
- `_config.yml` — site metadata and collection/permalink configuration.
- `cv.yaml` — single source of truth for the CV (see below).

## The CV

`cv.yaml` is rendered by [RenderCV](https://docs.rendercv.com/) into both
`assets/cv/alexander-puck-neuwirth-cv.pdf` (typeset PDF, for applications)
and `cv/generated.md` (plain Markdown, included on `/cv/`). This happens
automatically in `.github/workflows/pages.yml` on every push — **do not
hand-edit the generated PDF or `cv/generated.md`**; edit `cv.yaml` instead.

To regenerate locally:

```sh
pip install "rendercv[full]"
rendercv render cv.yaml
```

## Local development

```sh
bundle install
bundle exec jekyll serve
```

or, without Bundler, using system gems (`jekyll`, `jekyll-sitemap`):

```sh
jekyll serve
```

Then open <http://localhost:4000/>. Note that `bundle exec jekyll build`
alone will not regenerate the CV — run `rendercv render cv.yaml` first if
`cv.yaml` changed (the GitHub Actions workflow does both automatically).

## Deployment

The site builds and deploys via `.github/workflows/pages.yml` (GitHub
Actions), **not** GitHub Pages' legacy branch-based Jekyll build, because
the CV step needs to run `rendercv` (Python) before the Jekyll build. This
requires the repository's **Settings → Pages → Build and deployment →
Source** to be set to **"GitHub Actions"** rather than "Deploy from a
branch".
