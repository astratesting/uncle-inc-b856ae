# Uncle Inc. — Build Plan

## 1. PRODUCT

Uncle Inc. is a single Next.js 14 marketing landing page that introduces an AI-assisted MVP validation platform for first-time and early-stage startup founders. The page exists to convert qualified visitors — founders stuck between idea and build — into a pre-launch waitlist by demonstrating the platform's six core capabilities, transparent pricing, and answering objections in an FAQ. The specific pain addressed is the founder who has an idea but cannot afford the weeks of engineering, the cost of a dev agency, or the risk of building something nobody wants: Uncle promises a no-code path from idea to testable, measurable MVP in days. The marketing site itself must therefore feel decisive, technical, and trustworthy — Crisp Operator archetype — not playful or generic-SaaS.

## 2. WHO IT'S FOR

The ICP is the **non-technical first-time founder** (and the solo technical founder time-poor on design) who has validated the problem informally but has not yet shipped. They are 25–45, read Y Combinator essays, lurk on r/startups, have a Notion doc and maybe a Figma file, and have either failed to launch or watched a previous MVP crater from lack of signal. They are skeptical of vague AI hype and allergic to fake social proof — so the site copy must show concrete features, not invented logos or made-up user counts. This shapes the product:

- **Tone:** confident, plain-spoken, no exclamation marks, no "supercharge your workflow."
- **Density:** moderate — six feature cards and three pricing tiers is enough; padding the page with extra sections dilutes intent.
- **Single primary conversion:** Join Waitlist. One hero CTA, one closing CTA, and a tertiary "See How It Works" link. No secondary funnels.
- **No invented customers:** zero testimonials, zero "trusted by," zero download counts. The brand-board wireframes from the prior session confirm a Crisp Operator aesthetic, so the page reads like a product page from a real company at seed stage, not a YC startup with vapor claims.

## 3. LOOK & FEEL

**Visual system**

- **Archetype:** Crisp Operator — confident whitespace, precise grid, restrained color, type-led hierarchy. No gradients on backgrounds, no glassmorphism, no oversized illustrations.
- **Color palette (in `tailwind.config.ts`):**
  - `navy` `#1A3A5C` — primary, used for the CTA dark section, footer, headings on light.
  - `cobalt` `#4A90D9` — secondary accent, used for the wordmark "Inc." dot, links, the "popular" pricing border, focus rings.
  - `accent` `#22C55E` — single-action accent, used for the Join Waitlist button, the "MOST POPULAR" pill, the check icons in pricing, the active FAQ chevron.
  - `ink` `#0F172A` — body text on light.
  - `slate-500` `#64748B` — secondary text.
  - `border` `#E2E8F0` — dividers, card borders.
  - `surface` `#FFFFFF` — cards.
  - `canvas` `#F8FAFC` — page background sections (alternating with white).
- **Typography:**
  - Headings: **Inter**, weights 600/700, tight tracking (`-0.02em` on h1, `-0.01em` on h2/h3).
  - Body: **IBM Plex Sans**, weight 400/500, `leading-relaxed` (1.625) for body, 1.5 for UI.
  - Numeric/feature labels: Inter 600 uppercase, `text-xs tracking-widest text-slate-500` for the "FEATURES" eyebrow.
  - Loaded via `next/font/google` in `app/layout.tsx` with `subsets: ['latin']` and CSS variables `--font-inter` and `--font-plex`.
- **Spacing & layout:** 4px base unit. Section vertical rhythm `py-20 md:py-28`. Container `max-w-7xl mx-auto px-6 lg:px-8`. 12-column grid on desktop, single column on mobile. Cards use `rounded-md` (4px), `border border-slate-200`, `bg-white`, `p-8`.
- **Iconography:** lucide-react stroke icons only, 1.75px stroke, 20px default, 24px in feature cards, 16px inline. No emoji. The switchboard motif from the prior design session is reserved for the wordmark and a small inline glyph — not used decoratively.
- **Imagery:** none on the marketing page. The brand is carried by typography, color, and the wordmark. (No hero illustration, no stock photo — this signals technical seriousness, not consumer friendliness.)
- **Motion:** minimal. `transition-colors` on buttons and links, `transition-transform` on FAQ chevron rotation, `transition-all duration-200` on card hover (subtle `hover:border-cobalt/40 hover:-translate-y-0.5`). No scroll animations, no parallax, no auto-play anything.

**Screens (single page, sections top → bottom):**

1. **Nav (sticky, `sticky top-0 z-50`, white with `border-b border-slate-200`):** height 64px. Left: wordmark "Uncle Inc." (Inter 600, navy, with a 6px cobalt dot as the period of "Inc"). Right on desktop: three text links — Features, Pricing, FAQ — in `text-sm text-ink/80 hover:text-navy`, 32px gap. Then a primary button "Join Waitlist" — `bg-accent text-white px-4 py-2 rounded-md text-sm font-medium hover:bg-accent/90`. On mobile: links collapse into a hamburger that opens a full-screen sheet with the same three links stacked and the CTA at the bottom.
2. **Hero (`bg-white`, `pt-28 pb-24 md:pt-36 md:pb-32`):** Centered on desktop, max-width 56rem.
   - Eyebrow: `text-xs font-semibold tracking-widest text-cobalt uppercase` reading "FOR FIRST-TIME FOUNDERS".
   - H1: Inter 700, `text-5xl md:text-6xl lg:text-7xl`, `text-navy`, `tracking-tight`, `leading-[1.05]`: "Validate Your Startup Idea Before You Build It."
   - Subhead: IBM Plex Sans 400, `text-lg md:text-xl text-slate-500`, `max-w-2xl mx-auto`, `mt-6`: "Uncle turns your idea into a testable MVP in days, not months. Prototype with AI, run real user tests, and decide what to build next — without writing code or hiring a team."
   - CTA row (`mt-10`): two buttons side-by-side, centered, flex-wrap.
     - Primary: `bg-accent text-white px-6 py-3.5 rounded-md text-base font-semibold hover:bg-accent/90` → "Join the Waitlist".
     - Secondary: `border border-navy/20 text-navy bg-white px-6 py-3.5 rounded-md text-base font-semibold hover:border-navy hover:bg-navy/5` → "See How It Works" (anchors to `#features`).
   - Below CTAs: `mt-5` a single line `text-sm text-slate-500` — "No credit card. Early access invites roll out weekly." Honest, no fake urgency.
3. **Features (`bg-canvas`, `py-20 md:py-28`, id `features`):**
   - Section header centered, `max-w-2xl mx-auto text-center`: eyebrow `text-xs font-semibold tracking-widest text-cobalt uppercase` "WHAT YOU GET", h2 Inter 600 `text-3xl md:text-4xl text-navy` "Everything you need to go from idea to evidence.", sub `mt-3 text-slate-500`.
   - Grid: `mt-14 grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6`.
   - Each card: `bg-white border border-slate-200 rounded-md p-8 hover:border-cobalt/40 transition-all duration-200`. Top: a 44×44 square `bg-navy/5 rounded-md` containing a lucide icon in `text-cobalt`. Then `mt-5` Inter 600 `text-lg text-navy` title, `mt-2` IBM Plex Sans `text-sm text-slate-500 leading-relaxed` two-line description. Six cards in this exact order, each with a distinct lucide icon:
     1. **AI Rapid Prototyping** — `Wand2` — "Describe your idea. Uncle generates a working prototype you can share the same day."
     2. **Built-in User Testing** — `Users` — "Recruit testers from your network or ours. Capture sessions, surveys, and qualitative feedback in one place."
     3. **Launch Analytics** — `BarChart3` — "See where users drop off, what they click, and what they ignore — from day one."
     4. **Guided Validation** — `Compass` — "Follow a step-by-step playbook that tells you what to test, when, and what counts as a signal."
     5. **No Code Required** — `Blocks` — "Build, edit, and ship without touching a codebase. Founders ship. Engineers polish later."
     6. **Iterate with Real Data** — `RefreshCw` — "Replace gut feel with usage data. Decide the next sprint from what real people actually did."
