# Uncle Inc. — Build Plan

## 1. PRODUCT

Uncle Inc. is a pre-launch marketing landing page for an AI-assisted MVP development platform targeting non-technical, time-poor early-stage startup founders. The page converts visitors into waitlist signups by positioning Uncle Inc. as the fastest path from "napkin sketch" to validated, testable prototype — without a technical co-founder. Per the design session (`e95180e2cf4841b0a4f2c0dc936244ed/design.md`), the visual system uses a "Crisp Operator" archetype with a switchboard motif: navy `#1A3A5C` primary, cobalt `#4A90D9` secondary, green accent `#22C55E`, Inter for headings, IBM Plex Sans for body. Core value: collapse months of dev cycles into 72 hours of structured AI-assisted validation. The landing page is the entire shipped product — there is no authenticated app, no dashboard, no backend.

## 2. WHO IT'S FOR

The ICP is the solo non-technical first-time founder, 25–40, with a validated hypothesis but no engineering co-founder and limited runway. They're skeptical of hype, time-poor, allergic to jargon, and want to see the value proposition above the fold. Per the prior research session notes, the design system is built around this persona: a single primary CTA on first paint ("Join the Waitlist"), short scannable feature copy, no nested navigation, no fake testimonials, no invented customer counts. Tone: confident, plain-spoken, operator-first. Every word assumes the reader is evaluating whether this tool is real or vaporware.

## 3. LOOK & FEEL

**Vibe/positioning:** Crisp Operator. Enterprise-credible, founder-friendly. Generous whitespace, 4px spacing rhythm, 1280px max container, 4px border-radius. Not playful, not corporate-stiff.

**Color palette (locked from design session):**
- Navy `#1A3A5C` — primary text, CTA panels, buttons
- Cobalt `#4A90D9` — hover/focus accents, card borders
- Slate `#64748B` — secondary text, footer
- Accent (green) `#22C55E` — primary CTAs, success states, pulse dot
- Surface `#FFFFFF` — cards, nav background
- Bg `#F8FAFC` — page background

**Typography:**
- Headings: Inter, weights 600/700, tight tracking
- Body: IBM Plex Sans, weights 400/500/600
- Both loaded via `next/font/google` with CSS variables

**Spacing/layout:** Vertical sections are `py-20`. Hero is `pt-20 pb-24`. Grids use Tailwind responsive breakpoints (`sm:grid-cols-2 lg:grid-cols-3`). Cards are white with `border-gray-100`, lift to `border-cobalt/30` and `shadow-sm` on hover.

**Iconography:** Inline SVG only — checkmarks in pricing, hamburger/close in mobile nav, chevron in FAQ. No icon library dependency.

**Imagery:** None on this page. Pure typographic + UI-component composition. The product screenshot/hero illustration is deliberately omitted because no real product exists yet — invented mockups would be dishonest.

**Motion:** One animation — the pulsing green dot in the hero "Early access" badge (`animate-pulse`). FAQ chevron rotates 180° on open. Mobile nav fades via conditional render. No scroll animations, no parallax.

### Screens (sections), top-to-bottom:

**1. Nav (sticky)** — White/90 backdrop-blur, 64px tall, border-b gray-100. Left: wordmark "Uncle Inc." in Inter bold navy. Right (md+): Features, Pricing, FAQ links in slate, then green "Join Waitlist" pill button. Mobile: hamburger toggles a stacked link panel below.

**2. Hero** — Centered, max-w-4xl. Top: green-pill badge with pulsing dot + "Early access — join the waitlist". H1: "Validate Your Startup Idea Before You Build It" (4xl → 6xl responsive). Sub: slate body copy, max-w-2xl. Two buttons stacked on mobile, side-by-side on sm+: green primary "Join the Waitlist", outlined navy "See How It Works". Below buttons: muted "Free to start · No credit card required".

**3. Features (`#features`)** — Section header (centered h2 + slate sub), then 3×2 grid of 6 feature cards. Each card: emoji icon (2xl), navy h3, slate body copy, white bg, gray-100 border, hover lifts to cobalt border + soft shadow.

**4. Pricing (`#pricing`)** — Section header, then 3-column tier grid (max-w-5xl). Tiers: Explorer `$0`, Builder `$29` (highlighted with green ring + "Most Popular" pill), Team `$79`. Each card: tier name, large price, description, checkmark feature list, full-width CTA button. Popular card uses navy ring + accent button; others use plain navy button.

