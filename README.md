# Tobias Plank Portfolio

Personal portfolio website for Tobias Plank, built with Astro. The site contains an about page, project and blog sections, and the required legal pages.

## Tech stack

- [Astro](https://astro.build/) 7
- TypeScript
- CSS with custom properties for theming
- [Pixelarticons](https://github.com/halfmage/pixelarticons)

## Requirements

- Node.js `22.12.0` or newer
- npm, pnpm, or another Node.js package manager

## Getting started

Clone the repository, install the dependencies, and start the development server:

```sh
git clone <repository-url>
cd portfolio
npm install
npm run dev
```

The site is available at [http://localhost:4321](http://localhost:4321).

## Commands

Run these commands from the project root:

| Command | Description |
| --- | --- |
| `npm install` | Install dependencies |
| `npm run dev` | Start the development server |
| `npm run build` | Build the site for production in `dist/` |
| `npm run preview` | Preview the production build locally |
| `npm run astro -- --help` | Show Astro CLI help |

## Project structure

```text
public/                 Static assets and favicon
src/
├── components/         Reusable Astro components
├── data/                Shared site data
├── layouts/             Page layouts and document head
├── pages/               Website routes
└── styles/              Global and component styles
```

The current routes are:

- `/` — Home
- `/about` — About
- `/projects` — Projects
- `/blog` — Blog
- `/imprint` — Imprint
- `/privacy_policy` — Privacy policy

## Theme

The site uses dark mode by default. Visitors can switch between dark and light mode with the theme toggle in the navigation. The selected theme is stored in `localStorage` under the `theme` key.

## License

The source code is licensed under the [MIT License](LICENSE).

Personal content, images, branding, and portfolio materials remain © Tobias Plank and may not be reused without permission.
