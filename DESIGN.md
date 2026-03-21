# AutoPilot Design System

> Updated 2026-03-21 after full premium redesign.
> Pass this to Stitch or Claude when generating new screens to maintain visual consistency.

---

## Color Palette

```css
--bg:    #04040D   /* page background — deep near-black with purple tint */
--s0:    #07071A   /* first surface — ticker, callout, CTA bg */
--s1:    #0B0B20   /* second surface — stats bar, problem cards */
--s2:    #0F0F26   /* third surface — cards, panels, inputs */
--s3:    #14142E   /* fourth surface — table headers */
--s4:    #1B1B3A   /* fifth surface — elevated / featured */
--v:     #8B5CF6   /* PRIMARY ACCENT — violet. Use for CTAs, borders, gradients */
--v2:    #A78BFA   /* lighter violet — eyebrows, links, highlights */
--v3:    #C4B5FD   /* lightest violet — badges, muted accents */
--cyan:  #22D3EE   /* secondary accent — gradient endpoint, status dots */
--pink:  #F472B6   /* tertiary — aurora only, not UI */
--white: #F2F2FF   /* primary text — slightly purple-tinted white */
--off:   rgba(242,242,255,.78)  /* secondary text */
--muted: #6060A0   /* muted text, labels, placeholders */
--dim:   rgba(242,242,255,.16)  /* faded text — "dim" headline words */
--win:   #4ADE80   /* success / AutoPilot column values */
--err:   #F87171   /* error / competitor column values */
```

**Usage rules:**
- `--v` and `--cyan` always used as a `linear-gradient(135deg, #8B5CF6, #22D3EE)` pair
- Gradient applied to: CTA buttons, gradient text on headings, stat numbers, logo mark, progress bar, feature dots, price amounts on featured card
- `--v` border at `rgba(139,92,246,.1–.28)` on cards; `.28` for featured, `.1` for standard
- Never use violet as a solid fill on large surfaces — only gradients or low-opacity tints
- Cards always use `--s2` background
- Featured/highlighted card uses `linear-gradient(145deg, rgba(139,92,246,.12) 0%, var(--s2) 60%)`
- Aurora blobs use `mix-blend-mode` NOT needed — just `filter:blur(80px)` radial gradients

---

## Typography

```css
--head: 'Plus Jakarta Sans', sans-serif   /* all text — headings and body */
--mono: 'Space Mono', monospace           /* numbers, labels, eyebrows, code */
```

**Google Fonts import:**
```html
<link href="https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@300;400;500;600;700;800&family=Space+Mono:wght@400;700&display=swap" rel="stylesheet">
```

**Size scale:**
```css
/* Hero display */
font-size: clamp(48px, 8.5vw, 116px);
font-weight: 800;
line-height: .93;
letter-spacing: -.04em;

/* Section headings (h2) */
font-size: clamp(34px, 5.5vw, 72px);
font-weight: 800;
line-height: .95;
letter-spacing: -.035em;

/* CTA heading */
font-size: clamp(36px, 6.5vw, 84px);
font-weight: 800;
line-height: .93;
letter-spacing: -.04em;

/* Card titles */
font-size: 21px;
font-weight: 700;
letter-spacing: -.02em;
line-height: 1.2;

/* Step/FAQ questions */
font-size: 16px;
font-weight: 700;
letter-spacing: -.01em;

/* Body / card body */
font-size: 13–14px;
font-weight: 400;
line-height: 1.75–1.78;

/* Eyebrows / labels */
font-family: Space Mono;
font-size: 10px;
letter-spacing: .18em;
text-transform: uppercase;
color: --v2;

/* Stat numbers */
font-family: Plus Jakarta Sans;
font-size: clamp(36px, 4.5vw, 58px);
font-weight: 800;
letter-spacing: -.04em;
gradient text: linear-gradient(135deg, #8B5CF6, #22D3EE)

/* Callout big number */
font-size: clamp(80px, 16vw, 180px);
font-weight: 800;
letter-spacing: -.05em;
gradient text

/* Nav brand */
font-size: 15px;
font-weight: 800;
letter-spacing: -.01em;
```

**Text modifier classes:**
- `.hl` — gradient text: `background: linear-gradient(135deg, #8B5CF6, #22D3EE); -webkit-background-clip: text; -webkit-text-fill-color: transparent`
- `.dim` — `color: rgba(242,242,255,.16); font-weight: 300` — secondary headline word

---

## Spacing

