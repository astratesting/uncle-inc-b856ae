# Uncle Inc. — Build Plan

## 1. PRODUCT
Uncle Inc. is a marketing landing page (and the seed of a larger app) for an AI-assisted MVP platform that helps solo technical and non-technical founders validate startup ideas without a co-founder. The core value: collapse the weeks-long "napkin sketch → deployed prototype → first user signal" loop into a 72-hour, guided workflow combining AI prototyping, built-in user testing, and launch analytics. The primary user is a time-poor, non-technical first-time founder who has an idea but no team, no validation data, and no patience for enterprise tooling. The pain we solve — directly cited from the design session's "Crisp Operator" archetype and the founder's stated goal — is the founder's fear of building the wrong thing for months, alone, before discovering nobody wants it.

This deliverable is the public-facing Next.js 14 landing page that introduces Uncle Inc., explains the six core capabilities, shows three honest pricing tiers, answers the six most common pre-signup questions, captures waitlist emails, and links Privacy/Terms. It is the front door of the future product (dashboard + onboarding per the design wireframes) but ships today as a static, fast, accessible marketing site.

## 2. WHO IT'S FOR
ICP from the research: solo, non-technical, first-time founder, idea-stage, low budget, low time. The "Crisp Operator" archetype from the design notes — clean enterprise UI, confident whitespace, 1280px container, 4px spacing — confirms a professional but warm tone: not consumer-playful, not enterprise-stuffy. Implications:
- **Copy must respect time.** Short sentences, scannable, no jargon ("MVP", "GTM", "TAM" replaced with plain English: "prototype", "test", "see if people want it").
- **CTAs must be low-friction.** Single primary action per screen: waitlist email capture. No "Book a demo", no sales calls.
- **Trust signals must be honest.** No fake logos, no invented testimonials, no made-up user counts. A product with zero customers shows the value prop and the mechanism, not social proof that doesn't exist.
- **Tone is the "uncle" metaphor.** A trusted, slightly opinionated relative who tells you the truth. Confident, helpful, direct. Hence "Stop Guessing. Start Validating." — operator-direct, not motivational-poster.
- **Pricing shown transparently.** Three tiers, plain numbers, no "Contact us" — the ICP is a freelancer, not a procurement department.

## 3. LOOK & FEEL

**Visual system** (from the prior design session, ratified):
- **Vibe/positioning:** Crisp Operator. Clean enterprise UI, precise grids, confident whitespace. Not a "creator economy" look, not a "VC pitch deck" look. Looks like a tool a founder would actually pay for.
- **Color palette** (locked in `tailwind.config.ts`):
  - `navy` `#1A3A5C` — primary, used for headings, dark CTA background, footer
  - `cobalt` `#4A90D9` — secondary, used for links, icon accents, illustration strokes
  - `slate` `#64748B` — body text secondary, captions, FAQ question labels
  - `green` `#22C55E` — single accent, used ONLY for the primary CTA button and the "Popular" badge on the Builder tier. Restrained.
  - `surface` `#FFFFFF` — card backgrounds
  - `bg` `#F8FAFC` — page background, subtle contrast against white cards
  - Implicit utility classes: `text-slate-900` for body, `border-slate-200` for hairlines
- **Typography:**
  - Headings: `Inter` (variable, from `next/font/google`), tight tracking, semibold (600) for H1/H2, medium (500) for H3
  - Body: `IBM Plex Sans` (from `next/font/google`), regular (400), 16px base, 1.6 line-height
  - Mono: not used on landing, but configured in Tailwind for future dashboard
