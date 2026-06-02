# github-pages-talks-site

A static site, hosted on GitHub Pages, that presents the repo's talk-note markdown files as readable pages. New talks and vendor notes can be added by dropping a single markdown file (with front matter) into the relevant collection folder.

## Context
_Codebase facts and constraints learned during grilling._
- Three talk-note files at repo root: `building-for-production.md` (~95 lines), `state-of-ai-in-software-development.md` (~58 lines), `vendor-booth-notes.md` (~22 lines).
- All three share the same informal structure: `#` H1 title, then a blockquote datestamp (`> Conference talk notes — 2026-06-02`), then `##` H2 sections (speakers, takeaways, notes, action items).
- None of the notes have YAML front matter. All metadata (date, speaker, source URL) lives inline as Markdown prose / blockquotes.
- No images, diagrams, or code blocks in any file.
- Cross-links between notes use bare relative paths with `.md` extensions (e.g. `vendor-booth-notes.md`), which most SSGs rewrite to clean URLs at build time and would break unless handled.
- `README.md` is a one-line stub (`# ldx3`) — provides no site landing content.
- Default branch is `main`. Repo is clean.

## Decisions
_Resolved through grilling. Each entry references the question that produced it._
1. **Build approach: native Jekyll on GitHub Pages** — GH Pages builds the site itself from a `_config.yml` + layout + markdown sources. No GH Actions, no Node toolchain, no build step to maintain. Structure must make adding a new talk-note markdown file trivial.
2. **Source layout: Jekyll collection `_talks/`** — each talk is a `.md` file in `_talks/`. The index page iterates `site.talks`, so adding a new talk is a single-file change. URLs are `/talks/<slug>/`. The three existing root-level talk files are moved into `_talks/` as part of the migration.
3. **Metadata: YAML front matter per talk file** — adds machine-readable `title`, `date`, `speaker`, etc. to each `.md`. One-time edit of the 3 existing files; every new talk includes a small front-matter header.
4. **Front-matter fields (talks): `title`, `date` (YYYY-MM-DD), `speaker`, `summary`** — minimum viable set. Covers index rendering (chronological sort, speaker line, one-line blurb), the page `<h1>`, and the HTML `<meta description>`. `source_url` and similar stay inline in the body where they already live.
5. **Second collection: `_vendors/` — "Vendors to explore"** — separate from `_talks/`. `vendor-booth-notes.md` becomes `_vendors/harness.md`. URLs are `/vendors/<slug>/`. The index page renders two sections: "Talks" and "Vendors to explore". The cross-link from `building-for-production` to the vendor entry resolves to `/vendors/harness/`.
6. **Front-matter fields (vendors): `title`, `url`, `summary`, `seen_at`** — vendor name, homepage URL, one-line description, event/date string. Parallels the talk field set but tuned to "things to follow up on" rather than session notes.
7. **Styling: built-in GitHub Pages theme** — use a Jekyll theme supported natively by GH Pages (set via `theme:` in `_config.yml`). Avoids hand-rolled CSS; specific theme to be chosen in Q8.
8. **Theme: `tactile`** — supported GH Pages theme. Distinctive textured aesthetic; applied via `theme: jekyll-theme-tactile` in `_config.yml`.
9. **Landing page layout: two labelled sections, rich list per item** — "Talks" (newest-first by `date`, each row showing date + title link + speaker + `summary` blurb) and "Vendors to explore" (alphabetical by `title`, each row showing title link + `url` + `summary` + `seen_at`). Index is a single template iterating `site.talks` and `site.vendors` — zero edits when adding new content.
10. **Cross-link rewriting: Liquid `{% link %}` tags** — every cross-reference in talk/vendor markdown uses `{% link _talks/<slug>.md %}` or `{% link _vendors/<slug>.md %}`. Jekyll validates the path at build time, so a rename or delete breaks the build loudly instead of leaving a silent 404.
11. **Two separate landing files: `index.md` for the site, `README.md` for the repo** — `index.md` contains the Talks + Vendors lists. `README.md` is rewritten with a one-paragraph repo description, the live site URL, and a short "How to add a new talk / vendor" guide. Each file targets its own audience.
12. **Hosting: GH Pages project page at `https://<user>.github.io/ldx3/`** — `baseurl: "/ldx3"` in `_config.yml`; all internal links go through `{% link %}` (talks/vendors) or the `relative_url` filter (assets) so they resolve correctly under the prefix locally and deployed. No custom domain for v1.
13. **Local preview: `Gemfile` with `github-pages` gem, `_site/` and `.jekyll-cache/` gitignored** — `bundle install` once, then `bundle exec jekyll serve` for live reload at `http://localhost:4000/ldx3/`. Enables fast iteration on layout, theme overrides, and index page without relying on GH Pages build cycles.
14. **Body duplication cleanup: strip body `# H1`, blockquote datestamp, and `## Speakers` section from each migrated talk file** — layout renders one `<h1>{{ page.title }}</h1>` plus a metadata line (`{{ page.date | date: "%Y-%m-%d" }} · {{ page.speaker }}`) from front matter; the body holds only the unique content (Key takeaways, Notes, Action items, etc.). Single source of truth for metadata.
15. **Plugins: none for v1** — no `jekyll-seo-tag`, `jekyll-sitemap`, or `jekyll-feed`. Stays minimal; can be layered on later if shareability/discoverability matter.

