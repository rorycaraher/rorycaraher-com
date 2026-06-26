  # PRD: Hugo Site Housekeeping

  ## Tasks

  - [x] Update the copyright year in the site config (hugo.toml / config.toml) to 2026
  - [x] Add a `robots.txt` file to the `static/` directory that allows all crawlers
  - [x] Add a `.nojekyll` file to the `static/` directory (prevents GitHub Pages from treating the site as Jekyll)

  ## Done

  All tasks are complete when all checkboxes above are checked.

---

# PRD: Site Redesign — Dark Theme, Projects & Music

## Goals

- Dark theme with the existing purple accent
- Homepage becomes a proper landing page with section previews
- New Projects page (manually curated data file)
- New Music page (describe projects, embed SoundCloud where useful)
- Navigation enabled
- Blog scaffolded but kept minimal so the site doesn't look empty while content is sparse

---

## Tasks

### 1. Dark theme

- [x] Change `data-theme="light"` to `data-theme="dark"` in `themes/rorycaraher/layouts/_default/baseof.html`
- [x] Adjust the dark background CSS variable (`--mg-color-initial` in the dark block of `mgplus.css`) — current value `#302f2f` is too warm/brown; pick something closer to `#18181b` or similar
- [x] Verify purple accent (`#9b4dca`) has acceptable contrast on the new dark background; adjust lightness slightly if needed

### 2. Navigation

- [x] Uncomment the menu block in `themes/rorycaraher/layouts/partials/header.html`
- [x] Add `[[menus.main]]` entries to `hugo.toml` for: Home, Projects, Music (blog can be added later)
- [x] Confirm nav renders and active-page highlighting works

### 3. Projects page

- [x] Create `data/projects.yaml` with fields: `name`, `description`, `url`, `tags`, `featured` (bool) — seed with a handful of real GitHub repos
- [x] Create `content/projects/_index.md`
- [x] Create `themes/rorycaraher/layouts/projects/list.html` — card grid using existing `mg-row`/`mg-col` classes, only showing `featured: true` entries
- [x] Add a "Projects" teaser section on the homepage (2–3 featured cards + "see all" link)

### 4. Music page

- [x] Create `content/music/_index.md` with intro text and per-project write-ups (can start as plain markdown prose)
- [x] Create `themes/rorycaraher/layouts/music/single.html` (or use `_default/single.html` if no custom layout needed)
- [x] Embed SoundCloud widget (iframe) for each relevant project/track inline in the markdown via a Hugo shortcode or raw HTML
- [x] Optionally create a `layouts/shortcodes/soundcloud.html` shortcode so embeds are clean in markdown

### 5. Homepage redesign

- [x] Replace the raw markdown content in `content/_index.md` with structured front matter (bio, featured project slugs) — or keep markdown but restructure into sections
- [x] Update `themes/rorycaraher/layouts/_default/home.html` to render: short bio, featured projects grid, music teaser, (blog teaser — hidden if no posts)
- [x] Keep the work history (CV-style) — move it to a collapsible or secondary section so it doesn't dominate

### 6. Footer

- [x] Check `themes/rorycaraher/layouts/partials/footer.html` — add GitHub and SoundCloud icon/text links if missing
- [x] Ensure copyright line is present and styled

### 7. Blog (last, minimal)

- [x] Confirm `themes/rorycaraher/layouts/_default/list.html` and `single.html` work for posts
- [x] Add `archetypes/posts.md` with sensible front matter defaults (title, date, draft: true)
- [x] Add a nav menu entry for Blog only once there is at least one published post
- [x] Homepage blog teaser: only render if posts exist (use Hugo `if` guard)

---

## Order of execution

1 → 2 → 3 → 4 → 5 → 6 → 7

Dark theme and nav first so every subsequent step is previewed correctly.
