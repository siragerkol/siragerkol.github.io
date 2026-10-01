# Personal academic website

Built with [Hugo](https://gohugo.io) and the [HugoBlox Academic CV](https://github.com/HugoBlox/theme-academic-cv) template.

## Where to edit

| What | File |
|---|---|
| Name, role, bio, social links, interests | `data/authors/me.yaml` |
| Profile photo | `assets/media/authors/me.jpg` (replace the file, keep the name) |
| Browser tab icon (favicon) | `assets/media/icon.svg` (purple document icon, transparent); `assets/media/icon.png` is the raster copy used for phone home-screen icons |
| CV PDF (CV menu tab and profile icon, both open in a new tab) | `static/uploads/cv.pdf` |
| Homepage sections | `content/_index.md` |
| News items | the `News` block in `content/_index.md` (one bullet per item, newest first) |
| Publications (one folder per paper) | `content/publications/<paper>/index.md` |
| Menu | `config/_default/menus.yaml` |
| Colours, fonts, site name, description | `config/_default/params.yaml` |
| Site URL (set before deploying) | `config/_default/hugo.yaml` → `baseURL` |

Current palette: light mode is the `default` pack with Northwestern purple (#4E2A84) and a teal secondary set under `theme.colors_light`; dark mode is the `minimal` pack unmodified (`theme.pack` has separate `light` and `dark` entries). The light-mode header tint and a few layout tweaks live in `assets/css/custom.css`.

Colour themes available in `params.yaml` → `theme.pack`: coffee, contrast, cupcake, default, dracula, marine, matcha, minimal, retro, solar, synthwave.
Font packs in `typography.pack`: academic, developer, editorial, geometric, humanist, modern, system.

## Adding a publication

1. Copy any existing folder in `content/publications/` to a new folder.
2. Edit `index.md`: title, authors (write `me` for yourself), date, journal details and abstract.
3. Edit the `links` list at the bottom. Buttons appear in the order listed. Supported entries:

   ```yaml
   links:
     - type: doi
       id: '10.1000/xyz123'
     - type: preprint
       provider: arxiv
       id: '2501.01234'
     - type: project
       label: Website
       url: 'https://example.com'
     - type: code
       url: 'https://github.com/you/repo'
     - type: pdf
       url: 'paper.pdf'        # a PDF placed in the same folder as index.md
   ```

## Template overrides

A few theme templates are overridden in `layouts/`. Each file starts with a comment saying what it changes. If the theme is upgraded (see `.github/workflows/upgrade.yml`), check these still work:

| File | Purpose |
|---|---|
| `layouts/list.html` | side padding on list pages (phones) |
| `layouts/single.html` | wider paper pages; venue row labelled Journal / Institution |
| `layouts/_partials/components/headers/navbar.html` | menu items with `params.target: _blank` open in a new tab (CV) |
| `layouts/_partials/components/next-in-series.html` | prev/next paper links show only the year; right-aligned on phones |
| `layouts/_partials/functions/has_attachments.html` | DOI / arXiv ids count as link buttons |
| `layouts/_partials/page_links.html` | local PDFs open in a new tab; no stray underline before icons |
| `layouts/_partials/page_metadata_authors.html` | your name in bold in author lists |
| `layouts/_partials/views/citation.html` | clickable publication cards, reverse-numbered on the Publications page |

## Running locally

```sh
npm install                       # first time only
PATH="$PWD/node_modules/.bin:$PATH" hugo server
```

Then open http://localhost:1313/. Changes to content reload automatically.

## Deploying to GitHub Pages

1. Create a GitHub repository named `<username>.github.io`.
2. Set `baseURL` in `config/_default/hugo.yaml` to `https://<username>.github.io/`.
3. Push this folder to the `main` branch.
4. In the repo, go to Settings → Pages → Source and choose **GitHub Actions**.

The included workflow in `.github/workflows/deploy.yml` builds and publishes the site on every push.
