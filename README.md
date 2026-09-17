# Delicake — home page

Open `index.html` in any browser. No build step, no images, no external requests: the two supplied font files are bundled in `fonts/` and loaded with `@font-face`.

## Files
- `index.html` — the whole home page (announcement bar, header, hero, Value Props, Featured Collections, about snippet, newsletter, footer)
- `styles.css` — design tokens, 12-column grid, components, responsive rules
- `fonts/` — Sniglet Regular, Cabin variable (roman + italic), as supplied

## Design system
**Grid (desktop ≥1025px):** 12 columns, outer margin 0, gutter 20px. The container is full-bleed with a 10px half-gutter inset so the outer edge reads as margin 0 while text never touches the viewport edge. Press **G** on desktop to toggle a column overlay for review.

Column assignments: hero copy 1–7, hero stats 9–12, section titles 1–4, section notes 10–12, Value Props 3 × 4 columns, collection cards 3 × 4 columns, about headline 1–6 / body 8–11, newsletter 3–10 centered.

**Type:** Sniglet is used only for the wordmark (#550000). Everything else is Cabin (#421400). Scale: display `clamp(2.875rem → 8rem)`, section titles `clamp(1.875rem → 3.5rem)`, card/prop titles `clamp(1.5rem → 2rem)`, lead `clamp(1.25rem → 1.5rem)`, body 18px desktop / 17px mobile, labels 14px uppercase with 0.16em tracking.

**Colour:** paper `#FFF5F0`, type `#421400`, logo and primary buttons `#550000`, pastel accents `#F9D2D7` pink, `#FBE9B7` butter, `#CFE6DA` mint, `#DCD4EC` lilac, `#FBDCC4` peach. No photography — the specimen strip, collection glyphs and accent rules are pure CSS geometry.

## Accessibility
- Contrast: `#421400` on paper 14.7:1, `#550000` on paper 14.1:1, white on `#550000` 15.2:1; body type on every pastel stays above 10:1 (all AAA). An automated sweep of every text node found no element below 4.5:1.
- Skip link, single `h1`, ordered `h1 → h2 → h3` structure, labelled sections, `aria-label`ed navs, decorative geometry marked `aria-hidden`.
- Visible 3px focus ring on all interactive elements; hover never relies on colour alone (underline or border changes too).
- Touch targets: buttons 56px tall, nav and footer links ≥44px; mobile primary buttons are full width at 58px.
- Mobile menu is a real `<button>` with `aria-expanded` / `aria-controls`; the newsletter input has a visible label, `autocomplete="email"` and a hint tied with `aria-describedby`.
- Text uses relative units and survives 200% zoom / 400% reflow at 320px; `prefers-reduced-motion` disables transitions.

## Responsive behaviour
- ≥1025px: full 12-column layout, 6 specimen shapes, 3-up props and collections.
- 761–1024px: edge inset 16px, hero and section heads widen, 4 specimen shapes, props and cards stay 3-up with tighter padding.
- ≤760px: single column, 20px edges, 16px gutter, 17px body, disclosure nav, full-width CTAs, 3 specimen shapes.

## Shopify note
Each `<section>` maps one-to-one to a theme section (hero, value-props, featured-collections, about-snippet, newsletter), and the repeated items inside Value Props and Featured Collections are block-shaped (label, title, body, link), so they port to `section.blocks` loops with no markup changes.