4. **Pricing (`bg-white`, `py-20 md:py-28`, id `pricing`):**
   - Same header pattern: eyebrow "PRICING", h2 "Simple plans. Cancel anytime.", sub.
   - Grid: `mt-12 grid grid-cols-1 md:grid-cols-3 gap-6 max-w-5xl mx-auto`. Each tier card `rounded-md p-8 flex flex-col`. The middle ("Builder") card gets `border-2 border-cobalt` and a `MOST POPULAR` pill (`absolute -top-3 left-1/2 -translate-x-1/2 bg-accent text-white text-xs font-semibold px-3 py-1 rounded-full`) and the card uses `relative`.
   - Card anatomy top→bottom: tier name (Inter 600 `text-base text-slate-500 uppercase tracking-widest`), then price block — `mt-4` Inter 700 `text-5xl text-navy` for the number, `text-base text-slate-500` for "/mo" (or "Free" for Explorer), then a one-line description `mt-2 text-sm text-slate-500`, then a hairline `my-6 border-t border-slate-200`, then a 5-item feature list where each row is a flex with a 16px `Check` lucide icon in `text-accent` and `text-sm text-ink` label, then a button pushed to the bottom with `mt-auto pt-8`.
   - Tiers (kept exactly as the goal specified):
     - **Explorer — Free**: 1 project, AI prototyping (limited runs), 1 active user test, 7-day analytics retention, community support. Button: secondary style "Start Free".
     - **Builder — $29/mo (MOST POPULAR)**: 5 projects, unlimited AI prototyping, 10 active user tests, 90-day analytics, email support, guided validation playbooks. Button: accent primary "Join Waitlist".
     - **Team — $79/mo**: Everything in Builder + unlimited projects, unlimited user tests, 1-year analytics, 3 seats included, priority support, custom domains. Button: navy primary "Join Waitlist".
   - Footnote under grid: `mt-8 text-center text-sm text-slate-500` — "Prices in USD. All plans include a 14-day refund window after launch."
5. **FAQ (`bg-canvas`, `py-20 md:py-28`, id `faq`):**
   - Header: eyebrow "FAQ", h2 "Questions, answered."
   - Container: `max-w-3xl mx-auto mt-12`. List of 6 items, each a row separated by `border-b border-slate-200`. Use `<details>` + `<summary>` for native accessibility, with a custom-styled chevron `Plus` from lucide that rotates 45° when open. Summary is `flex items-center justify-between py-5 cursor-pointer list-none` (with `::-webkit-details-marker { display: none }` CSS reset), question text in Inter 600 `text-base md:text-lg text-navy`, answer in `mt-3 pb-5 text-slate-500 text-sm md:text-base leading-relaxed`. Use `<details name="faq">` so only one is open at a time on browsers that support exclusive accordion (graceful fallback to multi-open elsewhere).
   - The 6 questions and answers:
     1. "What exactly is Uncle?" — "Uncle is an AI-assisted platform that helps founders turn an idea into a testable MVP without writing code. You describe the problem, Uncle helps you build a prototype, recruit testers, collect feedback, and decide what to ship next."
     2. "Do I need to know how to code?" — "No. Uncle is built for non-technical founders. If you can write a clear problem statement, you can use Uncle. Engineers can still get involved later through exports and APIs."
     3. "How is this different from a no-code tool like Bubble or Webflow?" — "Those tools help you build. Uncle helps you decide whether to build. The focus is on validation — prototypes, user tests, and real usage data — before you commit to a full product."
     4. "What does 'AI-assisted' actually mean here?" — "Uncle uses AI to draft prototypes from your problem description, suggest test scripts, summarize user feedback, and highlight patterns in your analytics. You stay in control of every decision."
     5. "When can I start using it?" — "Uncle is in private beta. Joining the waitlist puts you in line for an invite — early access rolls out in small batches so we can give every founder real attention."
     6. "Can I cancel or change plans later?" — "Yes. You can upgrade, downgrade, or cancel at any time. After public launch, every plan includes a 14-day refund window."
6. **CTA (`bg-navy`, `py-20 md:py-28`):**
   - Centered, `max-w-2xl mx-auto text-center`. H2 Inter 600 `text-3xl md:text-4xl text-white` "Ready to stop guessing?" (honest — not "Ready to launch in 30 seconds?"). Sub `mt-4 text-base md:text-lg text-white/70` "Join the Uncle waitlist. We'll email you when it's your turn."
   - Form `mt-8`: a single horizontal flex on desktop, stacked on mobile. `flex flex-col sm:flex-row gap-3 max-w-md mx-auto`.
     - Email input: `flex-1 px-4 py-3.5 rounded-md bg-white text-ink placeholder:text-slate-400 focus:outline-none focus:ring-2 focus:ring-accent`, `type="email" required`, placeholder "you@startup.com".
     - Submit: `bg-accent text-white px-6 py-3.5 rounded-md font-semibold hover:bg-accent/90` "Join Waitlist".
   - Microcopy `mt-4 text-sm text-white/60` "We email sparingly. Unsubscribe in one click."
   - On submit, the form posts to `/api/waitlist` (POST) which returns `{ ok: true }`; the client swaps the form for a confirmation `<p class="text-white">You're on the list. We'll be in touch.</p>` and persists nothing in localStorage (single-use confirmation only).
7. **Footer (`bg-navy border-t border-white/10`, `py-10`):**
   - `max-w-7xl mx-auto px-6 lg:px-8 flex flex-col md:flex-row items-center justify-between gap-4`.
   - Left: wordmark "Uncle Inc." in white, Inter 600.
   - Right: link row `flex gap-6 text-sm text-white/70 hover:text-white` — "Privacy" (anchor to `#` — no real page yet, honest placeholder), "Terms" (same), and a `text-white/50` "© 2026 Uncle Inc.".
   - On mobile: stacked, centered.

## 4. USER FLOWS

The site is a single-page marketing surface, so flows are short and explicit:

**Flow A — Primary conversion (Join Waitlist)**
1. Visitor lands from any source → sees Hero with H1, subhead, and two CTAs.
2. Scrolls (or clicks "See How It Works" which smooth-scrolls to `#features`).
3. Reviews six feature cards → scrolls to Pricing → reviews three tiers.
4. Hovers FAQ items, expands one or two to check objection handling.
5. Reaches dark CTA section. Types email → clicks "Join Waitlist".
6. Client-side: `e.preventDefault()`, POST `/api/waitlist` with `{ email }`.
7. On 200: form is replaced with confirmation text; email input is cleared from DOM.
8. On 400 (validation): input border turns red via `aria-invalid` + `border-red-400`, helper text "Enter a valid email" appears under the input.
9. On 500/network: form stays, button text becomes "Try again", and a small `<p class="text-amber-300 text-sm mt-2">Something went wrong. Try again in a moment.</p>` appears.

