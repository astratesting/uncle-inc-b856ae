# Uncle Inc. — Build Plan

## 1. PRODUCT

Uncle Inc. is a single-page marketing site for an AI-assisted MVP development platform aimed at pre-seed and early-stage startup founders. The core value proposition is "validate before you build": founders describe an idea, the platform generates a working prototype, runs lightweight user tests against it, and surfaces real signal (engagement, conversion, qualitative feedback) so the founder can decide whether to keep building, pivot, or kill the idea. The primary user is a non-technical or semi-technical solo founder who has more ideas than time and has been burned by building something nobody wanted. The site exists to convert that visitor into a waitlist signup — there is no app, no dashboard, no auth flow on this build. Every section of the page is engineered to move a skeptical, time-poor founder from "what is this?" to "yes, drop my email."

## 2. WHO IT'S FOR

The ICP is a solo or two-person founder, typically 25–45, technical-adjacent (can read code, may not write production code), with one active idea and a budget under $100/month for tooling. They are skeptical of "AI does everything" hype, allergic to fluff, and respond to concrete mechanics ("here is what the AI does, here is what you get back"). They scan, they don't read. Tone implications for the site: confident, plain-spoken, no exclamation points, no "revolutionary," no invented logos or testimonials. Every claim is a feature description, not a benefit boast. The pricing tiers are concrete dollar amounts because this ICP compares line items, not vibes. The FAQ answers the four objections a founder actually has (do I need to code, what does "AI prototyping" actually produce, is my data safe, can I cancel).

## 3. LOOK & FEEL

