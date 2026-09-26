# Haokun Ren Academic Homepage

A bilingual Jekyll academic homepage built on [AcadHomepage](https://github.com/RayeRen/acad-homepage.github.io) and its Minimal Mistakes theme foundation.

| Language | Route |
| --- | --- |
| Chinese | `/` |
| English | `/en/` |

## Content

- Edit the localized research sections in `_pages/about.md` and `_pages/en.md`.
- Keep masthead labels in `_data/navigation.yml`.
- Maintain paper titles, author order, bilingual summaries, and arXiv/PDF links in `_data/publications.yml`.
- The profile name and localized biography are stored under `author` in `_config.yml`.

## Framework

The shared layout, masthead, sidebar profile, Sass theme, and paper boxes use the AcadHomepage/Minimal Mistakes component structure. Upstream theme assets are based on AcadHomepage commit [`2cc1577`](https://github.com/RayeRen/acad-homepage.github.io/tree/2cc1577eeaf2f74dede6d016a70722dbd409ea2f). This project retains the upstream MIT license and notices for its theme dependencies.

## Local development

```bash
bundle install
bash run_server.sh
bundle exec jekyll build
```

There is no automated test suite. Verify changes by building and inspecting `_site/index.html` and `_site/en/index.html`.

## Optional integrations and deployment

Google Analytics and Scholar citation display are disabled until their IDs and data source are configured. `google_scholar_crawler/` remains a standalone utility and has no active homepage workflow. Pushing to `master` triggers GitHub Pages deployment.
