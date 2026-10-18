# fabioconcina.com

Personal site of Fabio Concina. Hand-written static HTML and CSS, served via
Cloudflare Pages at [fabioconcina.com](https://fabioconcina.com). GitHub Pages
still redirects `fabioconcina.github.io` there (the CV and LinkedIn link to
those URLs), so keep `CNAME`.

There is no build step or framework: the files in this repo are exactly what is
served. That includes authoring sources like `blog/_template.html` and the
`*.src.html` card sources, so `_headers` marks them `noindex`.

## Local preview

Serve the directory over HTTP (opening files directly breaks absolute paths):

```bash
python -m http.server 8000
# then visit http://localhost:8000
```

## Layout

```
index.html      Homepage
style.css       Site-wide styles
blog/           Blog posts (one folder per post, each with index.html)
                _template.html is the starting point for new posts
projects/       Project pages (one folder per project, each with index.html)
static/         Assets: fonts/, img/, pdf/
feed.xml        RSS feed
sitemap.xml     Sitemap
robots.txt      Crawler rules
_headers        Cloudflare Pages response headers
CNAME           GitHub Pages custom domain (redirects fabioconcina.github.io)
favicon.svg     Favicon
```

## Adding a blog post

Copy `blog/_template.html` into a new `blog/<slug>/index.html`, write the post,
then:

1. Add the entry to `index.html`, `blog/index.html`, `feed.xml`, and
   `sitemap.xml`.
2. Generate the post's social preview card (see below) as
   `static/img/og-card-<slug>.png`.

## CV and LinkedIn content

The detailed career record lives in `../cv/career.html`, alongside its generator
in the separate `cv` project. The homepage is an independent introduction:
changing its wording, layout, or selected highlights does not change the CV.

To update CV or LinkedIn content, edit `../cv/career.html` (or `extras.yaml` for
CV-specific details), then run:

```bash
../cv/.venv/bin/python ../cv/build.py --check  # inspect generated-output drift
../cv/.venv/bin/python ../cv/build.py          # regenerate text and PDFs
```

The build copies the public PDF to `static/pdf/cv-web.pdf`. Full HTML conventions
and build instructions are in `../cv/CLAUDE.md`.

## Analytics

Pageviews are counted with [GoatCounter](https://www.goatcounter.com/)
(hosted, privacy-friendly, no cookies): dashboard at
[fabioconcina.goatcounter.com](https://fabioconcina.goatcounter.com/). Every
page (and `blog/_template.html`) includes the script tag just before
`</body>`. GoatCounter ignores localhost, so local previews don't pollute the
stats.

## Social preview cards

The 1200x630 images used by `og:image` / `twitter:image` are rendered from
committed HTML sources with a headless Chromium browser:

- `static/img/og-card.src.html` -> `static/img/og-card.png` (homepage)
- `static/img/og-card-post.src.html` -> `static/img/og-card-<slug>.png`
  (one per blog post or project page; pass the title as a `title` query
  parameter, URL-encoded)

Any Chrome or Chromium binary works. Set `CHROME` to its path, e.g.
`/Applications/Google Chrome.app/Contents/MacOS/Google Chrome`, or Playwright's
Chrome for Testing under `~/Library/Caches/ms-playwright/chromium-*/`. Run from
the repo root:

```bash
# Homepage card
"$CHROME" --headless=new --disable-gpu --hide-scrollbars --window-size=1200,630 \
  --screenshot="$PWD/static/img/og-card.png" "file://$PWD/static/img/og-card.src.html"

# Per-post card (file:// URL needed for the query parameter)
"$CHROME" --headless=new --disable-gpu --hide-scrollbars --window-size=1200,630 \
  --screenshot="$PWD/static/img/og-card-<slug>.png" \
  "file://$PWD/static/img/og-card-post.src.html?title=Post%20Title"
```
