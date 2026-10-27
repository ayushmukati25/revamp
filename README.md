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

This is a parent project holding one home page per client. The root page is
reserved as an index of clients; each client gets its own folder of layout,
components and styles, plus its own route folder.

```
src/
  pages/index.astro             Reserved root page that lists every client site
  hub/                          Layout + styles for the root page only
  pages/<client>/index.astro    A client's home page, served at /<client>/
  clients/<client>/             That client's Layout, Header, Footer, styles.css
public/                         Static assets (favicon)
```

Current clients: **Northwind** (`/northwind/`).

### Adding a client

1. Create `src/clients/<client>/` with its `Layout.astro`, components and `styles.css`.
2. Create `src/pages/<client>/index.astro` using that layout.
3. Add the client to the `clients` list in `src/pages/index.astro`.

Each client imports only its own stylesheet, so styles never leak between clients.

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