**5. FAQ (`#faq`)** — max-w-3xl centered. Six accordion items (border-gray-100 rows). Question button shows navy semibold text + chevron that rotates on open. Answer slides in below with slate body copy. One item open at a time.

**6. CTA (`#waitlist`)** — Navy background rounded-2xl panel, centered. White h2 "Stop Guessing. Start Validating.", gray-300 sub. Email form: white/10 input with white/20 border + green submit button. On submit (client-side only): swaps form for green success toast with checkmark.

**7. Footer** — border-t gray-100, max-w-7xl. Left: "© 2026 Uncle Inc. All rights reserved." Right: Privacy / Terms / Contact (mailto) links in slate.

## 4. USER FLOWS

**Flow A — Primary conversion (the only flow that matters for this build):**
1. Land → see hero H1 + green CTA within 1 viewport.
2. Click "Join the Waitlist" → smooth-scrolls to `#waitlist` section (native anchor behavior).
3. Enter email → client-side `setEmail` updates state.
4. Submit → `e.preventDefault()` → `setSubmitted(true)` → form swaps for green success message "You're on the list! We'll be in touch soon."
5. State persists in component memory only — no persistence, no analytics, no backend call. (Honest: the page does not currently POST anywhere; a future iteration can wire it to an API route or Supabase table.)

**Flow B — Scrolling discovery:**
1. Land → scroll past hero.
2. Hit Features → read 6 cards.
3. Hit Pricing → compare 3 tiers, click "Join Waitlist" on Builder/Team → anchor-scroll to waitlist.
4. Hit FAQ → expand 1–6 items to evaluate trust.
5. Hit CTA panel → convert.

**Flow C — Mobile:**
1. Land on narrow viewport → nav collapses to hamburger.
2. Tap hamburger → mobile menu reveals 3 links + green CTA button stacked.
3. Tap any link → menu closes (state flips), browser scrolls to anchor.

**States:**
- Nav: closed (default) | mobile open.
- FAQ: closed (all) | one item open at a time (null-indexed state).
- CTA form: idle | submitted (success view).

## 5. PAGES / ROUTES

The shipped product is a **single route**: `/`.

- `/` (`app/page.tsx`) — assembles Nav → Hero → Features → Pricing → FAQ → CTA → Footer in order.

The nav and footer link to `#features`, `#pricing`, `#faq`, `#waitlist` (all in-page anchors) plus `/privacy`, `/terms`, and `mailto:hello@uncleinc.com`. These secondary links are honest placeholders — they point to URLs that don't yet exist. Per the honesty rule: no fake pages, no invented content. The links are present because the footer needs them; clicking them will 404 until those routes are authored in a future iteration. They are not part of this build's acceptance criteria.

## 6. CORE FEATURES

The "features" here are the marketing page's interactive elements — each is a real, working piece of UI:

1. **Sticky responsive navigation** — Stays pinned on scroll (`sticky top-0 z-50`), blurs the page beneath (`backdrop-blur`), collapses to a hamburger menu below `md`. Hamburger icon swaps to an X when open (`useState`). Mobile menu closes implicitly via link click + state toggle.

2. **Anchor-scroll CTAs** — All primary CTAs (`#waitlist`) and nav links (`#features`, `#pricing`, `#faq`) use native `href="#section"` for smooth scroll. No JS scroll library.

3. **Feature grid with hover lift** — 6 cards rendered from a `FEATURES` array. Hover state: `border-cobalt/30` + `shadow-sm` + 150ms transition. Pure CSS, no JS.

4. **Pricing tier cards** — 3 tiers rendered from a `TIERS` array. The `popular: true` tier gets a green ring (`ring-accent/20`), a "Most Popular" pill at the top, and the green primary button instead of navy. Checkmarks rendered as inline SVG.

5. **FAQ accordion** — 6 items rendered from `FAQS` array. Single-open behavior via `useState<number | null>`. Clicking an open item closes it. Chevron SVG rotates 180° via Tailwind `transition-transform`.

6. **Waitlist email capture (client-side only)** — Controlled input + form. On submit: prevent default, set submitted state, swap to success view with checkmark SVG. No fetch, no API route, no persistence — honest about current scope.

## 7. DATA MODEL

There is no backend, no database, no API in this build. All "data" is static arrays co-located in components:

- `FEATURES` (`components/Features.tsx`) — `{ icon: string, title: string, desc: string }[]`, length 6.
- `TIERS` (`components/Pricing.tsx`) — `{ name: string, price: string, period: string, desc: string, features: string[], cta: string, popular: boolean }[]`, length 3.
- `FAQS` (`components/FAQ.tsx`) — `{ q: string, a: string }[]`, length 6.

