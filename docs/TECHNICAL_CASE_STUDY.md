# Technical Case Study

## Summary

Kalendra's website is a static single-page React application whose job is to explain an unreleased AI scheduling assistant and collect early-access sign-ups. Its distinguishing engineering is the animation: six chat bubbles, a branching integrations diagram, a glass-lens ticker, a scrolling chip wall and a looping logo, all produced with code rather than video.

Live: [getkalendra.com](https://getkalendra.com/)

## Scope

| Item | Detail |
|---|---|
| Type | Marketing and waitlist website |
| Rendering | Client-side React 18, built by Vite 5 into static files |
| Routing | None; one page with in-page anchors, plus `#privacy` and `#terms` dialogs |
| Backend | None owned by the project; form delivery uses the EmailJS browser SDK |
| Styling | Hand-written CSS, one stylesheet per section |
| Hosting | Netlify (verified from response headers on the live site) |
| Size | 26 JSX files, 26 CSS files, roughly 3,500 lines |
| Production bundle | About 334 kB JS (114 kB gzipped), 33 kB CSS; the largest assets are PNG backgrounds of 0.5 to 1.2 MB |

## Verification performed

- The live site returns 200 and loads without console errors.
- The live bundle contains GSAP and the EmailJS SDK; the source used for this write-up matches it.
- A clean install and production build of the source succeeds.
- Each section was captured on desktop at 1440 by 900 and on a 412 by 860 mobile viewport, and the mobile document width equals the viewport width.

## Design of the page

The page is a vertical stack of full-viewport sections. Each section is a folder holding its component, CSS and local assets, with sub-components for animations (`components/` or `animations/`). State is local to each section; the root component only tracks which legal dialog is open.

## Notable implementation decisions

1. **Code-driven animation.** Choosing SVG, CSS and small render loops avoids video and animation-runtime weight, keeps text crisp at any pixel density and lets copy change without re-exporting art.
2. **Parametric diagram.** The capabilities connector lines are generated from numeric inputs, so sizes on desktop and mobile come from the same component.
3. **Separate mobile composition for the conversation.** The six bubbles are positioned absolutely in percentages. Rather than make one layout stretch, the section holds two bubble configurations, a scattered desktop layout and a stacked alternating mobile layout, and picks one from the window width.
4. **Hash-driven dialogs.** Legal notices are state derived from `location.hash` instead of separate routes, which keeps the site a single static page while still giving shareable links.
5. **Environment-driven form config.** The form validates that its three identifiers exist before sending and falls back to a plain message if not.

## Trade-offs

- Everything is client-rendered; title, description, Open Graph and Twitter tags are present in the HTML shell.
- Large PNG backgrounds are shipped as-is, favouring visual fidelity over first-load weight.
