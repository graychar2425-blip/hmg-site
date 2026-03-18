# HMG Website — Claude Code Context

## What this is
The marketing website for **Hilltop Management Group (HMG)** — a Milwaukee-based treasury management firm targeting private equity and real estate sponsors. The site is a single-file static HTML app.

## Owner
Danny Fink — founder of HMG. He directs changes conversationally; Claude Code implements them.

## Deploy pipeline
- **Repo:** `github.com/graychar2425-blip/hmg-site`
- **Auto-deploy:** Push to `main` → GitHub Actions → `npx wrangler pages deploy` → Cloudflare Pages
- **Live URL:** `https://www.hilltopmanagementgroup.com`
- **Preview URL:** `https://hilltopmanagementgroup.pages.dev`
- Deploy takes ~60 seconds after push

## File structure
```
index.html   ← the entire site (HTML + CSS + JS in one file)
CLAUDE.md    ← this file
.github/
  workflows/
    deploy.yml  ← Cloudflare Pages deploy workflow
```

## Design system
**Aesthetic:** Dark institutional — refined, not flashy. Think Bloomberg Terminal meets private equity pitch deck.

**Fonts (loaded from Google Fonts):**
- `--serif: 'Cormorant Garamond'` — headlines, display text
- `--sans: 'Barlow'` — body, nav, labels
- `--mono: 'IBM Plex Mono'` — stats, data, CTAs, tags

**Color palette (CSS variables):**
```css
--black:   #070B12   /* page background */
--ink:     #0D1320   /* card/section backgrounds */
--surface: #111827   /* elevated surfaces */
--line:    rgba(255,255,255,0.07)  /* borders */
--cream:   #F0EAD6   /* primary text */
--muted:   #8A8680   /* secondary text */
--gold:    #C4993A   /* primary accent — CTAs, highlights */
--gold-lt: #E8C068   /* lighter gold for hover states */
--teal:    #3ABFB0   /* secondary accent — data, metrics */
--red:     #C45B4A   /* warning/negative */
```

## Site sections (in order)
1. **Nav** — fixed top bar with logo, links, "Schedule a Call" CTA
2. **Hero** — headline, subhead, two CTAs, animated stat counters
3. **Services** — 4 service cards (Treasury Infrastructure, Capital Deployment, Fund Finance, Strategic CFO)
4. **Economics** — fee table showing how HMG earns (basis points on AUM tranches)
5. **Process** — 4-step engagement timeline
6. **Validation** — key stats (AUM managed, yield improvement, time-to-deploy, liquidity ratio)
7. **ICP** — Ideal Client Profile criteria
8. **Footer** — contact info, nav links, legal

## Key content placeholders to update
- **Calendly link:** `https://calendly.com/hilltopmanagementgroup/30min` — needs real URL when available
- **Email:** `capital@hilltopmanagementgroup.com` — verify this is active

## Coding rules
- Keep everything in `index.html` — do not split into multiple files unless explicitly asked
- Preserve all CSS variables — never hardcode colors
- Do not change fonts without explicit instruction
- Maintain the grain overlay (`body::before`) — it's intentional
- The `.bleed-num` stat elements need `min-width: 9rem; flex-shrink: 0` — do not remove
- The economics table is wrapped in `.econ-table-wrap` with `overflow-x: auto` — keep this for mobile

## After making changes
```bash
git add index.html
git commit -m "describe what changed"
git push origin main
```
Cloudflare deploys automatically. No build step needed.