States: idle → submitting (button disabled, label "Joining…", `opacity-70 cursor-not-allowed`) → success | error.

**Flow B — Sticky nav shortcut**
1. User on any section clicks "Pricing" in the nav → smooth scroll to `#pricing` (using `scroll-behavior: smooth` on `html` and `scroll-margin-top: 80px` on each section to clear the sticky nav).
2. Same for "Features" → `#features` and "FAQ" → `#faq`.

**Flow C — Mobile menu**
1. On `< md`, hamburger button appears top-right.
2. Tap → full-height fixed sheet slides in (`fixed inset-0 bg-white z-50`), nav links stacked vertically with large tap targets (py-4), close button top-right, "Join Waitlist" button at bottom (`mt-auto`).
3. Tap a link → close sheet + smooth-scroll to anchor.

**Flow D — FAQ accordion**
1. Tap summary → `<details>` toggles open. Chevron rotates 45°. Only one open at a time via shared `name="faq"` attribute (with progressive enhancement).
2. On mobile, tapping a link in the sticky nav that resolves to the FAQ section will auto-close the mobile menu first.

## 5. PAGES / ROUTES

| Route | Purpose | Layout & main UI elements |
|---|---|---|
| `/` | The marketing landing page. The only user-facing page. | `<Nav />` sticky → `<Hero />` → `<Features />` → `<Pricing />` → `<FAQ />` → `<CTA />` → `<Footer />`. Sectioned by id for in-page anchors. |
| `/api/waitlist` | POST endpoint to accept waitlist emails. | Route handler: validates `email` (zod or simple regex), inserts into Supabase table `waitlist` (columns: `id`, `email`, `created_at`), returns `{ ok: true }` on success or `{ ok: false, error }` on failure. If Supabase env vars are not configured, falls back to logging the email to the server console and returning `{ ok: true }` so the UI works in any environment — the form must never feel broken to a visitor. |
| `/_not-used` | — | No dashboard, no /login, no /signup, no /app. The product goal is explicitly a marketing landing page; building an authenticated app is out of scope and would be vapor. |

## 6. CORE FEATURES

These are the features the marketing page *describes and demonstrates*. None of them require a live backend to be honest on the page — they describe what the platform does, not what this site does.

1. **AI Rapid Prototyping** (described in card 1) — Uncle generates a working prototype from a problem description. On the marketing page, this is communicated by the card copy, the H1 promise, and the `Wand2` icon. No interactive demo on the marketing page (would feel gimmicky and require backend).
2. **Built-in User Testing** (card 2) — Capture sessions, surveys, and feedback in one place. Card-only; no in-page demo.
3. **Launch Analytics** (card 3) — Drop-off, click, and ignore reporting from day one. Card-only.
4. **Guided Validation** (card 4) — Step-by-step playbook telling founders what to test, when, and what counts as signal. Card-only.
5. **No Code Required** (card 5) — Build, edit, and ship without a codebase. Reinforced in the Hero subhead.
6. **Iterate with Real Data** (card 6) — Replace gut feel with usage data. Card-only.
7. **Pricing transparency** (Pricing section) — three concrete tiers, real prices, real per-tier limits, one "Most Popular" call-out. No "Contact us" hidden tier. The middle tier uses a `border-cobalt` outline so the eye lands there; the accent pill above the card labels the choice for skimmers.
8. **FAQ objection handling** (FAQ section) — six questions covering what it is, who it's for, how it differs from no-code tools, what "AI-assisted" means, when users can start, and billing terms. Each answer is plain, specific, and avoids marketing puffery.
9. **Email waitlist capture** (CTA section) — single email input, primary action. Posts to `/api/waitlist`. Client-side validation, loading state, success state, error state. Disabled state on submit to prevent double-submit. Honeypot hidden field (`<input name="company" tabIndex={-1} className="hidden" />`) — if filled, the request is silently accepted but not stored.
10. **Sticky navigation with in-page anchors** — `Features`, `Pricing`, `FAQ` smooth-scroll to their sections. Mobile hamburger sheet.
11. **Honest copy & no fake social proof** — explicitly no testimonials, no customer logos, no download counts, no "as seen in" press mentions, no star ratings. The brand-board wireframes confirm this is intentional; building these in would be both dishonest and off-archetype.

## 7. DATA MODEL

The only data the marketing site itself owns is the waitlist capture. There is no user account system on this site (out of scope).

**Table: `waitlist`** (Supabase Postgres)
| Field | Type | Constraints | Notes |
|---|---|---|---|
| `id` | `uuid` | PK, default `gen_random_uuid()` | |
| `email` | `text` | NOT NULL, UNIQUE, lowercased before insert, regex `^[^\s@]+@[^\s@]+\.[^\s@]+$` | Normalize on insert: `email.trim().toLowerCase()`. On conflict, no-op. |
| `created_at` | `timestamptz` | NOT NULL, default `now()` | |
| `source` | `text` | nullable | Optional `referer` header or UTM param. Default `null`. |

**Environment variables** (read in the route handler, never exposed to the client):
- `SUPABASE_URL`
- `SUPABASE_SERVICE_ROLE_KEY`
- `WAITLIST_FALLBACK_LOG_ONLY` (optional, default `true` — if Supabase env vars are missing, log to console and return `ok: true`)

**Client state (transient only):**
- `formState`: `'idle' | 'submitting' | 'success' | 'error'`
- `errorMessage`: `string | null`

No localStorage, no cookies, no analytics SDK embedded (intentional — the page is honest about not yet having traffic to measure). A `<Script>` for a privacy-respecting counter (e.g., Plausible) is **not** added; this is a brand decision and out of scope here.

## 8. AUTH

**No authentication is implemented on this site.** The product goal is a marketing landing page; adding `/login`, `/signup`, or any auth UI would be scope creep and visually inconsistent with the Crisp Operator archetype (which is honest about pre-launch state). The waitlist form is anonymous email capture only. Supabase Auth is **not** wired up here. If a future iteration adds an authenticated dashboard, the recommended path is Supabase Auth with email+password and magic-link (no Google/GitHub buttons until real OAuth credentials are provisioned) — but that is explicitly **not** in this build.

## 9. FILES

Concrete file tree, each with its purpose:

- `package.json` — declares Next.js 14 (`next@14.2.x`), React 18, TypeScript 5, Tailwind 3, PostCSS, Autoprefixer, lucide-react, and (only if using Supabase) `@supabase/supabase-js`. Scripts: `dev`, `build`, `start`, `lint`.
- `next.config.js` — minimal config; no experimental flags; `reactStrictMode: true`.
- `tsconfig.json` — Next.js standard, `"strict": true`, `"moduleResolution": "bundler"`, path alias `@/*` → `./*`.
- `tailwind.config.ts` — extends colors (`navy`, `cobalt`, `accent`, `ink`, `canvas`), `fontFamily` (`sans: ['var(--font-inter)', 'system-ui', 'sans-serif']`, `plex: ['var(--font-plex)', ...]`, `mono: ['var(--font-mono)', ...]` — though mono is loaded for completeness per the design tokens), `borderRadius` defaults, content globs `./app/**/*.{ts,tsx}` and `./components/**/*.{ts,tsx}`.
- `postcss.config.js` — `tailwindcss` + `autoprefixer`.
- `app/globals.css` — Tailwind `@tailwind base/components/utilities`; resets `details > summary { list-style: none }` and `details > summary::-webkit-details-marker { display: none }`; sets `html { scroll-behavior: smooth }`; sets `section[id] { scroll-margin-top: 80px }`; defines focus-visible ring utility `@layer utilities { .focus-ring { @apply focus-visible:outline-none focus-visible:ring-2 focus-visible:ring-cobalt focus-visible:ring-offset-2 } }`.
- `app/layout.tsx` — root layout. Loads Inter via `next/font/google` (variable `--font-inter`, weight array `['400','500','600','700']`), IBM Plex Sans via `next/font/google` (variable `--font-plex`, weights `['400','500']`). Sets `metadata`: `title: { default: "Uncle Inc. — Validate Your Startup Idea", template: "%s · Uncle Inc." }`, `description: "An AI-assisted MVP platform that helps founders go from idea to testable prototype — without writing code."`, `openGraph` with title/description/type/URL, `twitter: { card: "summary", title, description }`, `robots: { index: true, follow: true }`. Body: `className={`${inter.variable} ${plex.variable} font-plex bg-white text-ink antialiased`}`. Wraps children in a single `<div className="min-h-screen flex flex-col">` so the footer can stick to the bottom of short viewports.
- `app/page.tsx` — server component that imports and renders `<Nav />`, `<main>` containing `<Hero />`, `<Features />`, `<Pricing />`, `<FAQ />`, `<CTA />`, and `<Footer />`. Exports `metadata` overrides for the homepage (`title: "Uncle Inc. — Validate Your Startup Idea Before You Build It"`).
- `app/api/waitlist/route.ts` — POST handler. Validates email, attempts Supabase insert if env vars are present, otherwise logs to console. Always returns 200 `{ ok: true }` to the client unless validation fails (400). Sets `Cache-Control: no-store`.
- `components/Nav.tsx` — client component (uses `useState` for mobile menu). Sticky header, wordmark, three anchor links, "Join Waitlist" button (anchor to `#waitlist`). Mobile hamburger with full-screen sheet.
- `components/Hero.tsx` — server component. Eyebrow, H1, subhead, two CTAs (primary = anchor to `#waitlist`, secondary = anchor to `#features`).
- `components/Features.tsx` — server component. Section wrapper with id and header, then a 3×2 grid of `FeatureCard` items (defined inline or as a local sub-component in the same file).
- `components/Pricing.tsx` — server component. Section with header and 3-column grid of `TierCard` items. Middle card has `relative` + `border-2 border-cobalt` + `MOST POPULAR` pill.
- `components/FAQ.tsx` — client component (uses `<details>` natively; no state needed). Renders the 6-item list with lucide `Plus` chevron rotated via `[&[open]>summary_svg]:rotate-45` Tailwind arbitrary variant.
- `components/CTA.tsx` — client component (form state). Email input, submit button, honeypot field. Handles submit → POST → swap to success message.
- `components/Footer.tsx` — server component. Wordmark, Privacy/Terms anchors, copyright.
- `lib/supabase.ts` — optional. Exports a `getSupabaseAdmin()` factory that returns a Supabase client using `SUPABASE_URL` and `SUPABASE_SERVICE_ROLE_KEY` if both are set, otherwise returns `null`. Imported by the route handler.
- `lib/validate.ts` — exports `isValidEmail(value: string): boolean` (single regex, used in both client and server).
- `.env.example` — documents `SUPABASE_URL` and `SUPABASE_SERVICE_ROLE_KEY` as optional. Includes a comment that the site works without them (fallback log-only mode).
- `README.md` — one paragraph: what Uncle is, `npm install` / `npm run dev` / `npm run build`, link to the optional env vars, and a note that there are no fake metrics on the page by design.

## 10. ACCEPTANCE

The build is "done and working" when every item below is true:

- [ ] `npm install && npm run dev` starts the site on `http://localhost:3000` with no console errors and no TypeScript errors.
- [ ] `npm run build` completes successfully (production build).
- [ ] `app/page.tsx` renders the seven sections in order: Nav, Hero, Features, Pricing, FAQ, CTA, Footer.
- [ ] Tailwind config defines `navy` (`#1A3A5C`), `cobalt` (`#4A90D9`), `accent` (`#22C55E`), `ink`, and `canvas` and these are used in components — no raw hex strings in JSX.
- [ ] `app/layout.tsx` loads Inter and IBM Plex Sans via `next/font/google` and applies them via CSS variables; heading text is in Inter, body in IBM Plex Sans (visually verifiable).
- [ ] The Hero H1 reads exactly "Validate Your Startup Idea Before You Build It" and the subhead references the AI-assisted MVP platform.
- [ ] Hero has exactly two CTA buttons: a primary accent "Join the Waitlist" (anchors to `#waitlist`) and a secondary outlined "See How It Works" (anchors to `#features`).
- [ ] Features section has exactly six cards with the specified titles in the specified order, each with a lucide icon, a one-line description, and the navy/cobalt/white treatment.
- [ ] Pricing section has exactly three tiers with the exact names, prices, and "MOST POPULAR" treatment on Builder.
- [ ] FAQ section has exactly six items, each expandable, with the specified questions and answers.
- [ ] CTA section is `bg-navy`, has an email input, a "Join Waitlist" submit button, and confirmation behavior: submitting swaps the form for a success message; invalid email shows a red border + helper text; server error keeps the form and shows a "Try again" hint.
- [ ] `/api/waitlist` returns 200 `{ ok: true }` for a valid email in fallback log-only mode (no Supabase env vars) and 400 for an invalid email.
- [ ] Nav is sticky at the top, has the wordmark, the three in-page links, and a "Join Waitlist" button. On `< md` viewports, a hamburger opens a full-screen sheet with the same items.
- [ ] Footer shows "© 2026 Uncle Inc." and Privacy / Terms anchor links.
- [ ] There are **no** fake testimonials, no customer logos, no download counts, no "as seen in" press lines, no star ratings anywhere on the page.
- [ ] The site is responsive at 360px, 768px, 1024px, and 1440px widths with no horizontal scroll.
- [ ] Lighthouse Best Practices score ≥ 90 on a production build (no broken images, valid `<html lang>`, `<button>` for buttons, `<a>` for links, sufficient color contrast on navy/white and accent/white pairs).
- [ ] Focus rings are visible on keyboard tab through all interactive elements.
- [ ] `prefers-reduced-motion: reduce` disables smooth scroll (handled in `globals.css` with `@media (prefers-reduced-motion: reduce) { html { scroll-behavior: auto } }`).

FILES: ["package.json", "next.config.js", "tsconfig.json", "tailwind.config.ts", "postcss.config.js", "app/globals.css", "app/layout.tsx", "app/page.tsx", "app/api/waitlist/route.ts", "components/Nav.tsx", "components/Hero.tsx", "components/Features.tsx", "components/Pricing.tsx", "components/FAQ.tsx", "components/CTA.tsx", "components/Footer.tsx", "lib/supabase.ts", "lib/validate.ts", ".env.example", "README.md"]# Uncle Inc. — Build Plan