## Slices

### Slice 1 — Skeleton Jekyll site builds locally with project baseurl
**Outcome:** `bundle exec jekyll build` produces a valid `_site/` directory containing at least `index.html`, all internal URLs prefixed with `/ldx3/`.
**Test (Red):** A repeatable verification — run `bundle exec jekyll build` and assert (a) exit code 0, (b) `_site/index.html` exists, (c) any absolute internal link in `_site/index.html` starts with `/ldx3/`. Files: documented in the slice's commit message (a shell one-liner used as the manual gate, since there is no Ruby test suite in this repo).
**Implementation (Green):** Create `_config.yml` (with `title`, `baseurl: "/ldx3"`, `url: "https://<user>.github.io"`, empty `collections:` block reserved for later slices), `Gemfile` (`source "https://rubygems.org"`, `gem "github-pages", group: :jekyll_plugins`), placeholder `index.md` with a single `<h1>` and a TODO marker, and a `.gitignore` adding `_site/`, `.jekyll-cache/`, `Gemfile.lock` (or commit `Gemfile.lock` if desired — see Open Question 2). Files: `_config.yml` (CREATE), `Gemfile` (CREATE), `index.md` (CREATE), `.gitignore` (CREATE).
**Refactor:** None expected.
**Acceptance:** `bundle exec jekyll build` exits 0; `_site/index.html` exists; absolute links in output use `/ldx3/`.

### Slice 2 — `_talks/` collection renders one talk page from front matter
**Outcome:** Visitors reach `/ldx3/talks/building-for-production/` and see the talk's title, date, speaker, and body content with no duplicate `<h1>`.
**Test (Red):** Build the site and assert `_site/talks/building-for-production/index.html` (a) exists, (b) contains the front-matter title in `<h1>` exactly once, (c) contains the rendered body content (e.g. "Key takeaways" heading), (d) does NOT contain the old blockquote datestamp or the old `## Speakers` heading.
**Implementation (Green):** Add `collections: talks: { output: true, permalink: /talks/:name/ }` and `defaults` for the `talks` collection setting `layout: talk` in `_config.yml`. Create `_layouts/talk.html` that extends nothing (or a minimal HTML skeleton) and renders `<h1>{{ page.title }}</h1>`, a metadata line `{{ page.date | date: "%Y-%m-%d" }} · {{ page.speaker }}`, then `{{ content }}`. Move `building-for-production.md` → `_talks/building-for-production.md`, add front matter (`title`, `date: 2026-06-02`, `speaker: "Liz Fong (Honeycomb)"`, `summary: "<one-liner>"`), strip the body `# H1`, blockquote datestamp, and `## Speakers` section. Files: `_config.yml` (UPDATE), `_layouts/talk.html` (CREATE), `_talks/building-for-production.md` (CREATE), `building-for-production.md` (DELETE).
**Refactor:** Extract the metadata line into a `_includes/metaline-talk.html` partial if used elsewhere — defer otherwise.
**Acceptance:** Built `_site/talks/building-for-production/index.html` contains exactly one `<h1>` with the front-matter title, a metadata line, and the unique body content.

