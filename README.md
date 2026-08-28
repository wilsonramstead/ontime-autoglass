# OnTime Autoglass — demo site

Single-page demo site built by **Wilson Innovations** for OnTime Autoglass, a mobile auto glass
service in Port Charlotte, FL.

**Live:** https://wilsoninnovations.net/ontime-autoglass/

## Provenance

- **Wave:** 80 (entry index 4)
- **Built:** 2026-08-27
- **Status:** unsolicited demo — `<meta name="robots" content="noindex">` is set, with a removal
  comment for the day it goes live. No contact forms anywhere; phone and text are the only CTAs.
- **Business data source:** Google Business Profile via the Google Places API, matched on phone
  **(941) 786-8903** and address **1258 Alward St, Port Charlotte, FL 33980**. Business had no
  website at build time (`websiteUri` absent from the Places response).
- **Facts used:** business name, phone, hours (Mon–Sat 7:00 AM – 6:00 PM, Sunday closed), rating
  5.0 across 21 Google reviews, five review texts, the owner's first name (Christian / "Chris" —
  named by customers in the reviews), and the vehicles visible in their own photos. Nothing else
  is asserted: no insurance billing, no ADAS calibration, no warranty, no pricing, no founding
  year, no license numbers, no email address, no employee count.
- **Address handling:** 1258 Alward St is a residential-grid address, so the site is written
  locality-lean — "Based in Port Charlotte, we drive to you." The street address appears nowhere
  on the page, and the JSON-LD `PostalAddress` carries locality/region/postal code only.
- **Reviews:** quoted verbatim from Google, attributed first name + last initial, no dates. Omar's
  review has no surname on the profile, so it is attributed "Omar". The aggregate 5.0 / 21 card is
  deliberately **not** styled as a quote. Short pull-quotes in the hero and the three-step section
  are exact sentences lifted from those same reviews, each attributed.

## Image sources

Six of the business's own **Google Business Profile photos**, pulled through the Places API
photo-media endpoint, re-encoded with PIL (progressive JPEG, each ≤ 350 KB) and self-hosted in
`img/`. **No stock photography is used on this site** — zero Unsplash or other third-party images,
so there is **zero cross-site image overlap** with the rest of the portfolio.

Attribution split on the GBP photo set: 3 uploaded by the business, 3 by customers (Brian, Omar)
on their own reviews. A seventh photo — a snapshot of the business card — was pulled and then left
out: it is a low-quality countertop shot and its card lettering ("ONTIME Auto Glass") does not
match the listing's own spelling.

Privacy edits applied before shipping:

- A cross-street sign naming the customer's intersection was blurred in
  `cargo-van-front-windshield.jpg`.
- A background vehicle's license plate was softened in `hero-super-duty-windshield.jpg`.
- **Painted-phone check:** no phone number is painted, lettered, or otherwise visible on any
  vehicle or surface in any photo, so the only number anywhere on the page is the Google-listed
  **(941) 786-8903**.

## Build notes

- **Tier 1 — Clean Slate.** White canvas, deep punctual-navy, clock-brass accent. This is the
  **third lane** in the glass trade portfolio-wide and shares nothing with its siblings:
  fast-glass-auto-glass (w76) owns the light glow / reflection-blue lane, autoglass-works (w74)
  owns the dark ice-blue edge-light lane. OnTime is crisp white/navy with brass.
- **The motif is a timetable.** The name is the brand, so punctuality is the visual system: brass
  tick-rails after every section eyebrow, a navy departure-board strip under the hero, a dotted
  hours ledger with tabular numerals, and a numbered 01/02/03 appointment rail. All of it is
  evidenced by the reviews, never by invented claims.
- **Structure** (deliberately different from both glass siblings): asymmetric split hero →
  timetable strip → **fleet section first** → services → the three-step appointment rail → work
  gallery → reviews → hours & service area → CTA.
- **Palette:** `#0d1c36` navy, `#a9793a` / `#c99a53` brass, `#f5f7fa` paper, white.
- **Fonts:** Albert Sans (display) + Inter (body).
- Self-contained `index.html` — inline CSS and JS, no build step, no external assets except
  Google Fonts.
- Mobile-first: H1 holds 2 lines at 390 px, zero horizontal overflow at 390/1366/1440, ≥ 44 px tap
  targets, icon-only header call button ≤ 600 px, brand name never clipped. **No fixed bottom call
  bar.**
- Hero stack (eyebrow → headline → sub → CTA pair → trust chip) clears the fold with room to
  spare: chip bottom at 664 px on 1440×900 and 612 px on 1366×768.
- Scroll reveals are IntersectionObserver-gated (threshold 0, `rootMargin` bottom +12%) with a
  momentum-scroll safety sweep, fully disabled under `prefers-reduced-motion`, and the page renders
  complete with JavaScript off.
- Reviews grid is 2-column on desktop, 1-column on mobile.
- `AutoRepair` JSON-LD with locality address, geo, opening hours and aggregate rating.
- Ken Burns settle on the hero photo, motion-gated.

### Deviation from the manifest

The manifest assigned the display font **"Albert Sans Mono"**. That family does not exist on Google
Fonts (`fonts.googleapis.com/css2?family=Albert+Sans+Mono` returns 404), and DESIGN.md bans
monospace display faces outright. The build uses the real **Albert Sans** — same type voice,
geometric and timetable-clean, rendered with `font-variant-numeric: tabular-nums` on every clock
and hours figure so the "timetable typography" intent survives.

## Call items for Wilson

- **Owner is Christian, goes by Chris.** Two reviews name him directly; one calls him "the owner".
- ***** **Lead with fleet accounts.** Omar at Integrity Electrical Services Inc. wrote that he has
  used them "several times for my fleet vehicles" and that Christian "has never let me down." That
  is the B2B lane and the whole site leads with it — a contractor with a fleet is a recurring
  customer, and OnTime already has one publicly saying so. Ask Chris how many fleet accounts he
  runs and whether he wants more of them; that is what the site is built to sell.
- **The name is the pitch.** "Came when he said he would" (Brian H.) and "He's always on time"
  (Omar) are the exact reason the business is named what it is. The hero, the strip and the
  three-step rail all run on that one promise.
- **Fair-price consistency** shows up in four of the five reviews — "very respectable price",
  "pricing is very fair", "price was reasonable", "great price".
- **No website at all** as of enrichment. Re-verify at call time (leads age), and eyeball the GBP
  for any sub-5 reviews the API did not surface before pitching the 5.0 display.
- Hours are Mon–Sat 7–6, Sunday closed — the site says so, so confirm that is still current.
- Address is residential, so the site never prints it. If Chris has a shop or wants the address
  shown, that is a five-minute change.

## Structure

`index.html` (self-contained) + `img/` (6 self-hosted JPEGs) + `.nojekyll`.

---

Website by [Wilson Innovations](https://wilsoninnovations.net).
