# Leech — Live Design Editor

A Chrome extension that attaches to any page and turns it into an in-place design editor. Pick an element, change its colour, typography, spacing, borders or text, and see the result immediately. When you are done, export the list of changes and hand it to whoever writes the code.

**[Install from the Chrome Web Store](https://chromewebstore.google.com/detail/nolfjfjlajgjgjegjheiaambgoojefma)**

---

## Getting started

Leech is passive until you open it.

1. Open any page and click the Leech toolbar icon, or press **Alt+Shift+L** (**⌥⇧L** on a Mac).
2. Press **Select**, then click any element on the page.
3. The panel shows editors for that element. Changes apply immediately.
4. **Prompt** or **Export** at the bottom gives you the change list.

Your edits are remembered per page and survive a reload.

### To edit local HTML files

Chrome keeps file access off by default. Go to `chrome://extensions`, open Leech's **Details**, and enable **Allow access to file URLs**. Without it Leech will not run on `file://` pages at all.

---

## What it does

- **Inspector** — hover any element for its size, typography, colours, effects and layout. Only values that are actually set, never a wall of defaults.
- **Colours** — offered **by token name**, read from the page's own CSS custom properties, so an edit writes `var(--color-primary)` rather than a raw hex. If the page has no tokens, the colours actually in use are offered instead.
- **Opacity** — per colour, the way a fill works in a design tool. The token name survives into the exported value.
- **Contrast** — every text colour is checked against WCAG AA as you work, adjusted for large text. Lower the opacity and the check follows the blended result, because that is what the eye sees.
- **Typography, spacing, borders, shadows** — step through the project's own scale, or type an exact number.
- **Text** — including elements that contain other elements.
- **Drag** — reorder, align or space children inside one component. They cannot leave it.
- **Dimensions** — preview at desktop, tablet and mobile widths. The window itself resizes, so the page's own breakpoints switch.
- **Undo and redo**, a change log, and a hide toggle for before/after.
- **Hebrew and English** interface.

---

## Privacy

Nothing leaves your device. There are no accounts, no analytics, and no network requests of any kind. Your edits are stored locally in the browser.

Full policy: **[leech-privacy](https://github.com/cohenben564-ai/leech-privacy)**

---

## Known limits

- **Framework re-renders overwrite edits.** On a React or Vue app a re-render replaces the DOM Leech edited. Static HTML and server-rendered pages are unaffected.
- **It does not reach into iframes.** Content inside an embedded frame cannot be selected.
- **`chrome://` pages are closed to every extension**, including this one.
- **After a reload, elements are found again by CSS path.** If the page structure shifted, some edits cannot be placed — the panel reports exactly how many rather than failing silently.
- **Text burned into an image** is not reachable by CSS and cannot be edited.

---

## Reporting a problem

Open an issue: **[Issues](https://github.com/cohenben564-ai/leech-support/issues)**

What helps most:

1. The page it happened on, or a small HTML file that reproduces it.
2. What you expected, and what happened instead.
3. A screenshot of the Leech panel, including the breadcrumb at the top.
4. Your Chrome version, from `chrome://version`.
