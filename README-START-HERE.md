# MuzHouse — Homepage Build

A fully-built, premium homepage as a live HTML/CSS/JS site. Open `index.html` in any browser to view it. No build step, no dependencies (fonts load from Google Fonts).

---

## 1. Swap in your real photos (the one thing to do)

I could see your five uploaded photos but couldn't read their files directly, so the site currently uses **on-brand placeholders** in `/images`. To go live, replace each placeholder with your real photo — **keep the exact same filename** and the site updates automatically.

| File in `/images` | Replace with (your upload) |
|---|---|
| `hero.jpg` | Photo 3 — Liuba + Marko standing in the sunset field (wide, lots of sky) |
| `duo-playing.jpg` | Photo 4 — the two of them playing together, facing each other |
| `instruments.jpg` | Photo 1 — the white Gretsch guitar + violin lying in the grass |
| `teacher-liuba.jpg` | Photo 2 — Liuba portrait in the white dress |
| `teacher-marko.jpg` | Photo 5 — Marko portrait in the floral blazer |
| `cta-final.jpg` | Photo 4 again (or any strong performance shot) |
| `perf-1.jpg`, `perf-2.jpg`, `perf-3.jpg` | Any recital / recording / on-stage photos as you get them |

Tip: export your photos at ~2000px on the long edge, save as JPG, name them to match, drop them in `/images`, done. (You can delete the leftover `gen.py` — it's just the script that drew the placeholders.)

The **logo** is rebuilt as crisp inline SVG (the green house-peak chevron + wordmark), so it stays sharp at any size and needs no file.

---

## 2. What's in the homepage (all 12 sections)

Hero → Why Music Matters → Why Families Choose MuzHouse → Meet Marko & Liuba (pinned story) → How It Works → Instruments (horizontal scroll) → Teachers → Student Performances → Testimonials → Service Areas (interactive map) → FAQ → Final CTA → Booking form. Every section routes toward **Book a Lesson** (6 CTAs site-wide).

---

## 3. Strategy notes (the thinking behind it)

**Brief audit — what I tightened.** The brief was strong; three things I adjusted for conversion: (a) sells *outcomes* not instruments — section copy leads with confidence/creativity/growth, instruments come later as the "what"; (b) the USP "we come to you" is repeated at hero, benefits, FAQ, footer and schema, not just once; (c) added a real booking form on the homepage so the primary CTA has somewhere to land on a single page.

**Design system (matched to your Figma template).** Pulled directly from your "MuzHouse" Figma file: warm cream `#FDF6EA` background, espresso `#4C433B` for text and buttons, `#ECDBCA` tan instrument cards with rounded images and circular arrow buttons, an arch-topped hero image, wavy line + star-sparkle accents, and the "We come to your home for the lessons" instruments grid. Type matches the Figma — Cormorant Garamond stands in for the "The Seasons" display serif (mixed roman/italic), with Montserrat for UI/body. All body and button text meets WCAG AA contrast on cream.

**Motion (all respect `prefers-reduced-motion`).** Cinematic hero zoom (100→106% over 28s), sequential hero text reveal, pinned Marko & Liuba panel with cross-fading "We teach with heart / purpose / experience / passion," scroll-reveal throughout, teacher-card lift + image scale on hover, horizontal instrument storytelling on desktop (vertical cards on mobile), and map pins that pulse/highlight in sync with the city list. No bounce, spin, scroll-hijack, or heavy parallax.

**SEO.** One H1, descriptive title + meta, semantic landmarks, every image has alt text, and three schema types embedded and validated: LocalBusiness (with areaServed + $60 offers), FAQPage, and Person (Liuba + Marko). Recommended next: build the dedicated landing pages — `/piano-lessons-sacramento`, `/guitar-lessons-sacramento`, `/voice-lessons-sacramento`, `/violin-lessons-sacramento`, `/in-home-music-lessons-sacramento`, `/charter-school-music-lessons`, `/homeschool-music-lessons`, `/areas-we-serve` — each reusing this design system with its own H1 and local copy.

**Porting to Framer.** This file is the visual + motion source of truth. In Framer: recreate the color/type tokens as variables, build each section as a component, use Scroll/Appear effects for the reveals and a horizontal-scroll section for instruments, and wire the form to Framer's form action or a booking tool (Calendly/Acuity) plus a Stripe link for the "payments through website" requirement.