```css
/* Section vertical padding */
.sec: 120px top/bottom
.callout-band: 120px top/bottom
.cta-section: 160px top/bottom (with 48px horizontal)

/* Horizontal container */
max-width: 1160px (--max)
padding: 0 48px

/* Card padding */
standard card: 48px 40px (problem) or 48px (pricing)
how-it-works panel: 36px
roi inputs/outputs: 40px

/* Grid gaps */
problem grid: 2px gap (with violet bg — creates separator effect)
pricing grid: 24px gap
roi grid: 40px gap
video grid: 24px gap
how-it-works: 80px gap

/* Internal spacing */
eyebrow margin-bottom: 24px
card title margin-bottom: 12px
stat margin-top: 10px
```

---

## Borders & Radius

```css
/* Border radius */
cards (price, how-panel, roi): 20–22px
buttons: 8–10px
inputs: 9px
eyebrow badges: 100px (pill)
logo mark: 9px
phone: 40px
problem grid: 20px (border-radius on wrapper, overflow:hidden)
vid-card: 18px
step number box: 9px

/* Border colors */
standard card border: 1px solid rgba(139,92,246,.1)
featured card border: 1px solid rgba(139,92,246,.28)
active step: border-color: var(--v)
input focus: 1px solid rgba(139,92,246,.5) + box-shadow: 0 0 0 3px rgba(139,92,246,.1)
nav scrolled: border-bottom: 1px solid rgba(139,92,246,.1)
table header: background var(--s3)
faq open icon: border-color var(--v), background rgba(139,92,246,.1)

/* Featured card top line */
.price-card.feat::before: 1px gradient line
  background: linear-gradient(90deg, transparent, #8B5CF6, #22D3EE, transparent)
```

---

## Shadows & Effects

```css
/* Phone mockup */
box-shadow:
  0 0 0 1px rgba(255,255,255,.03),
  0 60px 120px rgba(0,0,0,.95),
  0 20px 40px rgba(0,0,0,.6),
  inset 0 1px 0 rgba(255,255,255,.05),
  0 0 60px rgba(139,92,246,.08);

/* Phone glow behind */
radial-gradient(circle, rgba(139,92,246,.18) 0%, transparent 65%)
filter: blur(60px)

/* Hero aurora blobs (3 layers) */
.ab1: rgba(139,92,246,.22) — purple, top-left, 680px, blur 80px
.ab2: rgba(34,211,238,.12) — cyan, top-right, 580px, blur 80px
.ab3: rgba(244,114,182,.07) — pink, bottom-center, 480px, blur 80px
All animated with slow drift keyframes (22–30s infinite alternate)

/* Nav backdrop */
background: rgba(4,4,13,.9)
backdrop-filter: blur(24px)

/* Button hover glow */
box-shadow: 0 16px 50px rgba(139,92,246,.45)

/* Logo mark glow */
box-shadow: 0 4px 20px rgba(139,92,246,.4)

/* How-panel subtle glow */
box-shadow: 0 0 60px rgba(139,92,246,.05)

/* Noise texture */
SVG fractalNoise, opacity .028, position:fixed, pointer-events:none

/* Scrollbar */
width: 3px, thumb: var(--v), track: var(--bg)
```

---

## Animations

**Hero entrance (GSAP):**
```javascript
// Staggered entrance
gsap.to('#heroBadge',   {opacity:1, y:0, duration:.7,  delay:.2,  ease:'power3.out'});
gsap.to('.word',        {opacity:1, y:0, duration:.65, stagger:.09, delay:.35, ease:'power3.out'});
gsap.to('#heroSub',     {opacity:1, duration:.8,  delay:.9,  ease:'power3.out'});
gsap.to('#heroActions', {opacity:1, duration:.7,  delay:1.05, ease:'power3.out'});
gsap.to('#heroPhone',   {opacity:1, y:0, duration:1, delay:1.2, ease:'power3.out'});
// Float loop after entrance
gsap.to('#heroPhone', {y:-10, duration:3.8, repeat:-1, yoyo:true, ease:'sine.inOut'});

// Scroll reveals
gsap.fromTo('.reveal', {opacity:0, y:28}, {
  opacity:1, y:0, duration:.8, ease:'power3.out',
  scrollTrigger:{trigger:el, start:'top 90%'}
});
```