## 1. PRODUCT

Uncle Inc. is a single Next.js 14 marketing landing page that introduces an AI-assisted MVP validation platform for first-time and early-stage startup founders. The page exists to convert qualified visitors — founders stuck between idea and build — into a pre-launch waitlist by demonstrating the platform's six core capabilities, transparent pricing, and answering objections in an FAQ. The specific pain addressed is the founder who has an idea but cannot afford the weeks of engineering, the cost of a dev agency, or the risk of building something nobody wants: Uncle promises a no-code path from idea to testable, measurable MVP in days. The marketing site itself must therefore feel decisive, technical, and trustworthy — Crisp Operator archetype — not playful or generic-SaaS.

## 2. WHO IT'S FOR

The ICP is the **non-technical first-time founder** (and the solo technical founder time-poor on design) who has validated the problem informally but has not yet shipped. They are 25–45, read Y Combinator essays, lurk on r/startups, have a Notion doc and maybe a Figma file, and have either failed to launch or watched a previous MVP crater from lack of signal. They are skeptical of vague AI hype and allergic to fake social proof — so the site copy must show concrete features, not invented logos or made-up user counts. This shapes the product:

- **Tone:** confident, plain-spoken, no exclamation marks, no "supercharge your workflow."
- **Density:** moderate — six feature cards and three pricing tiers is enough; padding the page with extra sections dilutes intent.
- **Single primary conversion:** Join Waitlist. One hero CTA, one closing CTA, and a tertiary "See How It Works" link. No secondary funnels.
- **No invented customers:** zero testimonials, zero "trusted by," zero download counts. The brand-board wireframes from the prior session confirm a Crisp Operator aesthetic, so the page reads like a product page from a real company at seed stage, not a YC startup with vapor claims.

## 3. LOOK & FEEL

**Visual system**

- **Archetype:** Crisp Operator — confident whitespace, precise grid, restrained color, type-led hierarchy. No gradients on backgrounds, no glassmorphism, no oversized illustrations.
- **Color palette (in `tailwind.config.ts`):**
  - `navy` `#1A3A5C` — primary, used for the CTA dark section, footer, headings on light.
  - `cobalt` `#4A90D9` — secondary accent, used for the wordmark "Inc." dot, links, the "popular" pricing border, focus rings.
  - `accent` `#22C55E` — single-action accent, used for the Join Waitlist button, the "MOST POPULAR" pill, the check icons in pricing, the active FAQ chevron.
  - `ink` `#0F172A` — body text on light.
  - `slate-500` `#64748B` — secondary text.
  - `border` `#E2E8F0` — dividers, card borders.
  - `surface` `#FFFFFF` — cards.
  - `canvas` `#F8FAFC` — page background sections (alternating with white).
- **Typography:**
  - Headings: **Inter**, weights 600/700, tight tracking (`-0.02em` on h1, `-0.01em` on h2/h3).
  - Body: **IBM Plex Sans**, weight 400/500, `leading-relaxed` (1.625) for body, 1.5 for UI.
  - Numeric/feature labels: Inter 600 uppercase, `text-xs tracking-widest text-slate-500` for the "FEATURES" eyebrow.
  - Loaded via `next/font/google` in `app/layout.tsx` with `subsets: ['latin']` and CSS variables `--font-inter` and `--font-plex`.
- **Spacing & layout:** 4px base unit. Section vertical rhythm `py-20 md:py-28`. Container `max-w-7xl mx-auto px-6 lg:px-8`. 12-column grid on desktop, single column on mobile. Cards use `rounded-md` (4px), `border border-slate-200`, `bg-white`, `p-8`.
- **Iconography:** lucide-react stroke icons only, 1.75px stroke, 20px default, 24px in feature cards, 16px inline. No emoji. The switchboard motif from the prior design session is reserved for the wordmark and a small inline glyph — not used decoratively.
- **Imagery:** none on the marketing page. The brand is carried by typography, color, and the wordmark. (No hero illustration, no stock photo — this signals technical seriousness, not consumer friendliness.)
- **Motion:** minimal. `transition-colors` on buttons and links, `transition-transform` on FAQ chevron rotation, `transition-all duration-200` on card hover (subtle `hover:border-cobalt/40 hover:-translate-y-0.5`). No scroll animations, no parallax, no auto-play anything.

**Screens (single page, sections top → bottom):**

1. **Nav (sticky, `sticky top-0 z-50`, white with `border-b border-slate-200`):** height 64px. Left: wordmark "Uncle Inc." (Inter 600, navy, with a 6px cobalt dot as the period of "Inc"). Right on desktop: three text links — Features, Pricing, FAQ — in `text-sm text-ink/80 hover:text-navy`, 32px gap. Then a primary button "Join Waitlist" — `bg-accent text-white px-4 py-2 rounded-md text-sm font-medium hover:bg-accent/90`. On mobile: links collapse into a hamburger that opens a full-screen sheet with the same three links stacked and the CTA at the bottom.
2. **Hero (`bg-white`, `pt-28 pb-24 md:pt-36 md:pb-32`):** Centered on desktop, max-width 56rem.
   - Eyebrow: `text-xs font-semibold tracking-widest text-cobalt uppercase` reading "FOR FIRST-TIME FOUNDERS".
   - H1: Inter 700, `text-5xl md:text-6xl lg:text-7xl`, `text-navy`, `tracking-tight`, `leading-[1.05]`: "Validate Your Startup Idea Before You Build It."
   - Subhead: IBM Plex Sans 400, `text-lg md:text-xl text-slate-500`, `max-w-2xl mx-auto`, `mt-6`: "Uncle turns your idea into a testable MVP in days, not months. Prototype with AI, run real user tests, and decide what to build next — without writing code or hiring a team."
   - CTA row (`mt-10`): two buttons side-by-side, centered, flex-wrap.
     - Primary: `bg-accent text-white px-6 py-3.5 rounded-md text-base font-semibold hover:bg-accent/90` → "Join the Waitlist".
     - Secondary: `border border-navy/20 text-navy bg-white px-6 py-3.5 rounded-md text-base font-semibold hover:border-navy hover:bg-navy/5` → "See How It Works" (anchors to `#features`).
   - Below CTAs: `mt-5` a single line `text-sm text-slate-500` — "No credit card. Early access invites roll out weekly." Honest, no fake urgency.
3. **Features (`bg-canvas`, `py-20 md:py-28`, id `features`):**
   - Section header centered, `max-w-2xl mx-auto text-center`: eyebrow `text-xs font-semibold tracking-widest text-cobalt uppercase` "WHAT YOU GET", h2 Inter 600 `text-3xl md:text-4xl text-navy` "Everything you need to go from idea to evidence.", sub `mt-3 text-slate-500`.
   - Grid: `mt-14 grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6`.
   - Each card: `bg-white border border-slate-200 rounded-md p-8 hover:border-cobalt/40 transition-all duration-200`. Top: a 44×44 square `bg-navy/5 rounded-md` containing a lucide icon in `text-cobalt`. Then `mt-5` Inter 600 `text-lg text-navy` title, `mt-2` IBM Plex Sans `text-sm text-slate-500 leading-relaxed` two-line description. Six cards in this exact order, each with a distinct lucide icon:
     1. **AI Rapid Prototyping** — `Wand2` — "Describe your idea. Uncle generates a working prototype you can share the same day."
     2. **Built-in User Testing** — `Users` — "Recruit testers from your network or ours. Capture sessions, surveys, and qualitative feedback in one place."
     3. **Launch Analytics** — `BarChart3` — "See where users drop off, what they click, and what they ignore — from day one."
     4. **Guided Validation** — `Compass` — "Follow a step-by-step playbook that tells you what to test, when, and what counts as a signal."
     5. **No Code Required** — `Blocks` — "Build, edit, and ship without touching a codebase. Founders ship. Engineers polish later."
     6. **Iterate with Real Data** — `RefreshCw` — "Replace gut feel with usage data. Decide the next sprint from what real people actually did."
