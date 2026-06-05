# The Lunchbox — moablunchbox.com · Launch Notes

**Repo:** github.com/jpearly00/lunchbox  ·  **Domain (CNAME):** moablunchbox.com
**Brand:** The Lunchbox (DBA of Moab Mercantile LLC) — "Good Eats · Grab · Go · Repeat"
**Parent:** Coyote's, 805 N Main St, Moab UT 84532

## Pages
- `index.html` — Home. Hero, delivery-soon banner, how-it-works, Build-a-Box feature, menu preview.
- `menu.html` — Full menu (sandwiches, burritos, combos, sides, drinks) with `data-square-id` on every item.
- `order.html` — Pre-order flow: cart, **pickup-time selection** (6–10 AM, 15-min slots, same-day 30-min lead), pickup/delivery toggle (delivery = "Soon"), Square checkout, pay-at-pickup fallback.
- `build.html` — **Build Your Own Lunchbox**: pick entrée/side/snack/drink/dessert; live photo composite fills the box; bundle discount; hands cart to `order.html`.

## What's LIVE now
- Full rebrand to "The Lunchbox" (sign aesthetic: red #C8362B / black #1A1A1A / steel).
- Pre-order + pickup-time picker working end-to-end (order routes to SMS/email to info@ for pay-at-pickup).
- Build-Your-Own with auto-composing preview (PLACEHOLDER photos — see below).

## TODO before "fully done"
1. **Square online ordering (info@ account).** Edit `SQUARE_CONFIG` at top of `order.html`:
   - `enabled: true`
   - `applicationId` + `locationId` from Square Dashboard (info@ account) → Developer/Online.
   - Easiest path: stand up **Square Online "Order Ahead"** site, paste its URL into `onlineOrderingUrl`; the checkout button deep-links to it.
   - Item-level `data-square-id` (SQ-ITEM-001 …) must be mapped to real Square catalog IDs.
2. **Real food photos.** Replace placeholders in `/images` with plated cut-out shots, especially per-item images used by the Build-a-Box compartments (entrée/side/snack/drink/dessert).
3. **Confirm sales-tax rate** in `order.html` (`TAX_RATE`, currently 8.85% est.).
4. **GTM ID** — replace `GTM-XXXXX` once analytics container is created.
5. **Delivery** — flip the disabled toggle in `order.html` when delivery launches.

## Cross-brand context
- Marketed as a **restaurant** on TripAdvisor; Coyote's listed as a **"thing to do."** Same legal entity (Moab Mercantile LLC), separate DBAs. Sites cross-link; The Lunchbox owns food ordering, Coyote's owns retail/vibes.

## Deploy / rollback
- Hosting deploys from `main` (GitHub Pages / Cloudflare Pages with the CNAME).
- Every change is a git commit — roll back with `git revert <sha>` or `git checkout <sha> -- <file>`.