**CSS keyframe animations:**
```css
/* Aurora blob drift */
@keyframes ab1d { 0%{transform:translate(0,0) scale(1)} 100%{transform:translate(80px,60px) scale(1.14)} }
@keyframes ab2d { 0%{transform:translate(0,0) scale(1)} 100%{transform:translate(-60px,80px) scale(.92)} }
@keyframes ab3d { 0%{transform:translate(0,0) scale(1)} 100%{transform:translate(-40px,-60px) scale(1.08)} }
/* All run: 22–30s ease-in-out infinite alternate */

/* Badge ping dot */
@keyframes ping { 0%,100%{transform:scale(1);opacity:.9} 60%{transform:scale(3);opacity:0} }
/* duration: 2s ease-in-out infinite */

/* SMS bubble pop */
@keyframes bubPop { from{opacity:0;transform:scale(.88) translateY(8px)} to{opacity:1;transform:none} }

/* Typing dots */
@keyframes tdot { 0%,60%,100%{transform:translateY(0);opacity:.28} 30%{transform:translateY(-5px);opacity:1} }

/* Activity ticker scroll */
@keyframes tkr { 0%{transform:translateX(0)} 100%{transform:translateX(-50%)} }
/* duration: 44s linear infinite */

/* Marquee scroll */
@keyframes mq { 0%{transform:translateX(0)} 100%{transform:translateX(-50%)} }
/* duration: 36s linear infinite */

/* Stat item bottom border on hover */
transform:scaleX(0) → scaleX(1), origin left, 0.4s transition
```

**Interaction behaviors:**
- Magnetic buttons: `translate(x * .15, y * .15)` on mousemove, reset on mouseleave
- Phone 3D parallax: `perspective(900px) rotateX(Xdeg) rotateY(Ydeg)` on mousemove, max ±5°
- Step progress bar: fills 0→100% over 4500ms via setInterval, resets on step change
- FAQ accordion: one open at a time, icon rotates 45° when open
- Nav: background + border appears after 40px scroll
- Dual cursor: dot follows exactly, ring lags at 12% lerp rate, expands to 52px on hover

---

## Components

### Nav
```
- Fixed, full-width, height: 70px (--nav-h), padding: 0 48px
- Logo: gradient square mark (32×32, 9px radius, violet→cyan) + "AutoPilot" 15px 800w
- Center: nav links 13px 500w, color --muted, hover --white
- Right: badge pill (violet tint) + "Book Demo" gradient button
- On scroll: rgba(4,4,13,.9) + backdrop-filter:blur(24px) + violet border-bottom
```

### Hero
```
- Min-height: 100vh, centered, text-align: center
- z-index layers: aurora (0) → dot-grid (0) → content (1) → phone (2)
- Badge: violet border pill + ping cyan dot
- Headline: clamp 48–116px, 800w, -.04em tracking, word-by-word animation
- Sub: 15–19px, 400w, --muted color, max-width 500px
- CTAs: gradient primary + ghost border secondary
- Phone: 260px wide, 40px border-radius, float animation, 3D tilt on mousemove
```

### Phone Mockup
```
- Width: 260px, background --s0, 40px border-radius
- Island: 90×26px, dark, rounded bottom corners
- Screen height: 490px, flex column
- Header: gradient avatar (AP), name + status dot + mono time
- SMS feed: auto-scroll, no scrollbar, gap 6px
- AI bubbles: rgba(139,92,246,.12) bg + border, left-aligned, bl-radius 3px
- User bubbles: rgba(242,242,255,.06), right-aligned, br-radius 3px
- System: centered, no bg, --muted
- Calendar: rgba(34,211,238,.08) bg, cyan border, left-aligned
- Typing: 3 violet dots bouncing (tdot animation)
```

### Activity Ticker
```
- Single row, background --s0, 13px padding, border top+bottom
- Fade edges via ::before/::after gradients (width 100px)
- animation: 44s linear infinite (translateX 0 → -50%)
- Items: emoji + text, --muted base, .tick-hi for violet-highlighted names
```

### Stats Bar
```
- 4-column grid, background --s1, no outer border
- Each cell: 52px 40px padding, border-right rgba(139,92,246,.08)
- Number: gradient text, clamp 36–58px, 800w, -.04em
- Label: 13px, 400w, --muted, max-width 170px
- Hover: background --s2, gradient bottom border slides in
- Counters: IntersectionObserver on #statsBar parent, threshold .3
```

### Marquee
```
- Single row, background --bg, 14px padding
- Tech names in Space Mono, 10px, .12em tracking, uppercase, very dim color
- Preceded by tiny 3px violet dot
- animation: 36s linear infinite
```

### Problem Cards
```
- 3-column grid, 2px gap, violet tint bg (creates separator line effect)
- Border-radius 20px on wrapper (overflow:hidden)
- Each card: --s1 bg, 48px 40px padding
- Hover: --s2 bg, translateY(-4px)
- Hover: 2px gradient top line scaleX 0→1
- Icon: 46×46 box, 12px radius, violet tint + border
- Mono label (01/02/03) above title
- Body: 14px, 400w, 38% opacity
- Stat badge: red tint, Space Mono, 10px
```

