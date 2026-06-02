# TODO

Items deferred as out-of-scope from feature planning. Triage manually.

## From feature/github-pages-talks-site
| Item | Why deferred | Related decision | Added | Status |
|------|--------------|------------------|-------|--------|
| `jekyll-seo-tag` plugin | Skipped for v1 — no immediate need for richer link previews / SEO meta tags. Can be added with one line in `_config.yml` if shareability matters later. | Decision 15 | 2026-06-02 | Open |
| `jekyll-sitemap` plugin | Skipped for v1 — three pages don't need a sitemap.xml; can be enabled later if search-engine indexing becomes a priority. | Decision 15 | 2026-06-02 | Open |
| `jekyll-feed` plugin | Skipped for v1 — no current need for RSS subscription to talks. Easy to enable later. | Decision 15 | 2026-06-02 | Open |
| Custom domain (CNAME) | Project-page hosting at `<user>.github.io/ldx3/` is sufficient for v1; custom domain only worth doing if a domain is already owned. | Decision 12 | 2026-06-02 | Open |
| GH Actions PR build workflow | Native GH Pages build already fails loudly on bad builds; a duplicate workflow adds maintenance for no benefit at this scale. | Decision 13 | 2026-06-02 | Open |
| Richer talk front-matter fields (`tags`, `event`, `slides_url`) | No current use case; would add per-file overhead and inconsistency between files. Add only when an actual need arises. | Decision 4 | 2026-06-02 | Open |
| `jekyll-redirect-from` for old root-level `.md` URLs | The repo isn't deployed yet — no existing inbound links to preserve. | Decision 10 | 2026-06-02 | Open |
| Hand-rolled CSS / non-`tactile` theme | Tactile picked deliberately for distinctive look; revisit only if readability complaints arise. | Decisions 7, 8 | 2026-06-02 | Open |
| Mixed chronological feed on index | Talks/vendors are conceptually different; the two-section index is more scannable. | Decision 9 | 2026-06-02 | Open |
