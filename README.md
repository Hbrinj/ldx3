# ldx3

A small Jekyll site that turns conference talk notes and vendor-booth notes from LDX3 into readable pages. New entries are added by dropping a single markdown file with YAML front matter into the relevant collection folder; the index page and per-page layouts pick it up automatically on the next build.

**Live site:** _(to be configured once a host is chosen)_

## How to add a new talk

1. Create `_talks/<slug>.md` (slug becomes part of the URL: `/talks/<slug>/`).
2. Add this YAML front matter at the top of the file, then your notes below:

   ```yaml
   ---
   title: "<Talk title>"
   date: 2026-06-02          # YYYY-MM-DD; controls newest-first ordering on the index
   speaker: "<Name (Company)>"
   summary: "<One-line blurb shown on the index page and used as the HTML meta description>"
   ---
   ```

3. Write the body as Markdown. Do NOT repeat the title as an `# H1`, do NOT add a `## Speakers` section, and do NOT add a blockquote datestamp — the layout renders the title, date, and speaker from front matter. Start the body with content sections like `## Key Takeaways`, `## Notes`, `## Action Items`.
4. To cross-link to another talk or a vendor entry, use Jekyll's `{% link %}` tag. It resolves to the target's URL at build time and breaks the build if the target is renamed:

   ```markdown
   See [Harness vendor notes]({% link _vendors/harness.md %}).
   ```

   `{% link %}` validates the path at build time — renaming or deleting the target file fails the build loudly instead of leaving a silent 404.

## How to add a new vendor

1. Create `_vendors/<slug>.md` (slug becomes part of the URL: `/vendors/<slug>/`).
2. Add this YAML front matter at the top of the file, then your notes below:

   ```yaml
   ---
   title: "<Vendor name>"
   homepage: "https://www.example.com"   # external link shown on the index and page
   summary: "<One-line description of what they do>"
   seen_at: "LDX3 2026-06-02"            # event / when you encountered them
   ---
   ```

   > Note: the external URL field is named `homepage`, not `url`, to avoid colliding with Jekyll's built-in `page.url` (the document's own permalink).

3. Write the body as Markdown — module breakdown, follow-up questions, anything you want on the vendor's detail page.

## How to add a new reflection

Reflections are first-person syntheses (your own thinking, not a write-up of someone else's talk), so there is no `speaker` field.

1. Create `_reflections/<slug>.md` (slug becomes part of the URL: `/reflections/<slug>/`).
2. Add this YAML front matter at the top of the file, then your reflection below:

   ```yaml
   ---
   title: "<Reflection title>"
   date: 2026-06-02          # YYYY-MM-DD; controls newest-first ordering on the index
   summary: "<One-line blurb shown on the index page>"
   ---
   ```

3. Write the body as Markdown. As with talks, do NOT repeat the title as an `# H1` and do NOT add a blockquote datestamp — the layout renders the title, date, and summary from front matter.

## Local preview

```bash
bundle install                 # once
bundle exec jekyll serve       # http://localhost:4000/
```