- **Spacing/layout:** 4px base, 1280px max container, sections separated by 96–128px vertical padding on desktop, 64px on mobile. Two-column hero (text + visual mock), three-column features grid, three-column pricing grid, single-column FAQ.
- **Key components:** sticky top nav, pill-shaped green CTA, white rounded cards with 1px slate-200 border and subtle shadow, FAQ `<details>` accordions, email input + button combo in dark CTA section, footer with two text links.
- **Iconography:** inline SVG only, 1.5px stroke, cobalt or navy. No icon library import (keeps bundle small). Each feature card has a single 24px icon.
- **Imagery:** no stock photos. The hero includes a small abstract "switchboard" SVG mock (per the design session's logo motif) showing three connected nodes — visually references the idea-to-validation flow without faking a product screenshot. No fake product UI, no fake dashboard imagery.
- **Motion:** minimal. Smooth scroll for anchor links. Subtle 150ms color transition on buttons and links. No scroll animations, no parallax — the ICP doesn't have time for theater.

**Screen-by-screen layout:**

1. **Nav (sticky, 64px tall):** white background with 1px bottom border in `slate-200`. Left: "Uncle Inc." wordmark in navy, semibold. Right: three text links ("Features", "Pricing", "FAQ") in `slate-700`, 14px medium. Far right: green pill button "Join Waitlist" (anchor to `#waitlist`). On mobile (<768px): wordmark left, hamburger that toggles a vertical menu with the three links stacked + the green button at the bottom.
2. **Hero:** full-width, white background, 96px top padding (clears sticky nav). Two-column on desktop (60/40 split), stacked on mobile. Left column: H1 in navy Inter 56px/1.1 semibold, subtext in slate 18px IBM Plex Sans, two buttons side-by-side (green primary "Join the Waitlist" → `#waitlist`, outlined navy "See How It Works" → `#features`). Right column: switchboard SVG mock (240×240) centered, cobalt strokes on slate-100 background, no fake product screenshot. Below the two columns, a single thin row of three short trust statements (e.g., "No credit card", "No code required", "Built for solo founders") in slate-500, separated by middle dots.
3. **Features (`#features`):** light `bg` background. Section header centered: eyebrow text "What You Get" in cobalt uppercase 12px tracking-widest, H2 "Six Tools, One Workflow" in navy 40px. Below: 3-column grid (2-column tablet, 1-column mobile) of 6 white cards. Each card: 24px cobalt icon top-left, H3 in navy 18px semibold, body in slate-600 15px, 32px padding, 4px border-radius, 1px slate-200 border. Cards: AI Rapid Prototyping, Built-in User Testing, Launch Analytics, Guided Validation, No Code Required, Iterate with Real Data.
4. **Pricing (`#pricing`):** white background. Section header centered: eyebrow "Pricing" in cobalt, H2 "Honest Pricing, No Surprises" in navy. Three cards in a row (stacked on mobile). Card 1 "Explorer" — $0/mo, "Free forever", 5 feature bullets, outlined "Get Started" button. Card 2 "Builder" — $29/mo, "Most Popular" green badge top-right, 7 bullets, filled green "Start Free Trial" button, card has cobalt 2px border + slight lift. Card 3 "Team" — $79/mo, "For small teams", 7 bullets, outlined navy button. Below grid: a single line of slate-500 small text "All plans include a 14-day free trial. No credit card required." — honest, not invented testimonials.
5. **FAQ (`#faq`):** light `bg` background. Section header centered: eyebrow "Questions" in cobalt, H2 "Frequently Asked" in navy. Single column, max-width 720px, six `<details>` elements. Each: question as `<summary>` in navy 16px medium with a right-aligned `+`/`−` indicator, answer in slate-600 15px IBM Plex Sans, 1px slate-200 divider between items.
6. **CTA (`#waitlist`):** navy `#1A3A5C` full-width background, 96px vertical padding. Centered content: H2 "Stop Guessing. Start Validating." in white 40px, subtext "Join 0 founders on the waitlist" in slate-300 16px (the "0" is honest — pre-launch), single email input + green button combo (input: white, rounded-l, 320px wide; button: green "Join Waitlist", rounded-r). Below: small slate-400 disclaimer "We'll only email you when Uncle Inc. launches. No spam."
7. **Footer:** white background, 1px slate-200 top border, 64px padding. Two-column on desktop, stacked on mobile. Left: "© 2026 Uncle Inc." in slate-500 14px. Right: two text links "Privacy" and "Terms" in slate-500, separated by a middle dot.

## 4. USER FLOWS
The landing page has one primary flow and several anchor-link micro-flows.

**Primary: Anonymous visitor → waitlist signup**
1. Land on `/` (auto-scrolls to top).
2. See Hero with clear value prop and two CTAs.
3. Click "Join the Waitlist" (hero button) → smooth-scroll to `#waitlist` section.
4. Type email into input (HTML5 email validation enforced).
5. Click green "Join Waitlist" button.
6. **Form behavior (client-only, honest):** since this is a static landing page with no backend wired in this deliverable, the form's `onSubmit` calls `e.preventDefault()`, validates the email is non-empty and matches a basic regex, then displays a success state inline: input is replaced with a green checkmark and the text "Thanks — you're on the list. We'll be in touch." The email is logged to `console.info` (with a clear `// TODO: wire to waitlist API` comment) so the developer can later connect it to a real endpoint. No fake success animation, no fake confirmation page.
7. Error state: if email is empty or invalid, the input border turns red (`#DC2626`) and helper text "Please enter a valid email" appears below. Submitting in error state does nothing.

**Secondary flows:**
- **Mobile nav toggle:** tap hamburger → menu slides down (150ms), three links + green button appear, tap link → menu closes, smooth-scroll to section, tap outside or hamburger again → menu closes.
- **Anchor nav:** click "Features"/"Pricing"/"FAQ" in nav → smooth-scroll to that section. Sticky nav stays in place.
- **"See How It Works" button:** in Hero, scrolls to `#features`.

**States to handle:**
- Default: CTA email input empty, button enabled.
- Focused: input has 2px cobalt ring.
- Invalid (after submit attempt): red border, helper text visible.
- Submitting: button shows "Joining..." text and is disabled. (Since there's no real network call in this deliverable, this state is reachable only by adding a 600ms `setTimeout` for visual feedback — the developer can keep or remove it.)
- Success: input + button replaced by green confirmation row.
- Mobile menu: closed (default), open.

## 5. PAGES/ROUTES
This deliverable is a single-route marketing site plus standard Next.js boilerplate.

- **`/`** (`app/page.tsx`) — the landing page. Renders, in order: `<Nav />`, `<Hero />`, `<Features />`, `<Pricing />`, `<FAQ />`, `<CTA />`, `<Footer />`. Each section is a `<section>` with an `id` for anchor navigation (`#features`, `#pricing`, `#faq`, `#waitlist`).
- **No other routes in this deliverable.** The design session's wireframes reference a future `/dashboard` and `/onboarding` — those are out of scope for this landing-page task and will be built in a later milestone. No 404 page is required by the spec; Next.js's default 404 is acceptable.

## 6. CORE FEATURES
Each is a real, implemented React component with real content, not a placeholder.

1. **Sticky navigation with anchor links and mobile menu.** The nav uses `position: sticky; top: 0; z-50` with a white background and 1px bottom border. The mobile menu is a client component (`"use client"`) using `useState` to toggle a vertical menu below the nav. The "Join Waitlist" link uses `href="#waitlist"` for smooth in-page scroll.
2. **Hero with two-column layout and switchboard mock SVG.** The hero is a server component. The SVG is a small inline component (three rounded-rect nodes connected by lines, drawn in cobalt on a slate-100 rounded background) — no external image file, no fake product UI. The two CTAs are a green `<a href="#waitlist">` and an outlined navy `<a href="#features">`.
3. **Six feature cards in a responsive grid.** Each card is a presentational component receiving `{ icon, title, body }` as props. Icons are inline SVG functions defined in the same file. Grid uses `grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6`. Content per the spec: AI Rapid Prototyping, Built-in User Testing, Launch Analytics, Guided Validation, No Code Required, Iterate with Real Data. Each gets a 1–2 sentence honest description (no invented stats, no "10x faster" claims).
4. **Three-tier pricing with "Popular" highlight.** Builder tier has a green "Most Popular" badge absolutely positioned top-right and a 2px cobalt border. Buttons are real `<a href="#waitlist">` so all tiers funnel to the waitlist (no fake checkout). The "All plans include a 14-day free trial" line is honest and consistent with a pre-launch waitlist product.
5. **Six-question FAQ with native `<details>` accordions.** Uses semantic HTML `<details>` / `<summary>` for built-in keyboard accessibility and zero-JS expand behavior. The `+`/`−` indicator is a CSS-only trick using `details[open] summary::after`. Questions and answers are honest, founder-relevant, and avoid invented specifics.
6. **Email waitlist capture with client-side validation and inline success state.** Client component with `useState` for `email`, `status` (`'idle' | 'submitting' | 'success' | 'error'`), and `errorMessage`. On submit: validates with regex `/^[^\s@]+@[^\s@]+\.[^\s@]+$/`, shows submitting state, logs to console, shows success. Single source of truth — no external form library, no fake API call.
7. **Footer with copyright and two legal links.** Privacy and Terms are placeholder `<a href="#">` links (no fake routes, no invented policies) with a `// TODO: link to real /privacy and /terms pages` comment for the developer.

## 7. DATA MODEL
This is a static marketing site. There is no database, no user accounts, no backend in this deliverable. The only piece of "data" is the waitlist email, which is captured client-side and logged to `console.info` with a clear TODO for future wiring to a real endpoint (e.g., a `POST /api/waitlist` route + a Supabase `waitlist` table with `{ id, email, created_at }`). The data model is documented as a comment in `components/CTA.tsx` for the next developer.

## 8. AUTH
**No authentication is required for this deliverable.** The landing page is public, anonymous, and read-only except for the waitlist email capture. There is no login, no signup, no dashboard, no protected routes. When the future dashboard is built, the spec calls for Supabase Auth with email + password as the default (magic link as alternative) — explicitly **not** Clerk, explicitly **not** Google/GitHub/social OAuth unless real credentials are provisioned.

## 9. FILES
Concrete file tree to create, with one-line purpose for each. This matches the spec exactly and adds only the minimal necessary files (the two font imports are bundled into `app/layout.tsx`).

```
package.json                              // next@14, react@18, tailwind, typescript deps
next.config.js                            // minimal Next.js 14 config
tsconfig.json                             // standard Next.js TypeScript config
tailwind.config.ts                        // custom color palette (navy/cobalt/slate/green/surface/bg) + Inter/IBM Plex Sans font families
postcss.config.js                         // tailwindcss + autoprefixer
app/layout.tsx                            // root layout: imports Inter + IBM_Plex_Sans, sets metadata title
app/globals.css                           // @tailwind base/components/utilities + minimal base styles
app/page.tsx                              // landing page composition: imports + renders Nav, Hero, Features, Pricing, FAQ, CTA, Footer
components/Nav.tsx                        // sticky top nav with logo, anchor links, green CTA, mobile hamburger menu (client component)
components/Hero.tsx                       // hero section: H1, subtext, two CTAs, switchboard SVG mock, trust row
components/Features.tsx                   // 6 feature cards in responsive 3-col grid with inline SVG icons
components/Pricing.tsx                    // 3 pricing tiers with "Most Popular" highlight on Builder
components/FAQ.tsx                        // 6 expandable <details> accordions
components/CTA.tsx                        // navy bg waitlist section with email input + button + client-side validation (client component)
components/Footer.tsx                     // copyright + Privacy/Terms links
```

## 10. ACCEPTANCE
Done and working means:

- [ ] `npm install` completes without errors.
- [ ] `npm run dev` starts the Next.js dev server and `/` loads at `http://localhost:3000` with no console errors.
- [ ] `npm run build` completes successfully (TypeScript compiles, no Tailwind errors).
- [ ] All seven sections render in order: Nav, Hero, Features, Pricing, FAQ, CTA, Footer.
- [ ] Tailwind config contains the six custom colors exactly as hex values specified.
- [ ] `Inter` is applied to all headings, `IBM Plex Sans` to all body text (verified via computed styles).
- [ ] Page metadata title is exactly "Uncle Inc. - Validate Your Startup Idea Before You Build It".
- [ ] Sticky nav remains visible while scrolling and links smooth-scroll to `#features`, `#pricing`, `#faq`, `#waitlist`.
- [ ] On mobile (<768px), the hamburger menu opens/closes the nav and shows all three links plus the green CTA.
- [ ] Hero contains the exact H1 "Validate Your Startup Idea Before You Build It" and the exact subtext "AI-assisted MVP platform. Go from napkin sketch to tested prototype in 72 hours. No technical co-founder required."
- [ ] Hero has two buttons: green "Join the Waitlist" (→ #waitlist) and outlined "See How It Works" (→ #features).
- [ ] Features section shows exactly 6 cards with the exact titles: AI Rapid Prototyping, Built-in User Testing, Launch Analytics, Guided Validation, No Code Required, Iterate with Real Data.
- [ ] Pricing section shows exactly 3 tiers: Explorer ($0), Builder ($29/mo with "Most Popular" badge), Team ($79/mo).
- [ ] FAQ section shows exactly 6 expandable questions, all using semantic `<details>`/`<summary>`.
- [ ] CTA section has navy background, H2 "Stop Guessing. Start Validating.", an email input, and a green button.
- [ ] Waitlist email form validates client-side (empty/invalid → red border + helper text) and shows a success state on valid submit.
- [ ] Footer shows "© 2026 Uncle Inc." and links to "#" for Privacy and Terms.
- [ ] **No fake testimonials, no fake logos, no fake user counts, no fake metrics anywhere on the page.** The only number shown is the honest "0 founders" in the waitlist subtitle.
- [ ] Page is keyboard-navigable: tab order is logical, focus rings are visible, FAQ accordions expand/collapse with Enter/Space.
- [ ] All colors used in components come from the Tailwind config (no inline hex values except in the config itself).
- [ ] All icons are inline SVG; no external icon library or image assets are required.

FILES: ["package.json", "next.config.js", "tsconfig.json", "tailwind.config.ts", "postcss.config.js", "app/layout.tsx", "app/globals.css", "app/page.tsx", "components/Nav.tsx", "components/Hero.tsx", "components/Features.tsx", "components/Pricing.tsx", "components/FAQ.tsx", "components/CTA.tsx", "components/Footer.tsx"]# Uncle Inc. — Build Plan

## 1. PRODUCT
Uncle Inc. is a marketing landing page (and the seed of a larger app) for an AI-assisted MVP platform that helps solo technical and non-technical founders validate startup ideas without a co-founder. The core value: collapse the weeks-long "napkin sketch → deployed prototype → first user signal" loop into a 72-hour, guided workflow combining AI prototyping, built-in user testing, and launch analytics. The primary user is a time-poor, non-technical first-time founder who has an idea but no team, no validation data, and no patience for enterprise tooling. The pain we solve — directly cited from the design session's "Crisp Operator" archetype and the founder's stated goal — is the founder's fear of building the wrong thing for months, alone, before discovering nobody wants it.

This deliverable is the public-facing Next.js 14 landing page that introduces Uncle Inc., explains the six core capabilities, shows three honest pricing tiers, answers the six most common pre-signup questions, captures waitlist emails, and links Privacy/Terms. It is the front door of the future product (dashboard + onboarding per the design wireframes) but ships today as a static, fast, accessible marketing site.

## 2. WHO IT'S FOR
ICP from the research: solo, non-technical, first-time founder, idea-stage, low budget, low time. The "Crisp Operator" archetype from the design notes — clean enterprise UI, confident whitespace, 1280px container, 4px spacing — confirms a professional but warm tone: not consumer-playful, not enterprise-stuffy. Implications:
- **Copy must respect time.** Short sentences, scannable, no jargon ("MVP", "GTM", "TAM" replaced with plain English: "prototype", "test", "see if people want it").
- **CTAs must be low-friction.** Single primary action per screen: waitlist email capture. No "Book a demo", no sales calls.
- **Trust signals must be honest.** No fake logos, no invented testimonials, no made-up user counts. A product with zero customers shows the value prop and the mechanism, not social proof that doesn't exist.
- **Tone is the "uncle" metaphor.** A trusted, slightly opinionated relative who tells you the truth. Confident, helpful, direct. Hence "Stop Guessing. Start Validating." — operator-direct, not motivational-poster.
- **Pricing shown transparently.** Three tiers, plain numbers, no "Contact us" — the ICP is a freelancer, not a procurement department.

## 3. LOOK & FEEL

**Visual system** (from the prior design session, ratified):
- **Vibe/positioning:** Crisp Operator. Clean enterprise UI, precise grids, confident whitespace. Not a "creator economy" look, not a "VC pitch deck" look. Looks like a tool a founder would actually pay for.
- **Color palette** (locked in `tailwind.config.ts`):
  - `navy` `#1A3A5C` — primary, used for headings, dark CTA background, footer
  - `cobalt` `#4A90D9` — secondary, used for links, icon accents, illustration strokes
  - `slate` `#64748B` — body text secondary, captions, FAQ question labels
  - `green` `#22C55E` — single accent, used ONLY for the primary CTA button and the "Popular" badge on the Builder tier. Restrained.
  - `surface` `#FFFFFF` — card backgrounds
  - `bg` `#F8FAFC` — page background, subtle contrast against white cards
  - Implicit utility classes: `text-slate-900` for body, `border-slate-200` for hairlines
- **Typography:**
  - Headings: `Inter` (variable, from `next/font/google`), tight tracking, semibold (600) for H1/H2, medium (500) for H3
  - Body: `IBM Plex Sans` (from `next/font/google`), regular (400), 16px base, 1.6 line-height
  - Mono: not used on landing, but configured in Tailwind for future dashboard
- **Spacing/layout:** 4px base, 1280px max container, sections separated by 96–128px vertical padding on desktop, 64px on mobile. Two-column hero (text + visual mock), three-column features grid, three-column pricing grid, single-column FAQ.
- **Key components:** sticky top nav, pill-shaped green CTA, white rounded cards with 1px slate-200 border and subtle shadow, FAQ `<details>` accordions, email input + button combo in dark CTA section, footer with two text links.
- **Iconography:** inline SVG only, 1.5px stroke, cobalt or navy. No icon library import (keeps bundle small). Each feature card has a single 24px icon.
- **Imagery:** no stock photos. The hero includes a small abstract "switchboard" SVG mock (per the design session's logo motif) showing three connected nodes — visually references the idea-to-validation flow without faking a product screenshot. No fake product UI, no fake dashboard imagery.
- **Motion:** minimal. Smooth scroll for anchor links. Subtle 150ms color transition on buttons and links. No scroll animations, no parallax — the ICP doesn't have time for theater.

**Screen-by-screen layout:**

1. **Nav (sticky, 64px tall):** white background with 1px bottom border in `slate-200`. Left: "Uncle Inc." wordmark in navy, semibold. Right: three text links ("Features", "Pricing", "FAQ") in `slate-700`, 14px medium. Far right: green pill button "Join Waitlist" (anchor to `#waitlist`). On mobile (<768px): wordmark left, hamburger that toggles a vertical menu with the three links stacked + the green button at the bottom.
2. **Hero:** full-width, white background, 96px top padding (clears sticky nav). Two-column on desktop (60/40 split), stacked on mobile. Left column: H1 in navy Inter 56px/1.1 semibold, subtext in slate 18px IBM Plex Sans, two buttons side-by-side (green primary "Join the Waitlist" → `#waitlist`, outlined navy "See How It Works" → `#features`). Right column: switchboard SVG mock (240×240) centered, cobalt strokes on slate-100 background, no fake product screenshot. Below the two columns, a single thin row of three short trust statements (e.g., "No credit card", "No code required", "Built for solo founders") in slate-500, separated by middle dots.
3. **Features (`#features`):** light `bg` background. Section header centered: eyebrow text "What You Get" in cobalt uppercase 12px tracking-widest, H2 "Six Tools, One Workflow" in navy 40px. Below: 3-column grid (2-column tablet, 1-column mobile) of 6 white cards. Each card: 24px cobalt icon top-left, H3 in navy 18px semibold, body in slate-600 15px, 32px padding, 4px border-radius, 1px slate-200 border. Cards: AI Rapid Prototyping, Built-in User Testing, Launch Analytics, Guided Validation, No Code Required, Iterate with Real Data.
4. **Pricing (`#pricing`):** white background. Section header centered: eyebrow "Pricing" in cobalt, H2 "Honest Pricing, No Surprises" in navy. Three cards in a row (stacked on mobile). Card 1 "Explorer" — $0/mo, "Free forever", 5 feature bullets, outlined "Get Started" button. Card 2 "Builder" — $29/mo, "Most Popular" green badge top-right, 7 bullets, filled green "Start Free Trial" button, card has cobalt 2px border + slight lift. Card 3 "Team" — $79/mo, "For small teams", 7 bullets, outlined navy button. Below grid: a single line of slate-500 small text "All plans include a 14-day free trial. No credit card required." — honest, not invented testimonials.
5. **FAQ (`#faq`):** light `bg` background. Section header centered: eyebrow "Questions" in cobalt, H2 "Frequently Asked" in navy. Single column, max-width 720px, six `<details>` elements. Each: question as `<summary>` in navy 16px medium with a right-aligned `+`/`−` indicator, answer in slate-600 15px IBM Plex Sans, 1px slate-200 divider between items.
6. **CTA (`#waitlist`):** navy `#1A3A5C` full-width background, 96px vertical padding. Centered content: H2 "Stop Guessing. Start Validating." in white 40px, subtext "Join 0 founders on the waitlist" in slate-300 16px (the "0" is honest — pre-launch), single email input + green button combo (input: white, rounded-l, 320px wide; button: green "Join Waitlist", rounded-r). Below: small slate-400 disclaimer "We'll only email you when Uncle Inc. launches. No spam."
7. **Footer:** white background, 1px slate-200 top border, 64px padding. Two-column on desktop, stacked on mobile. Left: "© 2026 Uncle Inc." in slate-500 14px. Right: two text links "Privacy" and "Terms" in slate-500, separated by a middle dot.

## 4. USER FLOWS
The landing page has one primary flow and several anchor-link micro-flows.

**Primary: Anonymous visitor → waitlist signup**
1. Land on `/` (auto-scrolls to top).
2. See Hero with clear value prop and two CTAs.
3. Click "Join the Waitlist" (hero button) → smooth-scroll to `#waitlist` section.
4. Type email into input (HTML5 email validation enforced).
5. Click green "Join Waitlist" button.
6. **Form behavior (client-only, honest):** since this is a static landing page with no backend wired in this deliverable, the form's `onSubmit` calls `e.preventDefault()`, validates the email is non-empty and matches a basic regex, then displays a success state inline: input is replaced with a green checkmark and the text "Thanks — you're on the list. We'll be in touch." The email is logged to `console.info` (with a clear `// TODO: wire to waitlist API` comment) so the developer can later connect it to a real endpoint. No fake success animation, no fake confirmation page.
7. Error state: if email is empty or invalid, the input border turns red (`#DC2626`) and helper text "Please enter a valid email" appears below. Submitting in error state does nothing.

**Secondary flows:**
- **Mobile nav toggle:** tap hamburger → menu slides down (150ms), three links + green button appear, tap link → menu closes, smooth-scroll to section, tap outside or hamburger again → menu closes.
- **Anchor nav:** click "Features"/"Pricing"/"FAQ" in nav → smooth-scroll to that section. Sticky nav stays in place.
- **"See How It Works" button:** in Hero, scrolls to `#features`.

**States to handle:**
- Default: CTA email input empty, button enabled.
- Focused: input has 2px cobalt ring.
- Invalid (after submit attempt): red border, helper text visible.
- Submitting: button shows "Joining..." text and is disabled. (Since there's no real network call in this deliverable, this state is reachable only by adding a 600ms `setTimeout` for visual feedback — the developer can keep or remove it.)
- Success: input + button replaced by green confirmation row.
- Mobile menu: closed (default), open.

## 5. PAGES/ROUTES
This deliverable is a single-route marketing site plus standard Next.js boilerplate.

- **`/`** (`app/page.tsx`) — the landing page. Renders, in order: `<Nav />`, `<Hero />`, `<Features />`, `<Pricing />`, `<FAQ />`, `<CTA />`, `<Footer />`. Each section is a `<section>` with an `id` for anchor navigation (`#features`, `#pricing`, `#faq`, `#waitlist`).
- **No other routes in this deliverable.** The design session's wireframes reference a future `/dashboard` and `/onboarding` — those are out of scope for this landing-page task and will be built in a later milestone. No 404 page is required by the spec; Next.js's default 404 is acceptable.

## 6. CORE FEATURES
Each is a real, implemented React component with real content, not a placeholder.

1. **Sticky navigation with anchor links and mobile menu.** The nav uses `position: sticky; top: 0; z-50` with a white background and 1px bottom border. The mobile menu is a client component (`"use client"`) using `useState` to toggle a vertical menu below the nav. The "Join Waitlist" link uses `href="#waitlist"` for smooth in-page scroll.
2. **Hero with two-column layout and switchboard mock SVG.** The hero is a server component. The SVG is a small inline component (three rounded-rect nodes connected by lines, drawn in cobalt on a slate-100 rounded background) — no external image file, no fake product UI. The two CTAs are a green `<a href="#waitlist">` and an outlined navy `<a href="#features">`.
3. **Six feature cards in a responsive grid.** Each card is a presentational component receiving `{ icon, title, body }` as props. Icons are inline SVG functions defined in the same file. Grid uses `grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6`. Content per the spec: AI Rapid Prototyping, Built-in User Testing, Launch Analytics, Guided Validation, No Code Required, Iterate with Real Data. Each gets a 1–2 sentence honest description (no invented stats, no "10x faster" claims).
4. **Three-tier pricing with "Popular" highlight.** Builder tier has a green "Most Popular" badge absolutely positioned top-right and a 2px cobalt border. Buttons are real `<a href="#waitlist">` so all tiers funnel to the waitlist (no fake checkout). The "All plans include a 14-day free trial" line is honest and consistent with a pre-launch waitlist product.
5. **Six-question FAQ with native `<details>` accordions.** Uses semantic HTML `<details>` / `<summary>` for built-in keyboard accessibility and zero-JS expand behavior. The `+`/`−` indicator is a CSS-only trick using `details[open] summary::after`. Questions and answers are honest, founder-relevant, and avoid invented specifics.
6. **Email waitlist capture with client-side validation and inline success state.** Client component with `useState` for `email`, `status` (`'idle' | 'submitting' | 'success' | 'error'`), and `errorMessage`. On submit: validates with regex `/^[^\s@]+@[^\s@]+\.[^\s@]+$/`, shows submitting state, logs to console, shows success. Single source of truth — no external form library, no fake API call.
7. **Footer with copyright and two legal links.** Privacy and Terms are placeholder `<a href="#">` links (no fake routes, no invented policies) with a `// TODO: link to real /privacy and /terms pages` comment for the developer.

## 7. DATA MODEL
This is a static marketing site. There is no database, no user accounts, no backend in this deliverable. The only piece of "data" is the waitlist email, which is captured client-side and logged to `console.info` with a clear TODO for future wiring to a real endpoint (e.g., a `POST /api/waitlist` route + a Supabase `waitlist` table with `{ id, email, created_at }`). The data model is documented as a comment in `components/CTA.tsx` for the next developer.

## 8. AUTH
**No authentication is required for this deliverable.** The landing page is public, anonymous, and read-only except for the waitlist email capture. There is no login, no signup, no dashboard, no protected routes. When the future dashboard is built, the spec calls for Supabase Auth with email + password as the default (magic link as alternative) — explicitly **not** Clerk, explicitly **not** Google/GitHub/social OAuth unless real credentials are provisioned.

## 9. FILES
Concrete file tree to create, with one-line purpose for each. This matches the spec exactly and adds only the minimal necessary files (the two font imports are bundled into `app/layout.tsx`).

```
package.json                              // next@14, react@18, tailwind, typescript deps
next.config.js                            // minimal Next.js 14 config
tsconfig.json                             // standard Next.js TypeScript config
tailwind.config.ts                        // custom color palette (navy/cobalt/slate/green/surface/bg) + Inter/IBM Plex Sans font families
postcss.config.js                         // tailwindcss + autoprefixer
app/layout.tsx                            // root layout: imports Inter + IBM_Plex_Sans, sets metadata title
app/globals.css                           // @tailwind base/components/utilities + minimal base styles
app/page.tsx                              // landing page composition: imports + renders Nav, Hero, Features, Pricing, FAQ, CTA, Footer
components/Nav.tsx                        // sticky top nav with logo, anchor links, green CTA, mobile hamburger menu (client component)
components/Hero.tsx                       // hero section: H1, subtext, two CTAs, switchboard SVG mock, trust row
components/Features.tsx                   // 6 feature cards in responsive 3-col grid with inline SVG icons
components/Pricing.tsx                    // 3 pricing tiers with "Most Popular" highlight on Builder
components/FAQ.tsx                        // 6 expandable <details> accordions
components/CTA.tsx                        // navy bg waitlist section with email input + button + client-side validation (client component)
components/Footer.tsx                     // copyright + Privacy/Terms links
```

## 10. ACCEPTANCE
Done and working means:

- [ ] `npm install` completes without errors.
- [ ] `npm run dev` starts the Next.js dev server and `/` loads at `http://localhost:3000` with no console errors.
- [ ] `npm run build` completes successfully (TypeScript compiles, no Tailwind errors).
- [ ] All seven sections render in order: Nav, Hero, Features, Pricing, FAQ, CTA, Footer.
- [ ] Tailwind config contains the six custom colors exactly as hex values specified.
- [ ] `Inter` is applied to all headings, `IBM Plex Sans` to all body text (verified via computed styles).
- [ ] Page metadata title is exactly "Uncle Inc. - Validate Your Startup Idea Before You Build It".
- [ ] Sticky nav remains visible while scrolling and links smooth-scroll to `#features`, `#pricing`, `#faq`, `#waitlist`.
- [ ] On mobile (<768px), the hamburger menu opens/closes the nav and shows all three links plus the green CTA.
- [ ] Hero contains the exact H1 "Validate Your Startup Idea Before You Build It" and the exact subtext "AI-assisted MVP platform. Go from napkin sketch to tested prototype in 72 hours. No technical co-founder required."
- [ ] Hero has two buttons: green "Join the Waitlist" (→ #waitlist) and outlined "See How It Works" (→ #features).
- [ ] Features section shows exactly 6 cards with the exact titles: AI Rapid Prototyping, Built-in User Testing, Launch Analytics, Guided Validation, No Code Required, Iterate with Real Data.
- [ ] Pricing section shows exactly 3 tiers: Explorer ($0), Builder ($29/mo with "Most Popular" badge), Team ($79/mo).
- [ ] FAQ section shows exactly 6 expandable questions, all using semantic `<details>`/`<summary>`.
- [ ] CTA section has navy background, H2 "Stop Guessing. Start Validating.", an email input, and a green button.
- [ ] Waitlist email form validates client-side (empty/invalid → red border + helper text) and shows a success state on valid submit.
- [ ] Footer shows "© 2026 Uncle Inc." and links to "#" for Privacy and Terms.
- [ ] **No fake testimonials, no fake logos, no fake user counts, no fake metrics anywhere on the page.** The only number shown is the honest "0 founders" in the waitlist subtitle.
- [ ] Page is keyboard-navigable: tab order is logical, focus rings are visible, FAQ accordions expand/collapse with Enter/Space.
- [ ] All colors used in components come from the Tailwind config (no inline hex values except in the config itself).
- [ ] All icons are inline SVG; no external icon library or image assets are required.

FILES: ["package.json", "next.config.js", "tsconfig.json", "tailwind.config.ts", "postcss.config.js", "app/layout.tsx", "app/globals.css", "app/page.tsx", "components/Nav.tsx", "components/Hero.tsx", "components/Features.tsx", "components/Pricing.tsx", "components/FAQ.tsx", "components/CTA.tsx", "components/Footer.tsx"]