4. **Pricing (`bg-white`, `py-20 md:py-28`, id `pricing`):**
   - Same header pattern: eyebrow "PRICING", h2 "Simple plans. Cancel anytime.", sub.
   - Grid: `mt-12 grid grid-cols-1 md:grid-cols-3 gap-6 max-w-5xl mx-auto`. Each tier card `rounded-md p-8 flex flex-col`. The middle ("Builder") card gets `border-2 border-cobalt` and a `MOST POPULAR` pill (`absolute -top-3 left-1/2 -translate-x-1/2 bg-accent text-white text-xs font-semibold px-3 py-1 rounded-full`) and the card uses `relative`.
   - Card anatomy top→bottom: tier name (Inter 600 `text-base text-slate-500 uppercase tracking-widest`), then price block — `mt-4` Inter 700 `text-5xl text-navy` for the number, `text-base text-slate-500` for "/mo" (or "Free" for Explorer), then a one-line description `mt-2 text-sm text-slate-500`, then a hairline `my-6 border-t border-slate-200`, then a 5-item feature list where each row is a flex with a 16px `Check` lucide icon in `text-accent` and `text-sm text-ink` label, then a button pushed to the bottom with `mt-auto pt-8`.
   - Tiers (kept exactly as the goal specified):
     - **Explorer — Free**: 1 project, AI prototyping (limited runs), 1 active user test, 7-day analytics retention, community support. Button: secondary style "Start Free".
     - **Builder — $29/mo (MOST POPULAR)**: 5 projects, unlimited AI prototyping, 10 active user tests, 90-day analytics, email support, guided validation playbooks. Button: accent primary "Join Waitlist".
     - **Team — $79/mo**: Everything in Builder + unlimited projects, unlimited user tests, 1-year analytics, 3 seats included, priority support, custom domains. Button: navy primary "Join Waitlist".
   - Footnote under grid: `mt-8 text-center text-sm text-slate-500` — "Prices in USD. All plans include a 14-day refund window after launch."
5. **FAQ (`bg-canvas`, `py-20 md:py-28`, id `faq`):**
   - Header: eyebrow "FAQ", h2 "Questions, answered."
   - Container: `max-w-3xl mx-auto mt-12`. List of 6 items, each a row separated by `border-b border-slate-200`. Use `<details>` + `<summary>` for native accessibility, with a custom-styled chevron `Plus` from lucide that rotates 45° when open. Summary is `flex items-center justify-between py-5 cursor-pointer list-none` (with `::-webkit-details-marker { display: none }` CSS reset), question text in Inter 600 `text-base md:text-lg text-navy`, answer in `mt-3 pb-5 text-slate-500 text-sm md:text-base leading-relaxed`. Use `<details name="faq">` so only one is open at a time on browsers that support exclusive accordion (graceful fallback to multi-open elsewhere).
   - The 6 questions and answers:
     1. "What exactly is Uncle?" — "Uncle is an AI-assisted platform that helps founders turn an idea into a testable MVP without writing code. You describe the problem, Uncle helps you build a prototype, recruit testers, collect feedback, and decide what to ship next."
     2. "Do I need to know how to code?" — "No. Uncle is built for non-technical founders. If you can write a clear problem statement, you can use Uncle. Engineers can still get involved later through exports and APIs."
     3. "How is this different from a no-code tool like Bubble or Webflow?" — "Those tools help you build. Uncle helps you decide whether to build. The focus is on validation — prototypes, user tests, and real usage data — before you commit to a full product."
     4. "What does 'AI-assisted' actually mean here?" — "Uncle uses AI to draft prototypes from your problem description, suggest test scripts, summarize user feedback, and highlight patterns in your analytics. You stay in control of every decision."
     5. "When can I start using it?" — "Uncle is in private beta. Joining the waitlist puts you in line for an invite — early access rolls out in small batches so we can give every founder real attention."
     6. "Can I cancel or change plans later?" — "Yes. You can upgrade, downgrade, or cancel at any time. After public launch, every plan includes a 14-day refund window."
6. **CTA (`bg-navy`, `py-20 md:py-28`):**
   - Centered, `max-w-2xl mx-auto text-center`. H2 Inter 600 `text-3xl md:text-4xl text-white` "Ready to stop guessing?" (honest — not "Ready to launch in 30 seconds?"). Sub `mt-4 text-base md:text-lg text-white/70` "Join the Uncle waitlist. We'll email you when it's your turn."
   - Form `mt-8`: a single horizontal flex on desktop, stacked on mobile. `flex flex-col sm:flex-row gap-3 max-w-md mx-auto`.
     - Email input: `flex-1 px-4 py-3.5 rounded-md bg-white text-ink placeholder:text-slate-400 focus:outline-none focus:ring-2 focus:ring-accent`, `type="email" required`, placeholder "you@startup.com".
     - Submit: `bg-accent text-white px-6 py-3.5 rounded-md font-semibold hover:bg-accent/90` "Join Waitlist".
   - Microcopy `mt-4 text-sm text-white/60` "We email sparingly. Unsubscribe in one click."
   - On submit, the form posts to `/api/waitlist` (POST) which returns `{ ok: true }`; the client swaps the form for a confirmation `<p class="text-white">You're on the list. We'll be in touch.</p>` and persists nothing in localStorage (single-use confirmation only).
7. **Footer (`bg-navy border-t border-white/10`, `py-10`):**
   - `max-w-7xl mx-auto px-6 lg:px-8 flex flex-col md:flex-row items-center justify-between gap-4`.
   - Left: wordmark "Uncle Inc." in white, Inter 600.
   - Right: link row `flex gap-6 text-sm text-white/70 hover:text-white` — "Privacy" (anchor to `#` — no real page yet, honest placeholder), "Terms" (same), and a `text-white/50` "© 2026 Uncle Inc.".
   - On mobile: stacked, centered.

## 4. USER FLOWS

The site is a single-page marketing surface, so flows are short and explicit:

**Flow A — Primary conversion (Join Waitlist)**
1. Visitor lands from any source → sees Hero with H1, subhead, and two CTAs.
2. Scrolls (or clicks "See How It Works" which smooth-scrolls to `#features`).
3. Reviews six feature cards → scrolls to Pricing → reviews three tiers.
4. Hovers FAQ items, expands one or two to check objection handling.
5. Reaches dark CTA section. Types email → clicks "Join Waitlist".
6. Client-side: `e.preventDefault()`, POST `/api/waitlist` with `{ email }`.
7. On 200: form is replaced with confirmation text; email input is cleared from DOM.
8. On 400 (validation): input border turns red via `aria-invalid` + `border-red-400`, helper text "Enter a valid email" appears under the input.
9. On 500/network: form stays, button text becomes "Try again", and a small `<p class="text-amber-300 text-sm mt-2">Something went wrong. Try again in a moment.</p>` appears.

