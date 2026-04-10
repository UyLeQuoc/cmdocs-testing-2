# My Documentation

Documentation site powered by [cmdocs](https://github.com/CommandOSSLabs/cmdocs-starter).

## Getting started

Start the development server:

```bash
npx cmdocs dev
```

Open [http://localhost:3000](http://localhost:3000) to view your docs. The dev server hot-reloads on every save.

## Project structure

```
.
├── docs.json                # Site config — theme, navigation, navbar, SEO
├── index.mdx                # Home page
├── quickstart.mdx           # Quickstart guide
├── guides/
│   ├── writing-content.mdx  # MDX authoring guide
│   ├── components.mdx       # UI component reference
│   └── deploy.mdx           # Deployment guide
└── public/
    ├── favicon.svg
    └── logo/
        ├── light-logo-only.svg  # Navbar icon (light mode, ~24×24)
        ├── dark-logo-only.svg   # Navbar icon (dark mode, ~24×24)
        ├── light.svg            # Wide brand logo (light mode, for logo-only display)
        └── dark.svg             # Wide brand logo (dark mode, for logo-only display)
```

## Key files

- **`docs.json`** — Central configuration: site name, theme colors, navigation, navbar, footer, and SEO.
- **MDX files** — Documentation pages written in [MDX](https://mdxjs.com/) (Markdown + JSX components). All built-in components are auto-imported.
- **`public/`** — Static assets served at the root URL. Drop images, logos, and favicons here and reference them with absolute paths (e.g. `/logo/light.svg`).

## Common tasks

### Add a new page

1. Create a `.mdx` file with frontmatter:

   ```mdx
   ---
   title: My New Page
   description: A short description.
   ---

   # My New Page

   Content goes here.
   ```

2. Add the page slug (file path without `.mdx`) to `docs.json` under the appropriate group:

   ```json
   {
     "group": "Guides",
     "pages": [
       "guides/writing-content",
       "guides/components",
       "guides/deploy",
       "guides/my-new-page"
     ]
   }
   ```

### Customize the theme

Edit the `theme` section in `docs.json`. cmdocs ships with 11 presets — pick one and override the brand color:

```json
{
  "theme": {
    "preset": "neutral",
    "colors": { "primary": "#2563EB" },
    "darkMode": true
  }
}
```

Available presets: `neutral`, `black`, `vitepress`, `dusk`, `catppuccin`, `ocean`, `purple`, `solar`, `emerald`, `ruby`, `aspen`.

### Configure the navbar logo

The `navbar.logo` field supports three modes:

```jsonc
// 1. Brand name only
{ "navbar": { "title": "My Docs" } }

// 2. Square icon + brand name
{ "navbar": { "title": "My Docs", "logo": "/logo/icon.svg" } }

// 3. Logo with text baked in (hides the title)
{
  "navbar": {
    "logo": {
      "light": "/logo/light.svg",
      "dark": "/logo/dark.svg",
      "display": "logo-only",
      "width": 140,
      "height": 36
    }
  }
}
```

## Build for production

```bash
npx cmdocs build
```

This produces a fully static site in `dist/`. Upload it to any static host, or connect your repo to the [cmdocs dashboard](https://cmdocs.sh) to deploy on every push.

## Learn more

- [cmdocs Documentation](https://docs.cmdocs.sh)
- [GitHub Repository](https://github.com/CommandOSSLabs/cmdocs-starter)
