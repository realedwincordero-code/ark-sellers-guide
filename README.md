# ARK Sellers Guide — deployment package

A self-contained, page-turning flipbook of the ARK Real Estate Sellers Guide,
presented by Edwin Cordero. Sixteen pages, desktop page-flip and mobile swipe,
monochrome per ARK brand.

## What is in here

| Path | Purpose |
|---|---|
| `index.html` | The flipbook. 10 KB — all logic, no external libraries. |
| `pages/page-01…16.jpg` | The sixteen page spreads, 2.5 MB total. |
| `favicon-32.png`, `apple-touch-icon.png`, `icon-512.png` | ARK mark on brand black. |
| `.nojekyll` | Tells GitHub Pages to serve the files as-is. |
| `vercel.json` | Vercel-only config; harmless and ignored by GitHub Pages. |

Every path in `index.html` is relative, so the guide works at a domain root or in
a subfolder without modification. No build step, no dependencies.

The original single-file version had all sixteen pages embedded as base64 —
3.3 MB before a visitor saw anything. This build loads the cover first and the
rest as they are reached. Same design, materially faster on mobile.

---

## Option A — GitHub Pages (free, no terminal)

1. Go to **github.com/new**. Name the repository `ark-sellers-guide`, set it to
   **Public**, and do not add a README. Create it.
2. On the empty repository page, click **uploading an existing file**.
3. Drag in everything from this folder — `index.html`, the `pages` folder, the
   three icons, and `.nojekyll`. Commit.
4. Go to **Settings → Pages**. Under *Source*, choose **Deploy from a branch**,
   branch `main`, folder `/ (root)`. Save.
5. Wait about a minute. The guide is live at:

       https://realedwincordero-code.github.io/ark-sellers-guide/

If `.nojekyll` does not appear when you drag the folder, Finder is hiding
dotfiles — press `Cmd + Shift + .` to reveal it.

### Putting it on your own domain

1. In the repository, **Settings → Pages → Custom domain**, enter
   `guide.edwincordero.com` and save.
2. At your DNS provider, add a **CNAME** record:

       Host:  guide
       Value: realedwincordero-code.github.io

3. Return to Settings → Pages and tick **Enforce HTTPS** once the certificate is
   issued, usually within the hour.

GitHub writes a `CNAME` file into the repository for you — do not create one by
hand, as a wrong value takes the site offline.

---

## Option B — Vercel

Drag this folder onto **vercel.com/new**, or run `vercel --prod`. Then add the
subdomain under Project → Settings → Domains and create the CNAME record it
gives you.

Either host is fine. GitHub Pages is free and permanent; Vercel is the stack you
already run the FSBO dashboard on. Both serve the identical files.

---

## Why a subdomain rather than an iframe

Luxury Presence does not place iframes self-serve — their support team does it on
request, and framed content is not indexed by search engines. A subdomain puts
the guide on your own domain, under your control, fully indexable, and linkable
from any Luxury Presence page, email, or SMS without a support ticket.

If an in-page embed is still wanted, `LuxuryPresence-Support-Request.md` holds a
request ready to send.
