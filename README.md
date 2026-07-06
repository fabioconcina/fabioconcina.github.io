# fabioconcina.com

Personal site of Fabio Concina. Hand-written static HTML and CSS, served via
GitHub Pages at [fabioconcina.com](https://fabioconcina.com).

There is no build step or framework: the files in this repo are exactly what is
served.

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
CNAME           Custom domain (fabioconcina.com)
favicon.svg     Favicon
```

## Adding a blog post

Copy `blog/_template.html` into a new `blog/<slug>/index.html`, write the post,
then add the entry to `index.html`, `feed.xml`, and `sitemap.xml`.

## Social preview card

`static/img/og-card.png` (1200x630, used by `og:image` / `twitter:image`) is
rendered from `static/img/og-card.src.html`. To regenerate after editing the
source, screenshot it with a headless Chromium browser:

```
msedge --headless=new --disable-gpu --hide-scrollbars --window-size=1200,630 --screenshot="static\img\og-card.png" "static\img\og-card.src.html"
```
