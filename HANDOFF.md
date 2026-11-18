# Handoff: Grab-N-Go Lockers, coming-soon site

## Overview
One-page, mobile-first coming-soon site for Grab-N-Go Lockers: secure, temperature-regulating pickup lockers for pharmacy, food and drink orders. The page introduces the product through an interactive "locker wall" and adds two tabs: **Know more** (a sample pickup log printed like a slip) and **Security** (a keypad demo with the locker's logic shown as code).

## Quick publish (no build)
`index.html` is a single self-contained file (fonts, images, scripts inlined). Upload it to any static host (Netlify Drop, Vercel, GitHub Pages, Cloudflare Pages, or your existing web host) and it works as-is.

## About the design files
`reference/Grab-N-Go Website.dc.html` is a **design reference built in HTML**: a prototype showing intended look and behavior. If you are rebuilding the site in a codebase (React, Next.js, Astro, plain HTML/CSS…), recreate it using that environment's patterns. If there is no codebase yet, a single static page (plain HTML/CSS + a little JS, or Astro) is the best fit.

## Fidelity
**High-fidelity.** Final colors, type, spacing, copy and interactions. Recreate pixel-faithfully.

## Page structure
Max content width 1200px, centered, side padding clamp(16px, 4vw, 48px), bottom padding 96px. Vertical gap between major blocks clamp(40px, 7vw, 96px). White background (#FFFFFF), ink #0A0A0A.

### Header
- Left: logo lockup, height clamp(64px, 9vw, 88px). Snowflake (navy #02366C, stroke 9 in a 112 viewBox, round caps) | 2px divider (#55636D, 72% height) | three flames (#A8213A). Then "Grab-N-Go" Archivo 900, clamp(28px,4vw,38px), letter-spacing -0.045em, line-height .9; under it "HEATING & COOLING LOCKERS" Archivo 500, clamp(10px,1.2vw,12px), letter-spacing .14em, #333.
- Right: tab nav (Lockers / Know more / Security): Archivo 15px, 44px min height, padding 0 14px, active = weight 700 + 2px bottom inset line #0A0A0A; inactive weight 500, hover shows the line.
- "Contact" button: mailto, #0A0A0A bg, white 15px/700, min-height 44px, padding 0 18px, hover bg = accent (#A8213A).
- Header has a 1px #0A0A0A bottom border, 18px padding-bottom. Wraps on small screens.

### Tab 1: Lockers (default)
- Intro row: 2-col auto-fit grid (min 340px), gap 24px 48px, aligned to bottom.
  - H1 "Open<br>a door." Archivo 900, clamp(56px,10vw,128px), line-height .9, letter-spacing -0.045em.
  - Paragraph: "Secure, temperature-regulating pickup lockers. Each door holds one thing about us. Tap to open." 18px/1.6, #333, max 44ch.
- Toolbar row: right-aligned "Open all" / "Close all" text button (14px/700 underline), 1px bottom border.
- Locker grid: `repeat(auto-fit, minmax(min(100%,420px),1fr))`, rows min 340px, gap 8px → 2×2 on desktop, 1 column on phone.
- **Closed door** (button covering the cell): white, 1px #0A0A0A inset border, padding 20px. Big number top-left (01–04) Archivo 900 clamp(56px,7vw,80px); bottom row: label (Archivo 700 clamp(20px,2.2vw,24px)) + a thin handle (8×40px, 1px border, radius 4px). Hover bg #F5F5F3.
- **Open interior** (metal locker):
  - Steel frame: 10px padding, gradient #9EA3A8 → #7D8288.
  - Back wall: radial-gradient(ellipse at 50% 45%, #6F7479, #474B50 85%). Locker 02 (cooled) uses #5D7690 → #344A61.
  - Ceiling, side walls and floor are clip-path polygons: ceiling to 6% depth, side walls 8% inset, floor from 84% down. Floor gradient #6C7177 → #8E9399 → #7A7F85.
  - Shelf bar at top 30%, inset 3%, height 10px, gradient #C9CDD1 → #9A9EA3 → #6F7378, shadow 0 10px 14px -4px rgba(0,0,0,.45). Small hook on left wall at 36%.
  - Text sits above the shelf (top 6%, height 24%, padding 0 12%): white #F4F5F6, Archivo 700, clamp(26px,3vw,34px), line-height 1.1.
  - Items stand on the floor (absolute, bottom 9%, centered), each with an elliptical contact shadow and a faint reflection (`-webkit-box-reflect: below 1px linear-gradient(transparent 78%, rgba(255,255,255,.22))`).
  - "Close" text button top-right (13px/700, white, underline).
- **Locker content**

  | # | Door label | Interior text | Items |
  |---|---|---|---|
  | 01 | What it is | Pick up with a code. Anytime. | pickup-bag.svg |
  | 02 | Medicine, food & drinks | Kept cold or warm until pickup. | medicine.svg, drink.svg, food.svg (overlap −6px) |
  | 03 | Logged | Every pickup and temperature, recorded. | log.svg |
  | 04 | Get in touch | Say hello. | Four "books" (links) |

  Item widths: single item clamp(90px,10vw,118px); in 02: medicine clamp(70px,8vw,92px), drink clamp(62px,7vw,80px), food clamp(64px,7.2vw,84px).
- **Books (locker 04)**: upright `<a>` blocks on the floor, 3px gap, radius 3px 3px 2px 2px, spine highlight/shade insets, vertical label (writing-mode vertical-rl, rotated 180°, 15–18px, 800, uppercase). Hover lifts translateY(-10px).
  - Email: #A8213A / white, w clamp(46px,5vw,58px), h clamp(132px,15vw,168px), mailto:grabngolockers@proton.me
  - Call: #02366C / white, w clamp(44px,4.6vw,54px), h clamp(118px,13vw,148px), tel:+18049334543
  - Text: #EFE6D2 / #1F2A33, w clamp(44px,4.8vw,56px), h clamp(126px,14vw,158px), sms:+18049334543
  - LinkedIn: #2B2F33 / #F4F5F6, w clamp(46px,5vw,58px), h clamp(140px,15.5vw,172px), leaning rotate(-7deg) from bottom-left, opens https://www.linkedin.com/company/grab-n-go-lockers/ in new tab.

### Tab 2: Know more
- Split layout (wraps): left column with H1 "Every pickup leaves a trail." Archivo 900, clamp(44px,7vw,92px), line-height 1.04, letter-spacing -0.035em; paragraph "Each locker records every collection and temperature reading automatically. Here's a sample log."
- Right: #F5F5F3 panel, 1px #0A0A0A border, holding a printer slot (14px black bar) and a white slip in IBM Plex Mono 14px/1.5, zig-zag bottom edge. Content: header (GRAB-N-GO LOCKERS / PICKUP RECEIPT / STATUS: COMING SOON), locker details, TEMP LOG (SAMPLE) table with tabular numbers, the company description, CSS barcode, "THANK YOU · SEE YOU SOON".
- On entering the tab the slip "prints": translateY(-100%) → 0 over 2.6s with `steps(26)`.
- Sample log values (marked SAMPLE): 09:12 LOADED 4.2 °C · 11:00 READING 4.0 °C · 13:00 READING 4.1 °C · 15:00 READING 3.9 °C · 17:48 COLLECTED 4.1 °C.

### Tab 3: Security
- H1 "One code." + paragraph "Try the keypad and watch what the locker does behind the door. Enter 2468, or a wrong code three times."
- Two panels (auto-fit, min 340px, gap 8px):
  - Keypad: 1px border, 4 code boxes (64px high, IBM Plex Mono 28px, shows •), 3×4 key grid (min-height 56px, 1px border, Archivo 20px/700, hover #F5F5F3, active black/white), status top-right (Ready / n tries left / Unlocked green #15803D / Locked red #B91C1C), "Reset demo" link.
  - Code panel: #0A0A0A, IBM Plex Mono 13px/1.7, header "locker.js · Simplified example", 11 numbered lines of pseudo-code, and an event log (last 6 events, timestamps HH:MM:SS).
- Logic: correct code 2468 → highlight unlock/invalidate/log lines green, log "CODE ACCEPTED / DOOR 07 UNLOCKED / CODE INVALIDATED · one-time use / COLLECTED · 4.1 °C at pickup". Wrong → attempts +1, highlight the attempt lines red, log "WRONG CODE · attempt n of 3", 0.35s ×2 shake. Third wrong → "LOCKER 07 LOCKED · staff alerted", further attempts "DENIED · locker is locked".
- **Note:** one-time codes, 3-attempt lockout and staff alerts are illustrative. Confirm with the product team before launch.

### Footer
6px #0A0A0A top border, 18px padding-top. "Coming soon." Archivo 900, font-size calc(clamp(64px,9vw,88px) / 0.69) so cap height equals the header logo height, letter-spacing -0.045em. "© 2026 Grab-N-Go Lockers" 14px #333 on the same row, right-aligned, baseline-ish (padding-bottom 6px); wraps under on phones.

## Interactions & state
- `page`: 'lockers' | 'receipt' | 'security' (tabs; scroll to top on change; receipt reprints on enter).
- `doors`: map of open lockers. Door open = rotateY(-100deg), transform-origin left, perspective 1200px (origin left), 0.7s cubic-bezier(.2,.7,.2,1). Cell has overflow hidden so the door never covers neighbors. Door has z-index above interior items.
- Security: `code`, `attempts`, `locked`, `open`, `result`, `log[]`.
- Optional config used in the prototype: accent color (#A8213A default), columns 2 or 4, all doors open on load.

## Design tokens
- Ink #0A0A0A · White #FFFFFF · Panel #F5F5F3 · Body grey #333333 · Navy #02366C · Brand red #A8213A · Divider grey #55636D · Cream #EFE6D2
- Fonts (Google Fonts): Archivo 400/500/700/900 (UI + display), IBM Plex Mono 400/500/600 (slip, code)
- Radii: 0 for UI (sharp, Swiss style); books 3px
- Shadows: none on UI; only inside the locker illustration

## Assets
- `assets/illustrations/*.svg`: flat outlined illustrations drawn for this project (pickup bag, medicine, drink, burger, clipboard + thermometer).
- `logo/*.png`: vector-redrawn Grab-N-Go logo exports (white, transparent, navy; icon variants). The header logo is inline SVG + live text.

## Files
- `index.html`: publish-ready, self-contained page.
- `reference/Grab-N-Go Website.dc.html`: source prototype (needs the design runtime; use as reference).
- `assets/`, `logo/`: image assets.