States: idle → submitting (button disabled, label "Joining…", `opacity-70 cursor-not-allowed`) → success | error.

**Flow B — Sticky nav shortcut**
1. User on any section clicks "Pricing" in the nav → smooth scroll to `#pricing` (using `scroll-behavior: smooth` on `html` and `scroll-margin-top: 80px` on each section to clear the sticky nav).
2. Same for "Features" → `#features` and "FAQ" → `#faq`.

**Flow C — Mobile menu**
1. On `< md`, hamburger button appears top-right.
2. Tap → full-height fixed sheet slides in (`fixed inset-0 bg-white z-50`), nav links stacked vertically with large tap targets (py-4), close button top-right, "Join Waitlist" button at bottom (`mt-auto`).
3. Tap a link → close sheet + smooth-scroll to anchor.

**Flow D — FAQ accordion**
1. Tap summary → `<details>` toggles open. Chevron rotates 45°. Only one open at a time via shared `name="faq"` attribute (with progressive enhancement).
2. On mobile, tapping a link in the sticky nav that resolves to the FAQ section will auto-close the mobile menu first.

## 5. PAGES / ROUTES

| Route | Purpose | Layout & main UI elements |
|---|---|---|
| `/` | The marketing landing page. The only user-facing page. | `<Nav />` sticky → `<Hero />` → `<Features />` → `<Pricing />` → `<FAQ />` → `<CTA />` → `<Footer />`. Sectioned by id for in-page anchors. |
| `/api/waitlist` | POST endpoint to accept waitlist emails. | Route handler: validates `email` (zod or simple regex), inserts into Supabase table `waitlist` (columns: `id`, `email`, `created_at`), returns `{ ok: true }` on success or `{ ok: false, error }` on failure. If Supabase env vars are not configured, falls back to logging the email to the server console and returning `{ ok: true }` so the UI works in any environment — the form must never feel broken to a visitor. |
| `/_not-used` | — | No dashboard, no /login, no /signup, no /app. The product goal is explicitly a marketing landing page; building an authenticated app is out of scope and would be vapor. |

## 6. CORE FEATURES

These are the features the marketing page *describes and demonstrates*. None of them require a live backend to be honest on the page — they describe what the platform does, not what this site does.

1. **AI Rapid Prototyping** (described in card 1) — Uncle generates a working prototype from a problem description. On the marketing page, this is communicated by the card copy, the H1 promise, and the `Wand2` icon. No interactive demo on the marketing page (would feel gimmicky and require backend).
2. **Built-in User Testing** (card 2) — Capture sessions, surveys, and feedback in one place. Card-only; no in-page demo.
3. **Launch Analytics** (card 3) — Drop-off, click, and ignore reporting from day one. Card-only.
4. **Guided Validation** (card 4) — Step-by-step playbook telling founders what to test, when, and what counts as signal. Card-only.
5. **No Code Required** (card 5) — Build, edit, and ship without a codebase. Reinforced in the Hero subhead.
6. **Iterate with Real Data** (card 6) — Replace gut feel with usage data. Card-only.
7. **Pricing transparency** (Pricing section) — three concrete tiers, real prices, real per-tier limits, one "Most Popular" call-out. No "Contact us" hidden tier. The middle tier uses a `border-cobalt` outline so the eye lands there; the accent pill above the card labels the choice for skimmers.
8. **FAQ objection handling** (FAQ section) — six questions covering what it is, who it's for, how it differs from no-code tools, what "AI-assisted" means, when users can start, and billing terms. Each answer is plain, specific, and avoids marketing puffery.
9. **Email waitlist capture** (CTA section) — single email input, primary action. Posts to `/api/waitlist`. Client-side validation, loading state, success state, error state. Disabled state on submit to prevent double-submit. Honeypot hidden field (`<input name="company" tabIndex={-1} className="hidden" />`) — if filled, the request is silently accepted but not stored.
10. **Sticky navigation with in-page anchors** — `Features`, `Pricing`, `FAQ` smooth-scroll to their sections. Mobile hamburger sheet.
11. **Honest copy & no fake social proof** — explicitly no testimonials, no customer logos, no download counts, no "as seen in" press mentions, no star ratings. The brand-board wireframes confirm this is intentional; building these in would be both dishonest and off-archetype.

## 7. DATA MODEL

The only data the marketing site itself owns is the waitlist capture. There is no user account system on this site (out of scope).

**Table: `waitlist`** (Supabase Postgres)
| Field | Type | Constraints | Notes |
|---|---|---|---|
| `id` | `uuid` | PK, default `gen_random_uuid()` | |
| `email` | `text` | NOT NULL, UNIQUE, lowercased before insert, regex `^[^\s@]+@[^\s@]+\.[^\s@]+$` | Normalize on insert: `email.trim().toLowerCase()`. On conflict, no-op. |
| `created_at` | `timestamptz` | NOT NULL, default `now()` | |
| `source` | `text` | nullable | Optional `referer` header or UTM param. Default `null`. |

**Environment variables** (read in the route handler, never exposed to the client):
- `SUPABASE_URL`
- `SUPABASE_SERVICE_ROLE_KEY`
- `WAITLIST_FALLBACK_LOG_ONLY` (optional, default `true` — if Supabase env vars are missing, log to console and return `ok: true`)

**Client state (transient only):**
- `formState`: `'idle' | 'submitting' | 'success' | 'error'`
- `errorMessage`: `string | null`

No localStorage, no cookies, no analytics SDK embedded (intentional — the page is honest about not yet having traffic to measure). A `<Script>` for a privacy-respecting counter (e.g., Plausible) is **not** added; this is a brand decision and out of scope here.

## 8. AUTH

**No authentication is implemented on this site.** The product goal is a marketing landing page; adding `/login`, `/signup`, or any auth UI would be scope creep and visually inconsistent with the Crisp Operator archetype (which is honest about pre-launch state). The waitlist form is anonymous email capture only. Supabase Auth is **not** wired up here. If a future iteration adds an authenticated dashboard, the recommended path is Supabase Auth with email+password and magic-link (no Google/GitHub buttons until real OAuth credentials are provisioned) — but that is explicitly **not** in this build.

## 9. FILES

Concrete file tree, each with its purpose:

- `package.json` — declares Next.js 14 (`next@14.2.x`), React 18, TypeScript 5, Tailwind 3, PostCSS, Autoprefixer, lucide-react, and (only if using Supabase) `@supabase/supabase-js`. Scripts: `dev`, `build`, `start`, `lint`.
- `next.config.js` — minimal config; no experimental flags; `reactStrictMode: true`.
- `tsconfig.json` — Next.js standard, `"strict": true`, `"moduleResolution": "bundler"`, path alias `@/*` → `./*`.
- `tailwind.config.ts` — extends colors (`navy`, `cobalt`, `accent`, `ink`, `canvas`), `fontFamily` (`sans: ['var(--font-inter)', 'system-ui', 'sans-serif']`, `plex: ['var(--font-plex)', ...]`, `mono: ['var(--font-mono)', ...]` — though mono is loaded for completeness per the design tokens), `borderRadius` defaults, content globs `./app/**/*.{ts,tsx}` and `./components/**/*.{ts,tsx}`.
- `postcss.config.js` — `tailwindcss` + `autoprefixer`.
- `app/globals.css` — Tailwind `@tailwind base/components/utilities`; resets `details > summary { list-style: none }` and `details > summary::-webkit-details-marker { display: none }`; sets `html { scroll-behavior: smooth }`; sets `section[id] { scroll-margin-top: 80px }`; defines focus-visible ring utility `@layer utilities { .focus-ring { @apply focus-visible:outline-none focus-visible:ring-2 focus-visible:ring-cobalt focus-visible:ring-offset-2 } }`.
- `app/layout.tsx` — root layout. Loads Inter via `next/font/google` (variable `--font-inter`, weight array `['400','500','600','700']`), IBM Plex Sans via `next/font/google` (variable `--font-plex`, weights `['400','500']`). Sets `metadata`: `title: { default: "Uncle Inc. — Validate Your Startup Idea", template: "%s · Uncle Inc." }`, `description: "An AI-assisted MVP platform that helps founders go from idea to testable prototype — without writing code."`, `openGraph` with title/description/type/URL, `twitter: { card: "summary", title, description }`, `robots: { index: true, follow: true }`. Body: `className={`${inter.variable} ${plex.variable} font-plex bg-white text-ink antialiased`}`. Wraps children in a single `<div className="min-h-screen flex flex-col">` so the footer can stick to the bottom of short viewports.
- `app/page.tsx` — server component that imports and renders `<Nav />`, `<main>` containing `<Hero />`, `<Features />`, `<Pricing />`, `<FAQ />`, `<CTA />`, and `<Footer />`. Exports `metadata` overrides for the homepage (`title: "Uncle Inc. — Validate Your Startup Idea Before You Build It"`).
- `app/api/waitlist/route.ts` — POST handler. Validates email, attempts Supabase insert if env vars are present, otherwise logs to console. Always returns 200 `{ ok: true }` to the client unless validation fails (400). Sets `Cache-Control: no-store`.
- `components/Nav.tsx` — client component (uses `useState` for mobile menu). Sticky header, wordmark, three anchor links, "Join Waitlist" button (anchor to `#waitlist`). Mobile hamburger with full-screen sheet.
- `components/Hero.tsx` — server component. Eyebrow, H1, subhead, two CTAs (primary = anchor to `#waitlist`, secondary = anchor to `#features`).
- `components/Features.tsx` — server component. Section wrapper with id and header, then a 3×2 grid of `FeatureCard` items (defined inline or as a local sub-component in the same file).
- `components/Pricing.tsx` — server component. Section with header and 3-column grid of `TierCard` items. Middle card has `relative` + `border-2 border-cobalt` + `MOST POPULAR` pill.
- `components/FAQ.tsx` — client component (uses `<details>` natively; no state needed). Renders the 6-item list with lucide `Plus` chevron rotated via `[&[open]>summary_svg]:rotate-45` Tailwind arbitrary variant.
- `components/CTA.tsx` — client component (form state). Email input, submit button, honeypot field. Handles submit → POST → swap to success message.
- `components/Footer.tsx` — server component. Wordmark, Privacy/Terms anchors, copyright.
- `lib/supabase.ts` — optional. Exports a `getSupabaseAdmin()` factory that returns a Supabase client using `SUPABASE_URL` and `SUPABASE_SERVICE_ROLE_KEY` if both are set, otherwise returns `null`. Imported by the route handler.
- `lib/validate.ts` — exports `isValidEmail(value: string): boolean` (single regex, used in both client and server).
- `.env.example` — documents `SUPABASE_URL` and `SUPABASE_SERVICE_ROLE_KEY` as optional. Includes a comment that the site works without them (fallback log-only mode).
- `README.md` — one paragraph: what Uncle is, `npm install` / `npm run dev` / `npm run build`, link to the optional env vars, and a note that there are no fake metrics on the page by design.

## 10. ACCEPTANCE

The build is "done and working" when every item below is true:

- [ ] `npm install && npm run dev` starts the site on `http://localhost:3000` with no console errors and no TypeScript errors.
- [ ] `npm run build` completes successfully (production build).
- [ ] `app/page.tsx` renders the seven sections in order: Nav, Hero, Features, Pricing, FAQ, CTA, Footer.
- [ ] Tailwind config defines `navy` (`#1A3A5C`), `cobalt` (`#4A90D9`), `accent` (`#22C55E`), `ink`, and `canvas` and these are used in components — no raw hex strings in JSX.
- [ ] `app/layout.tsx` loads Inter and IBM Plex Sans via `next/font/google` and applies them via CSS variables; heading text is in Inter, body in IBM Plex Sans (visually verifiable).
- [ ] The Hero H1 reads exactly "Validate Your Startup Idea Before You Build It" and the subhead references the AI-assisted MVP platform.
- [ ] Hero has exactly two CTA buttons: a primary accent "Join the Waitlist" (anchors to `#waitlist`) and a secondary outlined "See How It Works" (anchors to `#features`).
- [ ] Features section has exactly six cards with the specified titles in the specified order, each with a lucide icon, a one-line description, and the navy/cobalt/white treatment.
- [ ] Pricing section has exactly three tiers with the exact names, prices, and "MOST POPULAR" treatment on Builder.
- [ ] FAQ section has exactly six items, each expandable, with the specified questions and answers.
- [ ] CTA section is `bg-navy`, has an email input, a "Join Waitlist" submit button, and confirmation behavior: submitting swaps the form for a success message; invalid email shows a red border + helper text; server error keeps the form and shows a "Try again" hint.
- [ ] `/api/waitlist` returns 200 `{ ok: true }` for a valid email in fallback log-only mode (no Supabase env vars) and 400 for an invalid email.
- [ ] Nav is sticky at the top, has the wordmark, the three in-page links, and a "Join Waitlist" button. On `< md` viewports, a hamburger opens a full-screen sheet with the same items.
- [ ] Footer shows "© 2026 Uncle Inc." and Privacy / Terms anchor links.
- [ ] There are **no** fake testimonials, no customer logos, no download counts, no "as seen in" press lines, no star ratings anywhere on the page.
- [ ] The site is responsive at 360px, 768px, 1024px, and 1440px widths with no horizontal scroll.
- [ ] Lighthouse Best Practices score ≥ 90 on a production build (no broken images, valid `<html lang>`, `<button>` for buttons, `<a>` for links, sufficient color contrast on navy/white and accent/white pairs).
- [ ] Focus rings are visible on keyboard tab through all interactive elements.
- [ ] `prefers-reduced-motion: reduce` disables smooth scroll (handled in `globals.css` with `@media (prefers-reduced-motion: reduce) { html { scroll-behavior: auto } }`).

FILES: ["package.json", "next.config.js", "tsconfig.json", "tailwind.config.ts", "postcss.config.js", "app/globals.css", "app/layout.tsx", "app/page.tsx", "app/api/waitlist/route.ts", "components/Nav.tsx", "components/Hero.tsx", "components/Features.tsx", "components/Pricing.tsx", "components/FAQ.tsx", "components/CTA.tsx", "components/Footer.tsx", "lib/supabase.ts", "lib/validate.ts", ".env.example", "README.md"]