Component-local state:
- `Nav` — `open: boolean` (mobile menu).
- `FAQ` — `open: number | null` (which item is expanded).
- `CTA` — `email: string`, `submitted: boolean`.

## 8. AUTH

**None.** This is a public marketing landing page. No sign-up, no login, no protected routes. The "Join the Waitlist" form is a client-side email capture stub — it does not currently POST to any backend. Adding real persistence (e.g., a Supabase `waitlist` table) is a future iteration and explicitly out of scope for this 15-file build.

## 9. FILES

All 15 files are listed below. The package already specifies exact contents for each — I'm restating the tree with one-line purposes for the coding agent:

```
package.json                              # Next.js 14 + React 18 + Tailwind deps, dev/build/start scripts
next.config.js                            # Empty NextConfig stub
tsconfig.json                             # TS strict mode, @/* path alias, Next plugin
tailwind.config.ts                        # Custom color palette (navy/cobalt/slate/accent), Inter+IBM Plex font families
postcss.config.js                         # Tailwind + autoprefixer pipeline
app/globals.css                           # Tailwind directives + IBM Plex Sans body font
app/layout.tsx                            # Root layout: Inter + IBM Plex Sans fonts, metadata, navy-on-bg body
app/page.tsx                              # Home route assembling Nav + Hero + Features + Pricing + FAQ + CTA + Footer
components/Nav.tsx                        # Sticky responsive nav with mobile hamburger toggle
components/Hero.tsx                       # H1, sub, dual CTA, pulse-dot early-access badge
components/Features.tsx                   # 6-card feature grid from FEATURES array
components/Pricing.tsx                    # 3-tier pricing cards, Builder highlighted as Most Popular
components/FAQ.tsx                        # 6-item accordion with single-open state
components/CTA.tsx                        # Navy waitlist panel with client-side email form + success state
components/Footer.tsx                     # Copyright + Privacy/Terms/Contact links
```

## 10. ACCEPTANCE

- [ ] `npm install && npm run dev` starts the server with zero errors.
- [ ] `npm run build` completes with zero TypeScript or ESLint errors.
- [ ] `/` renders all 7 sections in order: Nav, Hero, Features, Pricing, FAQ, CTA, Footer.
- [ ] Sticky nav stays pinned on scroll, blurs the page beneath it.
- [ ] Mobile (<768px): nav collapses to a hamburger; tapping it opens a stacked link panel; X icon closes it.
- [ ] Hero shows the green "Early access" pulse-dot badge, the H1, the sub copy, and two CTAs.
- [ ] Clicking any "Join the Waitlist" or nav anchor smooth-scrolls to the target section.
- [ ] Features grid shows 6 cards with emoji icon, title, description; cards lift on hover (border + shadow).
- [ ] Pricing shows 3 tiers; the Builder tier has the green ring, "Most Popular" pill, and green CTA button.
- [ ] FAQ renders 6 collapsed items; clicking one expands its answer and rotates the chevron; opening another closes the first.
- [ ] CTA section is a navy rounded panel with a white h2.
- [ ] Entering an email and submitting the waitlist form swaps the form for a green success message with a checkmark.
- [ ] Footer shows "© 2026 Uncle Inc." and three links.
- [ ] No external image assets, no icon libraries, no auth flows, no backend calls.
- [ ] No invented customer quotes, logos, user counts, ratings, or press mentions anywhere.
- [ ] Lighthouse: no missing-font flashes (fonts loaded via `next/font`), no console errors, all interactive elements keyboard-accessible.

---

**Note on the Pricing file:** The as-specified `TIERS` array in `components/Pricing.tsx` contains a typo on the Team tier description string — a literal `\n` escape sequence appears where a newline or space was intended (line: `desc: "For founding teams moving fast together.",\n    features: [...]`). The coding agent must render this verbatim per the file spec, but should be aware that React will render the `\n` as a literal backslash-n in the rendered text. This is a bug in the provided spec, not an instruction to fix — the file must be written exactly as specified. If the agent has discretion, replacing the escaped sequence with a space is a safe improvement; if writing verbatim, the literal string will appear.

FILES: ["package.json", "next.config.js", "tsconfig.json", "tailwind.config.ts", "postcss.config.js", "app/globals.css", "app/layout.tsx", "app/page.tsx", "components/Nav.tsx", "components/Hero.tsx", "components/Features.tsx", "components/Pricing.tsx", "components/FAQ.tsx", "components/CTA.tsx", "components/Footer.tsx"