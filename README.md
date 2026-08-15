# Bobby Lee's Scrapping & Recovery — website

Single-page site, no build step. `index.html` + `img/` + `robots.txt` + `sitemap.xml`.

## Deploying (Netlify)

Static publish from the repo root — `netlify.toml` is already set up, so there is
nothing to configure in the Netlify UI beyond connecting the repo:

1. Netlify → **Add new site → Import an existing project → GitHub**
2. Pick `admirolltodd/Bobby-lee-scrapping`
3. Build command: *(empty)* · Publish directory: `.` — both come from `netlify.toml`
4. Deploy

After that, every push to the connected branch redeploys automatically.

## ⚠️ Before launch — do these

1. **Set the real domain.** `bobbyleesscrapping.com` is a placeholder in four
   places: the `<link rel="canonical">` and og/twitter URLs in `<head>`, the
   `@id`/`url` fields in the JSON-LD block, `robots.txt`, and `sitemap.xml`.
   Find-and-replace the whole string once the domain is pointed at Netlify.
2. **Fill or delete the two remaining review slots.** The "Word of mouth"
   section carries one real quote (Robert's, first card) and two dashed
   placeholders reading *"Waiting on a real customer quote."* Replace those with
   something real customers actually said, or delete them — the section reads
   fine with one quote. **Do not invent reviews** — fake testimonials are the one
   thing that will sink a small local business's credibility, and they violate
   FTC endorsement rules.
   - Robert's quote is attributed by first name only. Add a town or last initial
     if he wants it; a fuller attribution reads as more credible.
   - The featured quote carries `class="quote lead"`, which runs it full width
     above the others at larger type. Move `lead` to whichever quote is the
     strongest, or drop it entirely once there are three or four real ones.
3. **Verify the SMS deep link on Bobby's phone.** Android launchers vary; check
   that the prefilled body renders.
4. **Submit the sitemap** in Google Search Console, and claim/fill the Google
   Business Profile — the schema on this page supports a GBP listing, it does
   not replace one.

## Contact links
- Phone: 850-758-3698 (tel: and sms: links throughout)
- Email: Bobbylduvall@gmail.com
- Text button pre-fills a message body via `sms:+18507583698?&body=...`
  (the `?&` prefix is intentional — works on both iOS and Android URL schemes)

## Structure
- `index.html` — everything: HTML, inline `<style>`, JSON-LD, and two small
  inline `<script>` blocks (see *Motion layer* below)
- `img/` — jobsite photos, resized to 900px max dimension, compressed JPEG
- `robots.txt`, `sitemap.xml` — both hardcode the site URL, see item 1 above

## Design system — "Deep Salvage"
- Dark theme throughout: near-black pine ground, electric lime (`--lime`) as the
  action color, verdigris (`--teal`) as the secondary. All tokens are CSS custom
  properties at the top of `<style>`; changing the palette means editing ~12 lines.
- Fonts: Bricolage Grotesque (display), Karla (body) — Google Fonts CDN
- Mobile-first, sticky bottom action bar (`.dock`) under 860px
- Grain overlay via inline SVG turbulence on `body::before`

## Motion layer (added back deliberately)
The site had no JavaScript for a while. It has ~2KB again, for scroll effects.
It is written as strict progressive enhancement — **keep it that way**:

- The hidden state for scroll reveals is scoped to `.js .r`, and the `js` class
  is only added by the head script when `IntersectionObserver` exists. With JS
  off, blocked, or broken, every section renders normally. Verified with
  `javaScriptEnabled: false`.
- The head script also sets a 2.5s failsafe that reveals everything if the main
  script never runs. The main script sets `data-revealing` on `<html>` to call
  it off.
- Stat counters print their **real values** in the HTML. The motion script zeroes
  them at init and counts them back up, so no-JS visitors see `30+`, not `0`.
- Everything bails out entirely under `prefers-reduced-motion: reduce`, which the
  CSS also enforces with `!important` overrides.

Effects: scroll progress bar, section reveals, count-up stats, headline rule
draw-in, drifting hero gradient, parallax on the photo strip.

## Photo strip
`.shots` is a scroll-snapped horizontal strip under 640px and a 3-up grid above
it. **Adding more photos needs nothing but another `<figure>`** — both layouts
reflow on their own. Give each new `<img>` a descriptive `alt` that names the
work and the town (it's doing SEO duty too).

## SEO
- JSON-LD `@graph` with `LocalBusiness`/`HomeAndConstructionBusiness`, `Service`,
  and `FAQPage`. The FAQ schema mirrors the visible accordion — **if you edit an
  FAQ answer on the page, edit it in the JSON-LD too** or the markup goes stale.
- `areaServed` is a 96,560m (60mi) GeoCircle around Crestview plus named counties
  and towns.
- Keyword-carrying headings, a dedicated service-area town list, geo meta tags,
  OG/Twitter cards.
- Copy stays in Bobby's first-person voice; keywords ride inside real sentences
  rather than being stacked. Keep it that way — it reads as trustworthy, which is
  the actual conversion mechanism for a one-man operation.

## Honesty constraints baked into this page
These are deliberate. Don't "improve" them without asking:
- **No fabricated statistics.** Every number in the proof band is verifiable:
  30+ years, 60-mile radius, ≤48hr turnaround, 3 counties, and 0 lb of metal
  landfilled (which is Bobby's stated policy, not a measurement). If Bobby ever
  supplies real tonnage or load counts, that's the place to add them.
- **No fake reviews.** See launch item 2.
- **Cash for valuable items** — Bobby sometimes pays cash for things like tool
  chests or running mowers, but this is intentionally *not* advertised. "The Deal"
  section's public ceiling stays at free pickup; don't add a purchase-offer card.

## Direction history (context if continuing)
- Started as a dark "steel data-plate" concept, metallic blue, automotive vibe —
  discarded per client request ("hate the font," "save the planet feel")
- Then light paper/verdigris theme
- Now "Deep Salvage": dark, high-contrast, same green family, built to make
  photos of Bobby pop
- Service emphasis: general contractor → reuse/haul-off led → scrapping &
  recovery led, with "metal taken always, no exceptions" as the signature hook
- Trade work (electrical/carpentry/masonry/auto) is secondary content below the
  fold, not the hero pitch

## Ideas researched but not built
Pulled from what national chains and reuse networks do that this site doesn't.
Ranked by likely payoff:
1. **The Free Pile** — a browsable grid of recovered items Bobby is giving away.
   This is the Freecycle/Buy Nothing hook and no local competitor has it; it
   drives repeat visits and inbound texts. Starts as a hand-edited list.
2. **Load-size estimator** — visual ¼/½/full trailer picker that sets
   expectations before the text and pre-fills the message body.
3. **Real diversion numbers** — the chains lead with landfill-diversion
   percentages. Needs real data from Bobby first (see honesty constraints).
