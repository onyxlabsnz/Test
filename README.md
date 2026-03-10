# Onyx Labs (Astro)

Rebuild of the Onyx Labs marketing site in [Astro](https://astro.build/) with **no Bootstrap**. Navbar and footer are reusable components; layout uses custom CSS (flex/grid utilities and component styles).

## Setup

```bash
npm install
npm run dev
```

Open [http://localhost:4321](http://localhost:4321).

## Build

```bash
npm run build
npm run preview
```

## Structure

- **`src/layouts/BaseLayout.astro`** – Root layout (meta, Navbar, slot, Footer, Lenis).
- **`src/components/Navbar.astro`** – Site header with Services dropdown (hover), About, Contact, CTA. Mobile menu toggles via `.nav-onyx.open`.
- **`src/components/Footer.astro`** – Footer columns, social links, live clock, copyright.
- **`src/styles/global.css`** – All styles (variables, layout utilities, navbar, hero, cards, forms, legal, footer). No Bootstrap.
- **`src/pages/*.astro`** – One file per route: index, about, contact, ai-governance, ai-training, ai-consulting, ai-development, web-development, web-hosting, privacy, terms.

## Features

- **Smooth scroll:** Lenis is initialized in the layout (see `src/scripts/lenis.ts`).
- **Responsive:** Custom grid and flex utilities; navbar collapses to a hamburger menu on small screens.
- **Dropdown:** Services menu opens on hover (CSS); no Bootstrap JS.
