# Busayomi Seyifunmi — Marketing Copywriter Portfolio

A premium, editorial, conversion-focused personal portfolio for Busayomi Seyifunmi,
Marketing Copywriter (Lagos, Nigeria). Built with plain HTML5, CSS3 and Vanilla
JavaScript — no frameworks, no build step, easy to hand-edit.

## 1. Project Overview

Five pages:

| Page | Purpose |
|---|---|
| `index.html` | Homepage — hero, proof strip, services, featured work |
| `about.html` | Bio, experience timeline, process, testimonials |
| `work.html` | Full case studies with category filters + modal viewer |
| `contact.html` | Contact methods + 2-step client intake brief (Formspree) |
| `success.html` | Post-submission confirmation (not in main nav) |

## 2. Technology Used

- HTML5 (semantic)
- CSS3 (custom properties / design tokens in `css/style.css`)
- Vanilla JavaScript (`js/main.js`, `js/form.js`)
- Google Fonts: Fraunces (display) + Inter (body) — the only external dependency
- No React, Tailwind, Bootstrap, jQuery or icon libraries

## 3. Folder Structure

```
/
├── index.html
├── about.html
├── work.html
├── contact.html
├── success.html
├── README.md
├── css/
│   ├── style.css        (design system + components)
│   └── responsive.css   (breakpoints: 1440/1200/1024/768/480/375)
├── js/
│   ├── main.js          (nav, reveals, filters, modal)
│   └── form.js          (brief steps + Formspree submit)
└── assets/
    ├── images/
    │   ├── profile/busayomi-profile.jpg
    │   ├── projects/esosa-yard-sale.jpg
    │   ├── projects/residar-homes.jpg
    │   ├── projects/rose-garden-realty.jpg
    │   ├── projects/landculture.jpg
    │   └── testimonials/
    ├── icons/social/
    │   ├── linkedin.svg
    │   ├── tiktok.svg
    │   └── whatsapp.svg
    └── documents/
        └── Busayomi-Seyifunmi-CV.pdf
```

## 4. How to Run Locally

No build step. Either:

- **Option A:** double-click `index.html` (everything works except the form fetch on some browsers — use Option B for testing the form).
- **Option B (recommended):** run a tiny local server from the project root:
  ```bash
  python3 -m http.server 8000
  ```
  then open `http://localhost:8000`.

## 5. Deploy to Vercel

1. Push this folder to a GitHub repository.
2. At [vercel.com](https://vercel.com) choose **Add New → Project** and import the repo.
3. Framework preset: **Other**. No build command, output directory = root.
4. Deploy. Update the canonical/OG URLs in each HTML `<head>` to your live domain.

## 6. Deploy to Netlify

1. Push to GitHub, then at [netlify.com](https://netlify.com): **Add new site → Import an existing project**.
2. Build settings: leave blank (no build). Publish directory: `/` (root).
   - Or drag-and-drop the whole folder onto Netlify's dashboard.

## 7. Replace the Profile Image

Replace the file (keep the name):
`assets/images/profile/busayomi-profile.jpg`
Recommended: ~900×1100px, portrait, JPG/PNG under 300 KB. The HTML needs no edits.

## 8. Replace Project Images

Replace any of:
`assets/images/projects/esosa-yard-sale.jpg`
`assets/images/projects/residar-homes.jpg`
`assets/images/projects/rose-garden-realty.jpg`
`assets/images/projects/landculture.jpg`
Recommended: 1200×800px, JPG under 300 KB. Filenames are referenced in
`index.html`, `work.html`, and the `CASE_STUDIES` object in `js/main.js`.

## 9. Replace Testimonials

In `about.html`, search for `PLACEHOLDER TESTIMONIALS`. Replace the five
`.testimonial-card` blocks with verified testimonials (quote + author/company).
Delete the HTML comment once real testimonials are in.

## 10. Replace the CV

Drop the final PDF at:
`assets/documents/Busayomi-Seyifunmi-CV.pdf`
Keep the exact filename — every "Download My CV" button already points to it
with the correct `download` attribute.

## 11. Edit Social Links

Search the HTML for `linkedin.com/in/busayomi`, `tiktok.com/@busayoseyifunmi5`,
and `wa.me/2348133840972`. They appear in the footer of every page and in the
contact cards on `contact.html`. Icons are the shared files in
`assets/icons/social/` — change them once, everywhere updates.

## 12. Change Colors

All colors are CSS variables at the top of `css/style.css`:

```css
:root {
  --color-primary: #043382;   /* navy — dominant brand color */
  --color-accent: #37B5FF;    /* blue — highlights, CTAs, states */
  --color-background: #F2F6FF;/* soft section background */
  ...
}
```

Change a value once; the whole site follows.

## 13. Change Typography

Fonts are defined as variables in `css/style.css`:

```css
--font-display: "Fraunces", Georgia, serif;
--font-body: "Inter", -apple-system, sans-serif;
```

Swap the Google Fonts `<link>` in each HTML `<head>` and update these two
variables.

## 14. Update Projects

1. **Homepage:** edit the `.case-card` blocks in `index.html`.
2. **Work page:** edit/add `.case-card` articles in `work.html`. Set
   `data-categories` using: `real-estate`, `marketing`, `sales-copy`,
   `campaigns`, `fashion-lifestyle` (space-separated for multiple).
3. **Modal content:** add/update the matching entry in the `CASE_STUDIES`
   object in `js/main.js` (key must match the button's `data-case-open`).
4. An annotated "ADD FUTURE CASE STUDIES HERE" comment sits inside
   `work.html` marking exactly where to paste new cards.

## 15. Update Services

Edit the four `.service-card` blocks in `index.html` (section `#services`).
Grid auto-adjusts from 2 columns to 1 on mobile.

## 16. Update Contact Details

Search-and-replace across all HTML files:
- Email: `busayoseyifunmi2021@gmail.com`
- Phone/WhatsApp: `+234 813 384 0972` (and `wa.me/2348133840972`)

## 17. Configure Formspree

1. Create a free form at [formspree.io](https://formspree.io) (email
   notifications enabled by default).
2. Copy the endpoint, e.g. `https://formspree.io/f/abcdwxyz`.
3. Paste it in place of the placeholder (see §18).
4. Optionally add a "Thank you" redirect setting in Formspree — the site
   already handles the redirect itself in JavaScript, so this is optional.

## 18. Formspree Placeholder Location

Exactly one place matters — the constant at the top of **`js/form.js`**:

```js
var FORMSPREE_ENDPOINT = "YOUR_FORMSPREE_ENDPOINT_HERE";
```

A developer comment plus the same string in the `<form action="...">` in
`contact.html` mark it too. Until replaced, the form shows a clear on-page
error instead of failing silently.

## 19. How the Success Redirect Works

`js/form.js` intercepts the submit, validates step 2, then `fetch()`-posts the
FormData to Formspree with `Accept: application/json`. On a successful response
it sets `window.location.href = "success.html"`. Errors and network failures
show inline status messages without leaving the page. Loading state disables
buttons and shows a spinner on the submit button.

## 20. Add Future Case Studies

1. Add project image to `assets/images/projects/`.
2. Copy a `.case-card` article in `work.html`, set its `data-categories`
   (see §14) and its button's `data-case-open="newkey"`.
3. Add a `newkey` entry to `CASE_STUDIES` in `js/main.js` with
   title, image, location, role, category, challenge, approach, outcome.
4. If it belongs on the homepage, copy a card into `index.html` too.
