# AGENTS.md

## Stack

Single-package Astro site (no frameworks) with Tailwind CSS v4. No test, lint, or typecheck scripts. `npm run build` is the closest verification.

## Development

When starting the dev server, use background mode:

```
astro dev --background
```

Manage the background server with `astro dev stop`, `astro dev status`, and `astro dev logs`.

## Conventions

- All UI copy is in Spanish (e.g. "Inicio", "Contacto", "Fanarts").
- Shared chrome (nav, sidebar, footer, ad script) lives in `src/layouts/BaseLayout.astro`; every page imports it and passes a `title` prop.
- Site-wide styling lives in `src/styles/global.css`: Tailwind v4 `@theme` tokens (`bg`, `panel`, `ink`, `ink-soft`, `accent`, ...) plus reusable classes (`.card`, `.btn-primary`, `.btn-download`, `.section-title`). Add reusable styles there, not inline per page.

## Gotchas

- Static media is served from `public/` (referenced as `/manzft/...`, `/wonder-maker/...`). The repo-root `assets/` dir is a tracked duplicate of the same files and is NOT served by Astro — put new media in `public/`.
- `dist/` is committed to git (predates `.gitignore`); rebuilds dirty the tree. Don't stage it for unrelated work.
- `BaseLayout.astro` intentionally injects an ad/popunder script on first click — preserve it unless explicitly asked to remove.

## Documentation

Full documentation: https://docs.astro.build

Consult these guides before working on related tasks:

- [Adding pages, dynamic routes, or middleware](https://docs.astro.build/en/guides/routing/)
- [Working with Astro components](https://docs.astro.build/en/basics/astro-components/)
- [Adding styles or using Tailwind](https://docs.astro.build/en/guides/styling/)
