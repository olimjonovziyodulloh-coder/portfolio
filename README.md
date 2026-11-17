# Portfolio — Olimjonov Ziyodulloh

Personal portfolio for the Web Programming course, published with GitHub Pages.

**Live:** https://olimjonovziyodulloh-coder.github.io/portfolio/

## Structure

- `index.html` — semantic one-page portfolio (About, Toolkit, Projects, Learning, Contact)
- `style.css` — theme tokens, responsive layout, light/dark themes, React island styles
- `app.js` — React 18 components for the interactive parts of the page
- `assets/profile.jpg` — portrait (4:5). Replace this file to update the photo.
- `assets/space-hero.jpg` — nebula hero background (NASA, public domain)

## React on the page

The site stays a static HTML page — React mounts into two islands, so there is
still no build step and GitHub Pages serves the same files.

| Island | Component | What it does |
| --- | --- | --- |
| `#projects-root` | `ProjectsApp` | Searchable, filterable project grid with a detail dialog |
| `#theme-toggle-root` | `ThemeToggle` | Light/dark switch, saved in `localStorage` |

Hooks and React features used:

| Feature | Where |
| --- | --- |
| `useState` | search text, active technology, selected project, theme |
| `useMemo` | technology list and the filtered + searched project list |
| `useEffect` | saves the active filter, applies the theme, dialog keyboard handling |
| `useRef` | focuses the dialog close button and returns focus to the Details button |
| `useCallback` | stable close handler for the dialog |
| `ReactDOM.createPortal` | renders the dialog into `document.body` |
| Lists + keys | project cards and technology tags |
| Conditional rendering | empty state, dialog, detail links |

The project data lives in a single array in `app.js`, so adding a project is one
more object — no HTML to copy.

## Notes

- No build step; React 18 (UMD) and ReactDOM load from jsDelivr with `defer`.
- Theme preference is stored in `localStorage`; the toggle is keyboard accessible.
- The dialog closes on Escape, on backdrop click and on the close button, and restores focus to the button that opened it.
- Scroll reveals fall back to visible content when `prefers-reduced-motion` is set.
- Without JavaScript the project grid shows a `<noscript>` list of direct links.
