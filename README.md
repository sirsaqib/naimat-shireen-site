# Bakery Website Template — Naimat-e-Shireen style

A single-file, mobile-first static website for a Pakistani sweets & bakery business.
Premium indigo/gold theme, Playfair Display + Poppins typography, scroll-reveal
animations, Urdu product names (Noto Nastaliq Urdu), slide-in nav drawer,
sticky category band, and per-product WhatsApp order buttons.

**Menu layout:** products are grouped into stacked category sections
(Hafiz Sweets / Rehmat-e-Shereen style) — one section per category with an
English + Urdu header and gold rule, all on one scrolling page. The sticky
pills scroll to each section (active pill highlights on scroll); the search
box switches to a flat "Search results (N)" grid.

**Files**

| File | Purpose |
|---|---|
| `index.html` | The whole website — inline CSS + JS, no build step |
| `products-template.csv` | Sample product sheet (5 rows) — copy this structure for your own data |

## Quick deploy (Vercel, free)

1. Go to [vercel.com](https://vercel.com) and sign in (GitHub/Google).
2. Click **Add New → Project →** upload: drag the `bakery-template` folder
   (or just `index.html`) into the deploy area.
3. Deploy — you get a live `https://your-site.vercel.app` link in ~30 seconds.
4. (Optional) Add a custom domain in Project → Settings → Domains.

No build command, no environment variables needed.

## Per-client setup (2 minutes)

Open `index.html` and edit the `CONFIG` object at the top of the `<script>`:

```js
const CONFIG = {
  businessName: "Naimat-e-Shireen Sweets & Bakers",
  phone: "+92 320 5773262",
  whatsappNumber: "923205773262",  // country code + number, no + or spaces
  address: "Main Commercial Area, Landhi Town Malir, District Korangi, Karachi",
  hours: "08:00 – 00:00 daily",
  sheetCsvUrl: ""
};
```

## Connect a Google Sheet as the product database

This is how the shop owner adds/edits products without touching code
(as easy as a WhatsApp product list):

1. Create a Google Sheet with **exactly** these header names in row 1:
   `name, urdu_name, category, price, unit, description, image_url, badge`
   - `category` must be one of: `mithai`, `savories`, `dairy`, `cakes`, `beverages`, `hampers`
   - Leave `image_url` blank to keep the built-in placeholder photo.
   - `badge` is optional (e.g. `Bestseller`, `Fresh Daily`).
2. In Sheets: **File → Share → Publish to web** → choose the sheet tab,
   format **CSV** → **Publish** → copy the link.
   It looks like: `https://docs.google.com/spreadsheets/d/…/pub?output=csv`
3. Paste that link as `sheetCsvUrl` in `CONFIG` and redeploy.
4. The site now loads products from the sheet on every visit. If the sheet
   ever fails to load, the page **automatically falls back** to the built-in
   product list — it never shows a blank/broken page.

## Placeholders the client must confirm

- `<!-- VERIFY: confirm founding year with client -->` — "Since 1990" is used;
  the original site said 1950 in one place. Confirm the real year.
- `[YOUR-DOMAIN]` in the FAQ — replace with the client's real website domain.
- Product photos are Unsplash placeholders — replace with real shop photos
  (via the sheet's `image_url` column or the embedded array).
- `<!-- REVIEWS: … -->` — add **real** customer reviews only. Never invent ratings.

## Notes

- Urdu names render in Noto Nastaliq Urdu (loaded from Google Fonts).
- Prices format as `Rs. 1,200`. WhatsApp buttons prefill an order message
  with the product name (English + Urdu), price and unit.
- Scroll-reveal animations respect `prefers-reduced-motion`.

## Design v2 (2026-10-07) — royal maroon retheme

Rebuilt visual layer only — no changes to products, CONFIG, the Google Sheet
CSV loader, or rendering logic (all 59 products intact, sheet fallback works
as before).

- **Palette:** deep maroon `#6d1a2d` primary (header, active pills, section
  accents), ivory `#faf5ea` page accents, soft blush `#f3e2d3` category band,
  cream `#fffdf7` pills, muted gold `#c9a227` wordmark, amber `#ffc531`
  discount badges. Deliberately NOT emerald/tan — distinct from other brands.
- **Header:** full-width maroon bar with white pill buttons (location, phone),
  gold-script brand badge overlapping the header's bottom edge, white circular
  WhatsApp + hamburger buttons (hamburger opens a slide-in drawer).
- **Hero:** rounded-3xl maroon gradient banner with subtle dot pattern, Poppins
  headline, white + outlined CTA pills, floating product image, staggered
  entrance animations.
- **Category strip:** sticky blush band with horizontally scrollable cream pills.
- **Cards:** white rounded-2xl, soft shadow, amber badges, price chips,
  green WhatsApp order buttons, hover lift.
- **Footer:** white 3-column (brand/contact, quick links, categories) + light-gray
  SEO about card with "Show More" expander + copyright bar.
- **Integrity:** no location-gate modal (products visible immediately), no fake
  reviews/ratings — the `<!-- REVIEWS -->` placeholder comment is kept for
  real reviews only.

## Design v4 (2026-10-07) — brand-premium rebuild

Full visual rebuild after studying real Pakistani mithai-brand sites (Rehmat-e-Shereen style),
with an original palette (not a copy):

- **Palette:** deep rich maroon `#7a1f2b` (header, buttons, footer, active states), gold
  `#c9a24b` (wordmark, accents, dividers, CTAs), warm ivory `#fffdf8` background with a
  faint repeating dot motif, body text `#2b2b2b`.
- **Typography:** Playfair Display (serif) for brand wordmark, section headings and product
  names; Poppins for body/UI (14–15px, small and refined); Noto Nastaliq Urdu for Urdu names.
- **Header:** sticky maroon bar — gold serif wordmark + italic tagline left; nav links +
  gold "Order on WhatsApp" pill right; hamburger → maroon slide-in drawer on mobile.
- **Hero:** image-dominant full-width auto-play slider (~62vh, min 420px), 3 slides
  (gulabjamun / laddu / jalebi) with soft dark bottom gradient, small caption overlay
  (gold micro-label, ~34px serif headline, short text, gold pill CTA), dots + slim arrows,
  5s auto-play, pause on hover, `prefers-reduced-motion` respected. Images lead, text is quiet.
- **Quick bar:** white/gold pill overlapping the hero's bottom edge — Call / WhatsApp Order / Landhi Town, Karachi.
- **Category nav:** sticky elegant pills (ivory + maroon border; active = maroon fill) + search.
- **Product cards:** image-first (4/3, full card width), compact text — 17px serif name,
  14px Urdu, 13px desc, bold price + unit, full-width maroon WhatsApp pill; amber badge on image.
- **Sections:** hero → quick bar → categories+search → product grid → Gift Hampers
  (giftbox banner + strip) → About + stats (Since 1990 / 59+ products / 8AM–12AM) →
  FAQ → Visit card → maroon footer (3 columns, social icons, SEO card, copyright).
- **Images:** all 59 products mapped to verified real photos in `images/`
  (baklava, gulabjamun, kaju, cake, laddu, jalebi, kalakand, rasmalai, samosa, lassi,
  giftbox, cookies) — zero Unsplash hotlinks. Sheet `image_url` still overrides per product.
- **Integrity kept:** no location-gate modal (products visible immediately), no fake
  reviews/ratings (placeholder comment only), real business facts, "Since 1990" flagged
  for client verification.

**Deploy note:** upload the whole `bakery-template` folder (including `images/`) —
dragging only `index.html` will break product/hero images.

## Design v4.1 (2026-10-07) — indigo retheme
- **Palette:** deep indigo `#3730a3` primary (header, active pills, section accents), deep `#2a2770` / ink `#1e1b4b`, gold `#c9a24b` accents, warm ivory `#fffdf8` background. (User request: maroon replaced with indigo.)
- All CSS variables renamed `--maroon*` → `--indigo*`; shadows and text-on-gold updated to indigo tones.

## Admin Panel (2026-10-07) — on-site editor for the shop owner
- **Open:** click the small **"Admin Panel"** link in the footer copyright bar → login modal.
- **Default password:** `admin123` (change it in the Password tab after first login). Stored in
  `localStorage` as `ns_admin_pw`. Note: this is a simple static-site gate, not server security.
- **Tabs (big buttons, English + Roman Urdu):**
  - **Products (Samaan):** searchable list; Add / Edit (Badlein) / Delete (Hatayein). Fields: name,
    Urdu name, category (existing + new), price, unit, description, badge, image (paste URL or
    upload — auto-compressed to max 1000px JPEG q70).
  - **Settings (Dukaan ki maloomat):** business name, tagline, phone, WhatsApp number, address,
    hours, announcement text, 3 hero slide captions.
  - **Sections (Hissay):** show/hide Gift Hampers, About/stats, FAQ, Visit card, Announcement bar;
    edit the 3 About stats.
  - **Password (Khufia lafz):** change admin password.
  - **Backup (Mehfooz copy):** Export/Import JSON, **Download updated website** (`index.html` with
    edits baked in — WhatsApp it to your developer for redeploy), Reset to defaults.
- **Storage keys:** `ns_products_v1` (product overrides), `ns_settings_v1` (settings overrides).
  Session flag lives in `sessionStorage` (cleared on logout; data is kept).
- **Honesty note (important):** edits made in the Admin Panel show **instantly on THIS device only**
  (they live in the browser's localStorage). For changes every customer sees, either use the
  Google Sheet (`CONFIG.sheetCsvUrl` — sheet always wins when set and loading), or use
  **Backup → Download updated website** and have the developer redeploy the file.
- **Priority at boot:** Google Sheet (if set and loads) → downloaded baked-in defaults →
  this device's Admin Panel overrides → embedded defaults.
- **Deploy note (updated):** product/hero images are now embedded in `index.html` as compressed
  data URIs, so the single file works standalone (the `images/` folder is kept as source).

## Cart & WhatsApp Checkout (2026-10-07)
- **Quantity stepper** on every product card (`- qty +`, 1–99) with live line total.
- **Add to Cart** (indigo button) → slide-in cart drawer; **WhatsApp quick-order** icon per card → instant single-product order.
- **Cart drawer** (right slide-in): thumbnails, qty steppers, line totals, remove, subtotal, green **Order on WhatsApp** checkout, Continue Shopping. Empty state included.
- **Floating cart button** (bottom-right, indigo, count badge); the WhatsApp float moved to bottom-left.
- **Persistence:** `localStorage ns_cart_v1` (`[{idx, qty}]`); product details resolved at render time so admin/Sheet price edits apply; missing products dropped.
- **Checkout message** auto-generated to `CONFIG.whatsappNumber` (or admin Settings → WhatsApp), format:
  `Assalam-o-Alaikum! *New Order* — [business] / 1. Name (unit) xqty — Rs line / *Total: Rs X* / Name: / Address:`
- Toasts: "Added to cart ✓" / "Order sent on WhatsApp!". Cart clears after checkout.
- No external dependencies; `prefers-reduced-motion` respected; mobile-first.
