# Bio-HuB

Central hub for all **Biotechnology Department** web apps at the **University of Raparin**.
Installable PWA — works on iPhone, Android and desktop, and the hub itself opens offline.

## Files

```
index.html              the whole hub (cards, EN/KU, theme, install flow)
manifest.webmanifest    PWA manifest
sw.js                   service worker (offline cache)
icons/                  app icons (SVG + PNG + maskable + Apple touch)
.nojekyll               tells GitHub Pages to serve files as-is
```

## Put it on GitHub Pages

1. Create a repo, e.g. `bio-hub`, under the `nawzad9` account.
2. Upload every file in this folder to the **root** of the repo (keep the `icons/` folder).
3. **Settings → Pages → Source: Deploy from a branch → `main` / `/ (root)` → Save.**
4. After a minute it's live at `https://nawzad9.github.io/bio-hub/`.

HTTPS is required for a PWA — GitHub Pages gives you that automatically.
Cloudflare Pages works too: just point it at the repo, no build command, output directory `/`.

## Adding a third app later

Open `index.html`, find the `APPS = [` list near the bottom, copy one block and edit it:

```js
{
  name:   { en:"Lab Booking", ku:"حیجزکردنی تاقیگە" },
  desc:   { en:"Reserve lab time slots.", ku:"حیجزکردنی کاتی تاقیگە." },
  url:    "https://example.pages.dev/",
  tags:   { en:["Students"], ku:["خوێندکاران"] },
  colors: ["#0891b2","#06b6d4"],
  icon:   '<circle cx="12" cy="12" r="9"/>'
}
```

`icon` is the inside of an SVG (24×24, stroked) — grab any path from [lucide.dev](https://lucide.dev).

**After any edit, bump the cache version** in `sw.js` (`biohub-v1` → `biohub-v2`), otherwise
installed phones keep showing the old page.

## How installing works

- **Android / Chrome** — the blue *Install* bar appears automatically; one tap installs it.
- **iPhone / iPad** — iOS has no install button. Open the page **in Safari**, tap **Share**,
  then **Add to Home Screen**. The footer link in the app shows these steps with pictures.
- Once installed it runs full-screen with no browser bar, and opens offline.

## Offline behaviour

The hub (cards, icons, layout) is cached and always opens. The individual apps live on their
own domains, so they need internet the first time — install each one separately from inside it,
and it keeps its own offline cache.

---
Built for the Biotechnology Department, University of Raparin.
