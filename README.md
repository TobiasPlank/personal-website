# Tobias Plank Portfolio

Personal portfolio website for Tobias Plank, built with Astro. The site combines a modern sans-serif interface with a pixel-inspired terminal hero animation and Pixelarticons.

## Technology

- [Astro 7](https://astro.build/)
- TypeScript in Astro frontmatter
- CSS custom properties for layout, colors, and themes
- [Pixelarticons](https://github.com/halfmage/pixelarticons)
- Departure Mono for pixel-style text and icons
- Plus Jakarta Sans for the primary interface typography

## Requirements

- Node.js `22.12.0` or newer
- npm, pnpm, or another Node.js package manager

## Getting started

```sh
git clone <repository-url>
cd portfolio
npm install
npm run dev
```

The development server is available at [http://localhost:4321](http://localhost:4321).

## Commands

Run commands from the project root:

| Command                   | Description                                            |
|---------------------------|--------------------------------------------------------|
| `npm install`             | Install dependencies.                                  |
| `npm run dev`             | Start the Astro development server in background mode. |
| `npm run build`           | Build the production site in `dist/`.                  |
| `npm run preview`         | Preview the production build locally.                  |
| `npm run astro -- --help` | Display Astro CLI help.                                |

## Project structure

```text
public/                 Static assets and local fonts
src/
├── components/         Reusable Astro components
├── data/               Shared site data
├── layouts/            Page shell, navigation, footer, and document head
├── pages/              Website routes
└── styles/             Global, layout, and component styles
```

## Routes

- `/` — Home
- `/about` — About
- `/projects` — Projects
- `/blog` — Blog
- `/imprint` — Imprint
- `/privacy_policy` — Privacy policy

## Theme behavior

Theme initialization happens in the document head to avoid a flash of the wrong theme:

1. A manually selected theme from `localStorage` takes priority.
2. On a first visit, the browser's `prefers-color-scheme` preference is used.
3. Dark mode is used as the fallback.

The `ToggleTheme` component owns the button and persistence logic. The Hero component observes changes to `data-theme` and updates the active label color and icon automatically.

## Navigation controls

The navigation contains two reusable UI components:

- `src/components/ui/ToggleTheme.astro` switches between light and dark mode and stores the selected theme in `localStorage`.
- `src/components/ui/ContactMe.astro` renders the hover- and focus-based contact menu.

The Contact Me links are configured in the `contactLinks` array inside the component. Each entry contains:

```yaml
{
    label: "GitHub",
    href: "https://github.com/tobiasplank",
    icon: githubIcon,
    darkColor: "rgb(251 251 248)",
    lightColor: "rgb(36 36 36)",
    external: true,
}
```

`darkColor` and `lightColor` define the icon color for each theme. Set `external` to `true` for web links that should open in a new tab. External links receive `target="_blank"` and `rel="noopener noreferrer"`; email links should use `external: false` and a `mailto:` URL.

The component styles are kept separately in `src/styles/ui/contact_me.css` and `src/styles/ui/toggle_theme.css`. The Contact Me menu opens when the component is hovered or focused, while individual links use the CSS `:has()` selector to move the inverted visual treatment from the trigger to the active menu item.

## Hero animation

Animated labels are configured in `src/components/Hero.astro`. Each sequence contains its text, icon, accessible label, and separate light/dark colors:

```yaml
{
    text: "automation ",
    icon: "file-big-code",
    label: "code",
    color: {
        dark: "rgb(80 220 150)",
        light: "rgb(20 130 80)",
    },
}
```

The animation uses `IntersectionObserver` and an `AbortController`. It runs only while the Hero is visible and cancels its timers when the component leaves the viewport. Users who prefer reduced motion see the first sequence without animation.

## License

The source code is licensed under the [MIT License](LICENSE).

Personal content, images, branding, and portfolio materials remain © Tobias Plank and may not be reused without permission.
