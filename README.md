# Bobby Lee's Scrapping & Recovery — website

Single-page site, no build step, no JavaScript. Just `index.html` + `img/`.

## Deploying (Netlify)

Static publish from the repo root — `netlify.toml` is already set up, so there is
nothing to configure in the Netlify UI beyond connecting the repo:

1. Netlify → **Add new site → Import an existing project → GitHub**
2. Pick `admirolltodd/Bobby-lee-scrapping`
3. Build command: *(empty)* · Publish directory: `.` — both come from `netlify.toml`
4. Deploy

After that, every push to the connected branch redeploys automatically.

## Contact links
- Phone: 850-758-3698 (tel: and sms: links throughout)
- Email: Bobbylduvall@gmail.com
- Text button pre-fills a message body via `sms:+18507583698?&body=...`
  (the `?&` prefix is intentional — works on both iOS and Android URL schemes)

## Structure
- `index.html` — everything: HTML + inline `<style>`. No JavaScript at all (the old scroll-reveal `<script>` and `.rise` classes were removed in the last rebuild — verified gone)
- `img/` — three jobsite photos (work-trim.jpg, work-patch.jpg, work-wall.jpg), resized to 900px max dimension, compressed JPEG

## Design system
- Palette: verdigris/pine/paper "reclaimed" theme — CSS custom properties at top of `<style>`
- Fonts: Bricolage Grotesque (display), Karla (body) — loaded from Google Fonts CDN
- Mobile-first CSS, sticky bottom action bar (`.dock`) on screens <860px, hidden on desktop
- Business name: Bobby Lee's Scrapping & Recovery (rebranded from an earlier "contractor consultant" concept — see hero copy)

## Known open items from the client (Robert, building this for Bobby)
1. **Does Bobby ever pay cash for valuable items** (tool chests, running mowers, etc.) rather than just free pickup? Currently the site's ceiling is "free to you" — no purchase offer. If yes, needs a 5th card in "The Deal" section.
2. **Verify SMS deep link behavior on Bobby's actual phone** — Android launchers vary; test that the prefilled body renders correctly.
3. Placeholder areas to double check: none currently — phone/email/service area are all real as of last update.
4. Three jobsite photos are real but casual (mid-task, not posed) — consider asking for 1-2 more polished/varied shots if Bobby wants a fuller gallery later.

## Recent direction changes (for context if continuing)
- Started as a dark "steel data-plate" concept, metallic blue, automotive vibe — fully discarded per client request ("hate the font," "save the planet feel")
- Rebuilt light/paper background, verdigris-green palette, Bricolage Grotesque + Karla
- Service emphasis shifted over time: general contractor → reuse/haul-off led → now scrapping & recovery led, with "metal taken always, no exceptions" as the signature hook
- Trade work (electrical/carpentry/masonry/auto) is now secondary content below the fold, not the hero pitch
