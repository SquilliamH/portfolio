# williamlh portfolio

Personal engineering portfolio, built with Jekyll and hosted on GitHub Pages.

## How it's organized

- `_config.yml`: site-wide settings (name, email, links). Available in templates as `site.*`.
- `_layouts/default.html`: the shell for every page (head, nav, footer).
- `_layouts/project.html`: the template for project pages, including the title block.
- `_projects/*.md`: one file per project. Front matter controls the title block and the home page listing; the body is the write-up.
- `_data/publications.yml`: the publications list on the home page.
- `index.html`: the home page.
- `assets/css/style.css`: all styling. Colors and fonts are tokens at the top.

## Adding a project

Copy an existing file in `_projects/`, rename it (the file name becomes the URL), and edit the front matter. `order` sets its position on the home page. Put images in `assets/img/<project-name>/` and reference them as `/assets/img/<project-name>/file.jpg`.

## Media guidelines

- Photos: export around 1600 px wide, JPG or WebP, under ~400 KB each.
- Hero loops: 5 to 10 seconds, no audio, 720p MP4, under ~8 MB.
- Full-length videos go on YouTube (unlisted is fine) and get linked or embedded.
- GitHub rejects files over 100 MB, so never commit raw footage.

## Previewing locally

Requires Ruby. Then:

    bundle install
    bundle exec jekyll serve

Open http://localhost:4000. Pages rebuild when you save.

## Switching williamlh.com over (do this last)

1. Settings > Pages > Custom domain: enter `www.williamlh.com`. This adds a `CNAME` file.
2. At the domain registrar, add the records from GitHub's "Managing a custom domain" docs and remove the Google Sites mapping.
3. Once the certificate is issued, check "Enforce HTTPS".
4. Set `url: https://www.williamlh.com` in `_config.yml`.
