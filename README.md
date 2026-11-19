# Astro HTML + CSS Starter

A fast, no-framework [Astro](https://astro.build) starter styled with plain,
class-based CSS — **no Tailwind, no UI framework**. It's the ideal canvas for
editing styles visually inside Ship Studio.

## Why this starter

Most starters reach for a utility-CSS framework. This one keeps styling in a
single, readable stylesheet where **every element has one semantic class and
each class is defined by exactly one CSS rule**. That makes the markup clean and
makes styles easy to edit — by hand or by clicking elements in Ship Studio's
visual editor, which writes real CSS (`padding: 24px`, any property, any value)
straight into the stylesheet.

## Structure

This is a parent project holding one home page per client project. There is no
root page — `/` returns a 404 — so a visitor who trims a project link back to
`/` doesn't find the others. Each project is served at its name plus a random code
(`/<project>-<code>/`), so the URLs can't be guessed either. The full index
lives at `/projects-10oo2qcgx/`, which nothing links to. Every page is
`noindex` and `robots.txt` disallows crawling.

Everything a project needs lives in its own folder under `src/pages/`. Astro
skips folders that start with `_`, so `_components/` never becomes a URL.

```
src/
  pages/
    projects-10oo2qcgx/index.astro           Unlinked index of every project
    <project>-<code>/
      index.astro                            The project's page, served at /<project>-<code>/
      _components/                           Its Layout, Header, Footer and styles.css
  hub/                                       Layout + styles for the project index
public/                                      Static assets (favicon, robots.txt)
```

Current projects: **Northwind** (`/northwind-aod9457/`).

### Adding a project

1. Pick a random code (three letters and four digits, e.g. `kwk3492`).
2. Copy `src/pages/northwind-aod9457/` to `src/pages/<project>-<code>/` and
   rework it. Keep `<meta name="robots" content="noindex, nofollow" />` in the
   layout's `<head>`, and point the header and footer links at the new path.
3. Add the project to the `clients` list in
   `src/pages/projects-10oo2qcgx/index.astro`.

Each project imports only its own stylesheet, so styles never leak between
projects.

## The styling convention

Keep these and the visual editor stays reliable:

- Style through **classes**, not inline `style=""`.
- Give each editable element **one semantic class** (`.hero-title`, `.feature-card`).
- Define each class with **one rule** in that client's `styles.css`.
- Put responsive overrides in the **`@media` block** at the bottom of the file.

## Commands

| Command           | Action                                       |
| ----------------- | -------------------------------------------- |
| `npm install`     | Install dependencies                         |
| `npm run dev`     | Start the dev server at `localhost:4321`     |
| `npm run build`   | Build the production site to `./dist/`       |
| `npm run preview` | Preview the build locally                    |

Built for [Ship Studio](https://github.com/ship-studio/ship-studio).