### Slice 3 — `_vendors/` collection renders one vendor page from front matter
**Outcome:** Visitors reach `/ldx3/vendors/harness/` and see the vendor's name, URL, summary, and the "seen at" event, followed by the body notes.
**Test (Red):** Build and assert `_site/vendors/harness/index.html` (a) exists, (b) contains `<h1>` with the vendor `title`, (c) contains a clickable `<a href>` to the vendor `url`, (d) contains the `seen_at` text and `summary` text in the metadata line, (e) renders the body notes.
**Implementation (Green):** Add `collections: vendors: { output: true, permalink: /vendors/:name/ }` and a default layout `vendor` for the collection in `_config.yml`. Create `_layouts/vendor.html` rendering `<h1>{{ page.title }}</h1>`, a metadata line (`<a href="{{ page.url }}">{{ page.url }}</a> · seen at {{ page.seen_at }}`), `<p>{{ page.summary }}</p>`, then `{{ content }}`. Move `vendor-booth-notes.md` → `_vendors/harness.md`, add front matter (`title: "Harness"`, `url: "https://www.harness.io"`, `summary: "<one-liner>"`, `seen_at: "LDX3 2026-06-02"`), strip the body `# H1` and any datestamp blockquote. Files: `_config.yml` (UPDATE), `_layouts/vendor.html` (CREATE), `_vendors/harness.md` (CREATE), `vendor-booth-notes.md` (DELETE).
**Refactor:** If `_layouts/talk.html` and `_layouts/vendor.html` share substantial HTML (head, footer), extract a `_layouts/default.html` and have both extend it.
**Acceptance:** Built `_site/vendors/harness/index.html` contains the title, a working URL link, the `seen_at` and `summary` strings, and the rendered body.

### Slice 4 — Second talk migrated into `_talks/`
**Outcome:** The DX "State of AI in Software Development" talk renders at `/ldx3/talks/state-of-ai-in-software-development/` using the same layout and metadata pattern.
**Test (Red):** Build and assert `_site/talks/state-of-ai-in-software-development/index.html` exists, contains the front-matter title in `<h1>`, the metadata line, and the unique body content; does not contain the old blockquote datestamp or `## Speakers` section.
**Implementation (Green):** Move `state-of-ai-in-software-development.md` → `_talks/state-of-ai-in-software-development.md`, add front matter (`title`, `date: 2026-06-02`, `speaker: "<speaker name from existing content>"`, `summary: "<one-liner>"`), strip body duplicates. Files: `_talks/state-of-ai-in-software-development.md` (CREATE), `state-of-ai-in-software-development.md` (DELETE).
**Refactor:** None.
**Acceptance:** Built page exists at the expected URL with correct title, metadata, and body.

### Slice 5 — Cross-links rewritten with `{% link %}` and resolve to new URLs
**Outcome:** The link from the Liz Fong talk to the Harness vendor entry (and the reciprocal back-link) work in the built site and break the build if either target is renamed.
**Test (Red):** Build and assert (a) `_site/talks/building-for-production/index.html` contains an anchor whose `href` ends with `/vendors/harness/`, (b) `_site/vendors/harness/index.html` contains an anchor whose `href` ends with `/talks/building-for-production/`, (c) temporarily renaming one of the targets causes `jekyll build` to exit non-zero (validated manually during the slice; reverted before commit).
**Implementation (Green):** Replace bare `vendor-booth-notes.md` and `building-for-production.md` references in the two files with Liquid `{% link _vendors/harness.md %}` and `{% link _talks/building-for-production.md %}` respectively. Files: `_talks/building-for-production.md` (UPDATE), `_vendors/harness.md` (UPDATE).
**Refactor:** None.
**Acceptance:** Both rendered hrefs resolve to the correct collection URL; build fails if a link target is renamed.

### Slice 6 — `index.md` renders Talks + Vendors lists with rich rows
**Outcome:** Visitors at `/ldx3/` see two clearly labelled sections — "Talks" (newest-first) and "Vendors to explore" (alphabetical) — each row showing the rich metadata defined in Decisions 9.
**Test (Red):** Build and assert `_site/index.html` contains (a) a "Talks" heading, (b) a "Vendors to explore" heading, (c) all migrated talk titles in the order newest-first by date (use stable tie-breaker — see Open Question 1), (d) all vendor titles in alphabetical order, (e) for each talk row: date, title (linked), speaker, summary, (f) for each vendor row: title (linked), url, summary, seen_at.
**Implementation (Green):** Rewrite `index.md` with Liquid: `{% assign talks = site.talks | sort: "date" | reverse %}`, `{% assign vendors = site.vendors | sort: "title" %}`, then two `<section>` blocks with `<ul>` of rows. Each talk row links via `{{ talk.url | relative_url }}`; each vendor row uses `{{ vendor.url | relative_url }}` for its internal page link and `{{ vendor.url }}` (front-matter `url` field) for the external link. Files: `index.md` (UPDATE — replace placeholder from Slice 1).
**Refactor:** Extract row template into `_includes/talk-row.html` and `_includes/vendor-row.html` only if the inline Liquid grows past ~10 lines per row.
**Acceptance:** Visiting `/ldx3/` in the local preview shows both labelled sections with all current entries rendered in the correct order with all required fields.

