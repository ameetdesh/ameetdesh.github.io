# ameetdesh.github.io

Personal site. Plain [Jekyll](https://jekyllrb.com), built automatically by
GitHub Pages on every push to `main`. Every page is a Markdown file — there is
no build step to run locally and no dependencies to keep current. The design is
dark; printing forces a light palette so PDFs come out readable.

## Layout

```
index.md                 homepage (bio + links)
writeups/index.md        auto-generated list of everything in writeups/
writeups/*.md            one file per writeup
_layouts/default.html    the only template
assets/css/style.css     the only stylesheet
_config.yml              site title, links, resume path
```

## Editing

**Change the homepage** — edit `index.md`, commit, push. Live in ~30 seconds.

**Change your links** — edit the `github_username`, `linkedin_username`,
`resume_url` and `email` values in `_config.yml`. They feed the header nav and
the footer on every page.

**Update the resume** — replace `resume_ameet_deshpande.pdf` in the repo root.

**Add a writeup** — create `writeups/my-note.md` with this front matter:

```yaml
---
layout: default
title: "Title of the note"
subtitle: "One line describing it"
date: 2026-09-09
permalink: /writeups/my-note/
math: true          # only if the note contains LaTeX
---
```

Then write Markdown below it. It appears on `/writeups/` automatically, newest
first. Do not repeat the title as an `# H1` in the body — the layout renders it.

**Add a PDF, tool or anything that is not Markdown** — list it under `extras:`
in the front matter of `writeups/index.md`:

```yaml
extras:
  - title: Battery Optimizer
    subtitle: One line describing it
    url: /pyodide_optimizer_standalone.html
    date: August 2026
    tag: Interactive        # small chip next to the title; PDF, Interactive, Talk…
```

Markdown notes are listed first, then these, in the order you write them.

**Change the colours** — everything lives in the `:root` block at the top of
`assets/css/style.css`. Keep body text and metadata above a 4.5:1 contrast ratio
against `--bg`.

**Math** — set `math: true` in the front matter and use `$$ ... $$` for display
equations, `$ ... $` for inline. MathJax loads only on pages that ask for it.

**Section links** — kramdown generates heading ids that differ from GitHub's for
headings starting with a number. Where a page has an in-page table of contents,
pin the ids explicitly by putting an IAL on the line *after* the heading:

```markdown
## 1. A charger is not quite like a pump
{: #1-a-charger-is-not-quite-like-a-pump }
```

**Start a blog** — create `_posts/YYYY-MM-DD-slug.md` with `layout: default` and
a `title`. Posts already flow into the `/writeups/` list and into `feed.xml`.

## Previewing locally (optional)

Not required — GitHub builds the site for you. If you want it anyway:

```sh
gem install --user-install jekyll jekyll-sitemap jekyll-feed
jekyll serve
```

Then open <http://localhost:4000>.