**Visual system.** Crisp Operator archetype: enterprise-clean, precise grids, confident whitespace, no decorative gradients, no glassmorphism. The page reads like a serious tool, not a consumer app. Background is near-white (#F8FAFC), surfaces are pure white (#FFFFFF), text is slate-900 (#0F172A) for primary and slate-500 (#64748B) for secondary, borders are slate-200 (#E2E8F0). Brand color usage is disciplined: navy #1A3A5C is reserved for the dark CTA section and the wordmark, cobalt #4A90D9 is the primary interactive color (links, primary buttons, focus rings), green #22C55E is used sparingly as a status accent (the "Popular" badge on Builder, the check icons in pricing, the success state on the waitlist form). No drop shadows on cards — use a 1px border and 4px radius instead. Spacing follows a 4px scale (4, 8, 12, 16, 24, 32, 48, 64, 96). Container max-width 1200px, centered, with 24px horizontal padding on mobile. Typography: Inter for all headings (weights 600, 700), IBM Plex Sans for body and UI (weights 400, 500). H1 is 56px desktop / 36px mobile, H2 is 40px / 28px, H3 is 20px, body is 16px / 1.6 line-height. Iconography is Lucide-style 1.5px stroke line icons, monochrome cobalt on feature cards. No stock photography anywhere — feature cards use icon-in-circle, the hero uses a flat geometric illustration or a clean product mockup placeholder (a bordered rectangle labeled "Prototype preview" with cobalt accent), and the CTA section is solid navy with white text. Motion is minimal and functional: 150ms ease-out on hover for buttons and cards, smooth scroll for in-page anchor links, accordion expand/collapse on FAQ items, no scroll-triggered animations.

**Screen-by-screen layout (top to bottom of the single page).**

**Nav (sticky, 64px tall, white background, 1px bottom border).** Left: Uncle Inc. wordmark (navy "Uncle" + green period dot, Inter 700, 20px). Center (desktop only): three text links — Features, Pricing, FAQ — cobalt on hover, slate-700 default, 14px IBM Plex Sans medium. Right: "Join Waitlist" button, cobalt background, white text, 4px radius, 36px tall, 16px horizontal padding. On scroll past 80px the nav gets a subtle backdrop blur and a slightly stronger bottom border.

**Hero (96px top padding, 96px bottom, white background).** Two-column on desktop (60/40 split), stacked on mobile. Left column: eyebrow text "AI-ASSISTED MVP PLATFORM" in 12px IBM Plex Sans medium, uppercase, letter-spacing 0.1em, cobalt. H1 "Validate Your Startup Idea Before You Build It" in Inter 700, slate-900, 56px desktop / 36px mobile, max-width 560px. Subhead in IBM Plex Sans 18px slate-500, max-width 520px: "Describe your idea. Uncle generates a working prototype, puts it in front of real users, and shows you the signal you need to decide whether to keep building." Two buttons side by side, 12px gap: primary "Join the Waitlist" (cobalt, white text, 48px tall, 24px horizontal padding, 4px radius), secondary "See How It Works" (white background, 1px slate-300 border, slate-900 text, same dimensions, scrolls to #features). Below the buttons, a single line of microcopy in 13px slate-500: "No credit card. Early access opens in waves." Right column: a flat product mockup — a 480×360 white card with 1px slate-200 border, 8px radius, containing a header bar with three traffic-light dots, a centered cobalt-bordered rectangle labeled "Your prototype" in 14px slate-500, and a footer row with three small stat placeholders ("12 users", "4.2 min avg", "67% completion") in 12px IBM Plex Sans. The mockup has no shadow; it sits on the white background and reads as a screenshot.

**Features (id="features", 96px vertical padding, slate-50 background #F8FAFC).** Section header centered: H2 "Everything you need to go from idea to signal" in Inter 700 40px, slate-900, max-width 640px centered. Subhead in 18px slate-500: "Six tools, one workflow. No code required." Below, a 3-column grid on desktop (1 column mobile, 2 column tablet), 24px gap. Six cards, each white, 1px slate-200 border, 4px radius, 32px padding. Card structure: 40×40 cobalt-bordered circle containing a Lucide icon (cobalt stroke), 16px gap, H3 in Inter 600 18px slate-900, 8px gap, body in 15px slate-500 line-height 1.6. The six cards in order: (1) AI Rapid Prototyping — "Describe your idea in plain English. Uncle generates a clickable prototype in minutes, not weeks." (2) Built-in User Testing — "Recruit testers from our network or invite your own. Watch them use your prototype with session replays." (3) Launch Analytics — "See where users drop off, what they click, and how long they stay. No analytics setup required." (4) Guided Validation — "Follow a structured 7-day sprint that tells you exactly what to test and when." (5) No Code Required — "If you can write a tweet, you can use Uncle. Export to code when you're ready." (6) Iterate with Real Data — "Update your prototype based on what users actually do, not what you assume they'll do."

**Pricing (id="pricing", 96px vertical padding, white background).** Section header centered: H2 "Simple pricing, no surprises" in Inter 700 40px. Subhead: "Start free. Upgrade when you're ready to ship." Three-column grid on desktop, stacked on mobile, 24px gap. Each tier is a white card, 1px slate-200 border, 4px radius, 32px padding, 320px min-width. Tier 1 — Explorer, Free: tier name in Inter 600 14px uppercase cobalt letter-spacing 0.1em, "$0" in Inter 700 48px slate-900 with "/mo" in 16px slate-500, one-line description in 14px slate-500, 24px gap, then a feature list with green check icons and 14px slate-700 items: "1 active project", "AI prototype generation", "Up to 10 testers", "Community support", then a full-width "Get Started" button (white, 1px slate-300 border, slate-900 text, 44px tall). Tier 2 — Builder, $29/mo: same structure, but the card has a 2px cobalt border, a green "Most Popular" badge (green background, white text, 12px IBM Plex Sans medium, 4px padding, positioned top-right overlapping the card edge by 8px), and the CTA button is cobalt filled with white text. Features: "5 active projects", "Everything in Explorer", "Up to 100 testers", "Session replays", "Launch analytics", "Email support". Tier 3 — Team, $79/mo: standard border, features: "Unlimited projects", "Everything in Builder", "Unlimited testers", "Team workspaces (up to 5)", "Custom branding on prototypes", "Priority support", white CTA button. Below the grid, centered microcopy in 14px slate-500: "All plans include unlimited prototypes and 7-day data retention. Annual billing saves 20%."

**FAQ (id="faq", 96px vertical padding, slate-50 background).** Section header centered: H2 "Questions founders actually ask" in Inter 700 40px. Below, a single-column list, max-width 720px centered, 12px gap between items. Each item is a white card, 1px slate-200 border, 4px radius. The header row is a button (full width, 56px tall, 20px horizontal padding) with the question text in Inter 600 16px slate-900 on the left and a Lucide chevron-down icon (cobalt, rotates 180deg when open) on the right. The answer panel is conditionally rendered, 20px padding, IBM Plex Sans 15px slate-500 line-height 1.7, with a 1px slate-200 top border separating it from the header. Six items in order: (1) "Do I need to know how to code?" — "No. Uncle is built for founders who think in product, not code. If you can describe what you want users to do, you can use Uncle. When you're ready to ship, you can export your prototype to React or hand it to a developer." (2) "What does the AI actually generate?" — "A clickable, interactive prototype with real navigation, real forms, and real flows — not a static mockup. You can edit anything the AI produces by describing the change in plain English." (3) "How do you get users to test my prototype?" — "You can invite people directly via a share link, or opt into our tester network of early-stage founders and product folks who opt in to try new ideas." (4) "Is my idea safe?" — "Your prototypes are private by default. Only people you explicitly invite can see them. We don't train models on your data, and you can delete everything at any time." (5) "Can I cancel anytime?" — "Yes. Paid plans are month-to-month with no contracts. Cancel from your account settings and you'll keep access until the end of your billing period." (6) "When does Uncle launch?" — "We're opening access in waves starting Q3 2026. Join the waitlist to get early access and locked-in founder pricing."

**CTA section (96px vertical padding, navy #1A3A5C background).** Centered content, max-width 560px. H2 "Stop building in the dark" in Inter 700 40px white. Subhead in 18px IBM Plex Sans, white at 80% opacity: "Join 1,200+ founders on the waitlist. Get early access and founder pricing when we launch." — wait, no invented metrics. Replace with: "Join the waitlist for early access and locked-in founder pricing." Below, a single horizontal form: email input (white background, 1px transparent border, 4px radius, 48px tall, 16px horizontal padding, placeholder "you@startup.com", IBM Plex Sans 16px, flex-grow) + submit button ("Join Waitlist", green #22C55E background, white text, 48px tall, 24px horizontal padding, 4px radius, IBM Plex Sans 600 16px). On mobile the form stacks vertically with 12px gap. Below the form, 13px white-at-60% microcopy: "We'll email you when your spot opens. No spam, ever." The form has three states: idle (as designed), submitting (button shows "Joining…" and is disabled, input is disabled), success (form is replaced by a centered confirmation: green check icon + "You're on the list. We'll be in touch." in white Inter 600 18px). Error state (invalid email) shows a red 13px message below the input: "Please enter a valid email address."

**Footer (64px vertical padding, white background, 1px slate-200 top border).** Two-column layout: left side "© 2026 Uncle Inc. All rights reserved." in 14px slate-500 IBM Plex Sans. Right side: two text links — "Privacy" and "Terms" — in 14px slate-500, cobalt on hover, 24px gap between them. On mobile, stacked and centered.

## 4. USER FLOWS

**Primary flow: visitor → waitlist signup.** Visitor lands on the page (entry point: direct, social share, or search). They see the hero, read the H1 and subhead, scan the two CTAs. They either click "Join the Waitlist" in the nav (smooth-scrolls to the CTA section) or "See How It Works" (smooth-scrolls to Features). If they scroll, they encounter Features (6 cards, ~10 seconds of scanning), then Pricing (3 tiers, comparison), then FAQ (answers objections). At any point they can click "Join the Waitlist" in the nav or scroll to the bottom CTA section. In the CTA section they type an email and submit. Client-side validation checks email format (regex). On valid submit, the form posts to `/api/waitlist` (a Next.js Route Handler), which validates server-side and returns 200. The UI swaps to the success state. No account is created, no auth is required, no redirect happens. The visitor is now on the waitlist.

**Secondary flow: visitor → FAQ answer → waitlist.** Visitor lands, scrolls past hero, opens one or more FAQ items to resolve an objection, then scrolls to the CTA section and signs up. The FAQ accordion uses native `<details>`/`<summary>` for accessibility and zero-JS expand/collapse, with a small client component only for the chevron rotation.

**Tertiary flow: visitor → pricing comparison → waitlist.** Visitor is price-sensitive, scrolls directly to Pricing (via nav anchor), compares the three tiers, decides Builder is the right fit, clicks "Get Started" on Builder. Because there is no app yet, the "Get Started" button on Explorer and Builder scrolls to the CTA section and shows a tooltip-style microcopy under the form: "Early access starts with the waitlist — paid plans unlock at launch." The Team tier's "Get Started" button does the same. This keeps the funnel unified.

**States.** Nav: default, scrolled (backdrop blur + stronger border). CTA button: default, hover (cobalt darkens 10%), focus-visible (2px cobalt ring offset 2px), active (cobalt darkens 15%). FAQ item: closed, open (chevron rotated, answer panel visible). Waitlist form: idle, invalid (red helper text), submitting (button disabled, label changes), success (form replaced by confirmation), error (server returned non-200, red helper text "Something went wrong. Try again.").

## 5. PAGES / ROUTES

This is a single-page marketing site. Routes:

- `/` — the landing page. Renders Nav, Hero, Features, Pricing, FAQ, CTA, Footer in order. This is the only page.
- `/api/waitlist` — POST Route Handler. Accepts `{ email: string }`, validates email format, appends to a waitlist store. For this build, the store is a JSON file at `data/waitlist.json` (no database required, no external service). Returns `{ ok: true }` on success, `{ ok: false, error: "invalid_email" }` on bad input, `{ ok: false, error: "server_error" }` on write failure.

No other routes. No `/dashboard`, no `/login`, no `/signup` — the product is not built yet, and inventing those routes would be dishonest.

## 6. CORE FEATURES

**Feature 1: Sticky navigation with smooth-scroll anchors.** The nav stays fixed at the top of the viewport. Clicking "Features", "Pricing", or "FAQ" smooth-scrolls to the corresponding section id. The "Join Waitlist" button smooth-scrollls to the CTA section. On mobile (<768px), the center links collapse into a hamburger menu that opens a full-width dropdown panel with the same links stacked vertically plus the CTA button at the bottom.

**Feature 2: Hero with dual CTA.** The hero presents the value proposition and two paths: primary action (join waitlist) and secondary action (learn more). Both buttons are keyboard-accessible, have visible focus rings, and the secondary button scrolls to Features.

**Feature 3: Six-card feature grid.** A responsive grid (3 cols desktop, 2 tablet, 1 mobile) of feature cards. Each card has an icon, title, and one-sentence description. Cards have no hover effect beyond a 150ms border-color shift to cobalt — no lift, no shadow.

**Feature 4: Three-tier pricing comparison.** Three pricing cards with a highlighted middle tier. The "Most Popular" badge on Builder uses the green accent. Feature lists use green check icons. All three CTAs route to the waitlist form.

**Feature 5: Expandable FAQ accordion.** Six questions with answers. Uses `<details>`/`<summary>` for native a11y. A small client component handles the chevron rotation animation. Only one item can be open at a time (enforced by giving all items the same `name` attribute, which makes them behave like a radio group in modern browsers — actually, native `<details>` doesn't support exclusive open, so we use a small client component with React state to enforce single-open behavior).

**Feature 6: Waitlist email capture form.** Email input + submit button in the dark CTA section. Client-side email validation (regex). POST to `/api/waitlist`. Three UI states: idle, submitting, success. Error states for invalid email and server failure.

**Feature 7: Waitlist API endpoint.** A Next.js Route Handler at `/api/waitlist` that accepts POST with a JSON body `{ email: string }`. Validates the email server-side with the same regex. Appends `{ email, createdAt: ISO timestamp }` to `data/waitlist.json`. Returns JSON. No authentication required — this is a public marketing endpoint. Rate limiting is out of scope for this build but the endpoint should be structured so it can be added later.

**Feature 8: Footer with legal links.** Static footer with copyright and two placeholder links. The Privacy and Terms links point to `#` for now (no real legal pages exist yet — do not invent legal copy).

## 7. DATA MODEL

**WaitlistEntry** — represents one email signup.
- `id`: string (UUID v4, generated server-side)
- `email`: string (validated, lowercased, max 254 chars per RFC 5321)
- `createdAt`: string (ISO 8601 timestamp)

Storage: append-only JSON file at `data/waitlist.json`. Structure: `{ entries: WaitlistEntry[] }`. The file is created on first write if it doesn't exist. No database, no ORM, no migrations. This is appropriate for a pre-launch waitlist with low volume.

No other entities. No users, no projects, no prototypes — the app doesn't exist yet.

## 8. AUTH

No authentication on this build. The waitlist endpoint is public and unauthenticated by design — it is a marketing capture form, not a gated feature. There is no login, no signup, no session, no user account. Do not add NextAuth, do not add Supabase Auth, do not add Clerk. The only server-side concern is input validation on the waitlist endpoint.

## 9. FILES

```
package.json                          — Next.js 14, React 18, TypeScript, Tailwind, lucide-react
next.config.js                        — minimal Next config, no custom webpack
tsconfig.json                         — Next.js TypeScript config
tailwind.config.ts                    — custom colors (navy, cobalt, accent), Inter + IBM Plex Sans font families
postcss.config.js                     — tailwindcss + autoprefixer
app/globals.css                       — Tailwind directives, base resets, font imports
app/layout.tsx                        — root layout, Inter + IBM Plex Sans via next/font, metadata
app/page.tsx                          — composes Nav + Hero + Features + Pricing + FAQ + CTA + Footer
app/api/waitlist/route.ts             — POST handler for email capture, writes to data/waitlist.json
components/Nav.tsx                    — sticky nav with logo, anchor links, CTA button, mobile menu
components/Hero.tsx                   — headline, subhead, dual CTA, product mockup placeholder
components/Features.tsx               — section header + 6-card responsive grid
components/Pricing.tsx                — section header + 3-tier pricing cards with Popular badge
components/FAQ.tsx                    — section header + 6-item accordion (client component for single-open)
components/CTA.tsx                    — dark navy section with email form, client component for state
components/Footer.tsx                 — copyright + Privacy/Terms links
components/icons.tsx                  — Lucide icon re-exports used across components
lib/waitlist.ts                       — server-side helpers: validateEmail, appendEntry, readEntries
data/waitlist.json                    — created on first write, gitignored initially
.gitignore                            — node_modules, .next, data/waitlist.json
```

## 10. ACCEPTANCE

- [ ] `npm install` completes without errors
- [ ] `npm run dev` starts the Next.js dev server on port 3000
- [ ] `npm run build` completes without TypeScript or build errors
- [ ] Visiting `/` renders all seven sections in order: Nav, Hero, Features, Pricing, FAQ, CTA, Footer
- [ ] Nav is sticky and stays visible on scroll
- [ ] Nav anchor links smooth-scroll to Features (#features), Pricing (#pricing), FAQ (#faq), and CTA (#cta)
- [ ] "Join Waitlist" in nav scrolls to the CTA section
- [ ] Hero H1 reads exactly "Validate Your Startup Idea Before You Build It"
- [ ] Hero shows two buttons: "Join the Waitlist" (primary) and "See How It Works" (secondary)
- [ ] "See How It Works" scrolls to Features
- [ ] Features section shows exactly 6 cards with the specified titles and descriptions
- [ ] Features grid is 3 columns on desktop (≥1024px), 2 on tablet (≥768px), 1 on mobile
- [ ] Pricing section shows exactly 3 tiers: Explorer ($0), Builder ($29/mo), Team ($79/mo)
- [ ] Builder tier has a green "Most Popular" badge and a cobalt-filled CTA button
- [ ] Explorer and Team CTAs are white with a border
- [ ] All three pricing CTAs scroll to the CTA section
- [ ] FAQ section shows exactly 6 items with the specified questions and answers
- [ ] FAQ accordion enforces single-open behavior (opening one closes others)
- [ ] FAQ chevron rotates 180deg when an item is open
- [ ] CTA section has navy background, white H2, email input, and green submit button
- [ ] Submitting an invalid email (e.g., "notanemail") shows a red error message and does not submit
- [ ] Submitting a valid email POSTs to `/api/waitlist` and shows the success state
- [ ] `/api/waitlist` appends the entry to `data/waitlist.json` with id, email, and createdAt
- [ ] `/api/waitlist` returns `{ ok: true }` on success and `{ ok: false, error: "invalid_email" }` on bad input
- [ ] Footer shows "© 2026 Uncle Inc. All rights reserved." and two links: Privacy, Terms
- [ ] Privacy and Terms links point to `#` (no invented legal pages)
- [ ] No fake testimonials, customer logos, user counts, ratings, or press mentions anywhere on the page
- [ ] Color palette uses only the specified tokens: navy #1A3A5C, cobalt #4A90D9, green #22C55E, plus the neutral slate scale
- [ ] Headings use Inter, body uses IBM Plex Sans (loaded via next/font, no FOUT)
- [ ] Page is responsive and usable at 360px, 768px, and 1440px widths
- [ ] All interactive elements have visible focus rings (keyboard accessibility)
- [ ] No console errors or warnings in the browser
- [ ] No external image dependencies (everything renders without network calls beyond fonts)

FILES: ["package.json", "next.config.js", "tsconfig.json", "tailwind.config.ts", "postcss.config.js", "app/globals.css", "app/layout.tsx", "app/page.tsx", "app/api/waitlist/route.ts", "components/Nav.tsx", "components/Hero.tsx", "components/Features.tsx", "components/Pricing.tsx", "components/FAQ.tsx", "components/CTA.tsx", "components/Footer.tsx", "components/icons.tsx", "lib/waitlist.ts", ".gitignore"]