### Slice 7 — `tactile` theme applied and layouts inherit from it cleanly
**Outcome:** The site renders with the tactile theme (textured background, theme typography) on both the index and individual pages, without breaking the per-page metadata line added in Slices 2 and 3.
**Test (Red):** Build and assert (a) `_site/index.html` references the tactile theme's CSS asset (e.g. via `<link rel="stylesheet">` to a path containing `assets/css/style.css` or the tactile equivalent), (b) the metadata line and content from Slices 2–3 still render on a talk and vendor page, (c) `index.md` styling does not collide with the theme's default homepage rendering.
**Implementation (Green):** Set `theme: jekyll-theme-tactile` in `_config.yml`. If the `talk` and `vendor` layouts were previously standalone HTML skeletons, refactor them to use `layout: default` (the tactile theme provides a `default` layout) so they inherit the theme chrome, and keep only the title + metadata line + `{{ content }}` portion in the talk/vendor layouts. Files: `_config.yml` (UPDATE), `_layouts/talk.html` (UPDATE), `_layouts/vendor.html` (UPDATE).
**Refactor:** Remove any HTML skeleton (`<html>`, `<head>`, `<body>`) duplicated between layouts since the theme provides it.
**Acceptance:** Local preview shows tactile-styled pages; metadata lines and content still render correctly on every page type.

### Slice 8 — `README.md` rewritten as repo intro with "how to add" guide
**Outcome:** A new visitor to the GitHub repo page sees a one-paragraph description, a link to the live site, and a concise guide that tells them exactly which folder and which front-matter fields to use to add a new talk or vendor.
**Test (Red):** Read `README.md` after the change and assert it contains (a) a one-paragraph description of the project, (b) a working link to `https://<user>.github.io/ldx3/`, (c) a "How to add a new talk" section listing the path (`_talks/<slug>.md`) and the four front-matter fields (`title`, `date`, `speaker`, `summary`), (d) a "How to add a new vendor" section listing the path (`_vendors/<slug>.md`) and the four front-matter fields (`title`, `url`, `summary`, `seen_at`), (e) a one-line note on running local preview (`bundle install && bundle exec jekyll serve`).
**Implementation (Green):** Rewrite `README.md` with the structure above. Files: `README.md` (UPDATE).
**Refactor:** None.
**Acceptance:** README contains all the elements listed in the test; live-site URL placeholder uses the user's actual GH username (resolved by Open Question 3 before push).

## Deferred (out of scope)
_Items resolved as "not this feature" during grilling. Consolidated to `/TODO.md` at termination._

| Item | Why deferred | Related decision |
|------|--------------|------------------|
| `jekyll-seo-tag` plugin | Skipped for v1 — no immediate need for richer link previews / SEO meta tags. Can be added with one line in `_config.yml` if shareability matters later. | Decision 15 (Q15 option chosen: "none") |
| `jekyll-sitemap` plugin | Skipped for v1 — three pages don't need a sitemap.xml; can be enabled later if search-engine indexing becomes a priority. | Decision 15 |
| `jekyll-feed` plugin | Skipped for v1 — no current need for RSS subscription to talks. Easy to enable later. | Decision 15 |
| Custom domain (CNAME) | Project-page hosting at `<user>.github.io/ldx3/` is sufficient for v1; custom domain only worth doing if a domain is already owned. | Decision 12 |
| GH Actions PR build workflow | Native GH Pages build already fails loudly on bad builds; a duplicate workflow adds maintenance for no benefit at this scale. | Decision 13 (Q13 option 3) |
| Richer talk front-matter fields (`tags`, `event`, `slides_url`) | No current use case; would add per-file overhead and inconsistency between files. Add only when an actual need arises. | Decision 4 |
| `jekyll-redirect-from` for old root-level `.md` URLs | The repo isn't deployed yet — no existing inbound links to preserve. | Decision 10 |
| Hand-rolled CSS / non-`tactile` theme | Tactile picked deliberately for distinctive look; revisit only if readability complaints arise. | Decisions 7, 8 |
| Mixed chronological feed on index | Talks/vendors are conceptually different; the two-section index is more scannable. | Decision 9 |

## Open Questions
_All three open questions were resolved by the user before Step 2 dispatch._
- **Q1 — Tie-breaker when multiple talks share the same date.** RESOLVED: secondary sort by `title` ascending.
- **Q2 — Commit `Gemfile.lock`?** RESOLVED: gitignore it (keep local-only).
- **Q3 — Actual GitHub username for the live-site URL.** RESOLVED: `Houms`. Live site URL is `https://Houms.github.io/ldx3/`. Use this in `_config.yml` (`url: "https://Houms.github.io"`) and in `README.md`.