### How It Works Steps
```
- Steps: border-top/bottom dividers, flex gap-20 layout
- Step number: 34×34px box, 9px radius, violet when active
- Title: 16px 700w — white when active, 28% opacity when inactive
- Body: max-height: 0 collapsed → 220px expanded (0.45s transition)
- Progress bar: 2px height, gradient fill 0→100% over 4500ms
- Auto-advances every 4500ms, click to override
```

### Results Panel (sticky)
```
- Position: sticky top:100px on desktop
- --s2 bg, 36px padding, 20px radius, violet border
- Rows: label (40% opacity) + before (strikethrough mono) / after (gradient 800w 16px)
- Note: violet tint bg + border, 18px padding, 13px body
```

### Comparison Table
```
- Border-radius 20px wrapper, overflow:hidden, violet border
- Header: --s3 bg, Space Mono 10px uppercase
- AutoPilot column header: violet tint bg, --v2 color
- AutoPilot column cells: violet tint bg
- Win values: #4ADE80 (emerald), Lose values: rgba(248,113,113,.7)
- Row hover: --s3 bg
```

### ROI Calculator
```
- 2-column grid (inputs left, results right), 40px gap
- Inputs panel: --s2 bg, 40px padding, violet border
- Slider: 4px track, gradient fill using CSS --pct custom property
- Thumb: 20px white circle, 3px violet border, violet ring shadow
- Results panel: violet inner glow (radial gradient ::before)
- Big number: clamp 42–78px, gradient text
- Rows: Space Mono values, win/lose colors
- CTA: gradient button at bottom
```

### Pricing Cards
```
- 2-column, max-width 880px, 24px gap
- Standard: --s2 bg, violet .1 border
- Featured: violet gradient tint bg, .28 border, gradient top line ::before
- Price amount: standard = white, featured = gradient text
- Feature list: gradient dots as bullets, 13px 400w body
- CTA: standard = border button, featured = gradient button
```

### CTA Form
```
- Centered, max-width 560px, --s0 bg section
- Fields: name, email, business (agency), phone
- Input: --s2 bg, violet border, 9px radius, 14px 400w
- Focus: violet border + tint bg + box-shadow ring
- Label: Space Mono 9px uppercase --muted (above input)
- Submit: full-width gradient button, 800w
- Action: formsubmit.co (no server needed)
```

---

## Brand Guidelines (Copy Rules)

**Tone:** Direct, specific, no corporate speak
**Audience:** Staffing agency owners — busy, skeptical, value ROI
**Never use:** leverage, utilize, streamline, game-changer, comprehensive, em-dashes
**Headlines:** Problem-focused, specific scenarios ("A candidate applies at 11pm...")
**CTAs:** "Book a Free Demo" / "Book My Free Demo" / "Book a Demo →"
**Stats:** Always specific (83%, 38%, 3×, +6) — never vague
**Social proof:** Industry stats only — no fake testimonials

---

## Stitch Prompt Template

> Copy-paste this when creating a new screen in Stitch:

```
SCREEN: [Name of screen]
PRODUCT: AutoPilot — AI candidate screening and follow-up automation for independent staffing agencies (commercial, light industrial, clerical). Owner or GM is the buyer. Non-technical. Value speed and ROI.

DESIGN SYSTEM (match exactly, non-negotiable):
Background: #04040D (near-black with purple tint)
Cards/surfaces: #0F0F26 with 1px rgba(139,92,246,0.1) border
Accent: linear-gradient(135deg, #8B5CF6, #22D3EE) — use ONLY on CTAs, gradient text, feature dots, borders
Primary text: #F2F2FF (slightly purple-tinted white)
Secondary/muted text: #6060A0
Faded/dim text: rgba(242,242,255,0.16) at 300 font-weight
Font: Plus Jakarta Sans — headings 700-800 weight, body 400 weight, tight letter-spacing (-.03 to -.04em)
Mono font: Space Mono — for numbers, stats, labels, eyebrows
Aesthetic: ElevenLabs / Stability AI — deep dark, minimal, aurora glow effects, premium
Section padding: 120px top/bottom, 48px horizontal, max-width 1160px
Card border radius: 20-22px; button radius: 8-10px
Hero background: 3-layer animated aurora blobs (violet, cyan, pink — blurred radial gradients)
No heavy shadows, no colorful gradients on backgrounds, no stock photo aesthetics

SECTION REQUIREMENTS:
[Describe the sections needed for this screen]

PRIMARY GOAL:
[What action should a visitor take?]

DO NOT:
- Use Webflow/Squarespace template aesthetics
- Add colorful gradients or loud backgrounds
- Use serif or decorative fonts
- Add stock photo placeholder images
- Use blue or green as the primary accent color (it's violet/purple)
- Use flat solid violet fills on large areas (use tints and gradients only)
```
