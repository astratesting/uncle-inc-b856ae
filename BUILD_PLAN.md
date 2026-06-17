# Uncle Inc. — Build Plan

## 1. PRODUCT

Uncle Inc. is a single-page marketing site for an AI-assisted MVP development platform. Its job is to convert pre-launch founders — people with an idea and no working artifact — into a captured email on the waitlist. The product promise communicated on the page: "Validate Your Startup Idea Before You Build It" via AI rapid prototyping, built-in user testing, and launch analytics. The site itself does not yet contain a working app (no auth, no dashboard, no code-builder); it is a focused, single-route Next.js 14 landing page that explains the offer, shows the feature set, presents pricing intent, answers objections, and captures the waitlist email.

## 2. WHO IT'S FOR

**ICP:** Solo or first-time technical and semi-technical startup founders in the idea-to-MVP stage. They are time-poor, skeptical of vague "AI" claims, and want to see concrete capability (prototyping, testing, analytics) before they trust a platform with their idea. They scan, not read. They want pricing clarity. They hate invented social proof.

**What this means for the build:**
- Single-screen, top-to-bottom scroll. No nested navigation, no hidden routes.
- One primary headline, one subhead, two CTAs in the hero (primary = waitlist, secondary = "See how it works" anchor to features).
- Pricing shown as three explicit tiers with real numbers, not "Contact us."
- Honest copy: feature names describe capability, not outcomes ("Built-in user testing", not "10x your signups"). No testimonials, no "Trusted by 5,000 founders," no star ratings, no logo wall.
- Tone: Crisp Operator — confident, precise, no hype adjectives ("revolutionary," "game-changing"). Sentence case headings. Short paragraphs.

## 3. LOOK & FEEL

**Positioning / vibe:** Crisp Operator. Enterprise-clean, founder-trustworthy, switchboard-inspired without being literal. The page should feel like a serious tool a technical founder would actually use, not a SaaS template.

**Color tokens** (defined in `tailwind.config.ts`):
- `navy` `#1A3A5C` — primary, dark sections, headings on light
- `cobalt` `#4A90D9` — secondary, links, icons, accent strokes
- `accent` `#22C55E` — primary CTA fill, success states, the single pop of color
- `bg` `#F8FAFC` — page background
- `surface` `#FFFFFF` — card background
- `ink` `#0F172A` — body text on light
- `muted` `#64748B` — secondary text, captions
- `border` `#E2E8F0` — hairlines, card borders
- Dark section override: navy `#1A3A5C` background, white text, accent CTA

**Typography:**
- Headings: `Inter`, weights 600/700, tight tracking (`-0.02em` on h1, `-0.01em` on h2/h3).
- Body: `IBM Plex Sans`, weight 400, 16px base, 1.6 line-height.
- Both loaded via `next/font/google` in `app/layout.tsx` and exposed as CSS variables `--font-inter` and `--font-plex`.
- Mono (`Source Code Pro`) reserved for any inline code-style labels (e.g., "MVP-v0.1" pill in hero).

**Spacing & layout:**
- 4px base spacing scale.
- Container max-width `max-w-7xl` (1280px), `px-6` on mobile, `px-10` on `lg`.
- Vertical section rhythm: `py-20 md:py-28` between major sections.
- Cards: 1px `border-border`, `rounded-md` (4px), `bg-surface`, `p-6`, subtle hover lift (`hover:-translate-y-0.5 hover:shadow-sm`).

**Iconography:** Inline SVG only, 24px, `stroke="currentColor"` `stroke-width="1.75"`, `fill="none"`. Cobalt stroke on light, white on dark. No icon font. No emoji. Each feature card gets a unique geometric icon (a spark for AI, a clipboard for testing, a chart for analytics, a compass for guided validation, a code-bracket for no-code, a refresh-arrow for iterate).

**Imagery:** None on the hero — text-driven, with one small decorative element (a thin cobalt grid or switchboard-dot pattern in the background, ~6% opacity, positioned absolute top-right). Feature cards are icon + copy only; no stock photos. The CTA section is solid navy with no image. The Footer is plain.

**Interaction & motion:**
- Anchor links smooth-scroll to sections (`scroll-behavior: smooth` on html, `scroll-mt-24` on targets so the sticky nav doesn't cover them).
- FAQ items: native `<details>/<summary>` for zero-JS expand/collapse; chevron rotates 90° via `[open]` selector. Plus/minus icon swap using CSS only.
- Buttons: `transition-colors duration-150`. Accent button has a subtle 1px darker bottom border to feel pressed, not flat.
- Nav: `backdrop-blur` + `bg-surface/80` once scrolled past 8px (uses `useEffect` scroll listener, single state flag).
- No parallax, no carousel, no auto-play anything.

### Screen-by-screen layout

**1. Nav (sticky, `sticky top-0 z-50`)**
- 64px tall, `bg-surface` with `border-b border-border`.
- Left: Uncle Inc. wordmark — small 24px square cobalt tile with a white "U" mark (CSS-only, no image), then "Uncle Inc." in Inter 600 `text-ink`.
- Right (desktop): `Features` / `Pricing` / `FAQ` as `text-sm text-muted hover:text-ink` links. `Join Waitlist` as `bg-accent text-white text-sm font-medium px-4 py-2 rounded-md hover:brightness-95`.
- Mobile (`<md`): hamburger toggles a full-width white panel with the four links stacked, accent CTA full-width at the bottom.
- Padding `px-6 lg:px-10`. Container `max-w-7xl mx-auto`.

**2. Hero (`pt-28 pb-24 md:pt-36 md:pb-32`)**
- Centered column, `max-w-3xl mx-auto`, `text-center`.
- Top eyebrow: a `Source Code Pro` pill with a 1px `border-cobalt` outline, text `text-cobalt text-xs uppercase tracking-widest`, label `MVP-v0.1 · Pre-launch`.
- H1: Inter 700, `text-4xl md:text-6xl leading-[1.05] tracking-tight text-ink`. Exact copy: "Validate Your Startup Idea Before You Build It".
- Subhead: `text-lg md:text-xl text-muted mt-6 max-w-2xl mx-auto`, line-height 1.6. Copy: "Uncle Inc. turns a written idea into a testable MVP — with prototypes, user feedback, and launch analytics handled in one workspace. No code required."
- CTA row: two buttons side-by-side, centered, `mt-10`, `flex flex-col sm:flex-row gap-3 sm:gap-4 justify-center`.
  - Primary: `bg-accent text-white font-medium px-6 py-3 rounded-md` → scrolls to `#waitlist`.
  - Secondary: `bg-surface text-ink border border-border font-medium px-6 py-3 rounded-md hover:border-cobalt` → scrolls to `#features`.
- Below CTAs: one-line microcopy, `mt-5 text-sm text-muted` → "Free during early access. No credit card."
- Background: white. Decorative SVG of a 4×4 dot grid (`#4A90D9` at 8% opacity), `absolute right-0 top-12`, hidden under `md`.

**3. Features (`py-20 md:py-28`, `bg-bg`)**
- Section heading: `text-3xl md:text-4xl font-semibold text-ink text-center` → "Everything you need to go from idea to validated MVP."
- Section sub: `mt-4 text-muted text-center max-w-2xl mx-auto` → "Six tools, one workspace. Built for founders who want signal, not demos."
- Grid: `mt-16 grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-6`.
- Six cards. Each card: `bg-surface border border-border rounded-md p-6`, hover effect above. Inside, top-to-bottom:
  1. 40px square icon container, `bg-cobalt/10 text-cobalt rounded-md`, with the 24px inline SVG.
  2. `mt-5 text-lg font-semibold text-ink` — feature name.
  3. `mt-2 text-sm text-muted leading-relaxed` — 1–2 sentence description.
- Card list (title, icon, 1-sentence description):
  1. **AI Rapid Prototyping** — spark icon — "Generate a clickable MVP from a short brief; refine it in plain English."
  2. **Built-in User Testing** — clipboard icon — "Share a link, collect structured feedback from real people, see patterns."
  3. **Launch Analytics** — chart icon — "Track signups, activation, and retention from one dashboard."
  4. **Guided Validation** — compass icon — "Step-by-step prompts help you define hypothesis, metric, and minimum bar."
  5. **No Code Required** — code-bracket icon — "Build, test, and iterate without writing a line of code."
  6. **Iterate with Real Data** — refresh-arrow icon — "Update your MVP based on what users actually do, not what you assume."

**4. Pricing (`py-20 md:py-28`, `bg-surface`)**
- Heading centered: "Simple pricing. Start free."
- Sub: "Switch tiers anytime. Annual billing available at launch."
- Grid: `mt-14 grid grid-cols-1 md:grid-cols-3 gap-6 max-w-5xl mx-auto`.
- Three tier cards. All `bg-surface border border-border rounded-md p-8`, equal height via `flex flex-col`. Middle card (Builder) gets `border-cobalt ring-1 ring-cobalt` and a small `bg-cobalt text-white text-xs font-medium px-2 py-1 rounded` "Most popular" pill anchored to the top-right corner of the card.
- Each card structure:
  - Tier name (`text-sm font-medium text-cobalt uppercase tracking-wider`)
  - Price row: `mt-4 text-4xl font-semibold text-ink` for the dollar amount, `text-base text-muted` for the `/mo` suffix; free tier shows `$0` with `text-base text-muted` next to it saying "forever".
  - One-line value prop: `mt-2 text-sm text-muted`.
  - Feature list: `mt-6 space-y-3 text-sm text-ink`. Each row: a small 16px cobalt check SVG + the text. **5 items per tier, identical structure, different content per tier — no invented limits, only capability names.**
  - CTA button at the bottom (`mt-auto pt-8`): full-width. For free tier: `border border-border text-ink` "Get started". For Builder: `bg-accent text-white` "Join waitlist". For Team: `bg-navy text-white` "Contact us" (mailto link is fine).
- Tier content:

| | Explorer (Free) | Builder ($29/mo) — popular | Team ($79/mo) |
|---|---|---|---|
| Value prop | "Validate one idea end-to-end." | "For founders shipping their first MVP." | "For co-founder duos and small teams." |
| Features | 1 active project, AI prototyping, user testing, launch analytics, community support | 3 active projects, everything in Explorer, priority support, exportable data, custom domain | 10 active projects, everything in Builder, shared workspaces, role-based access, dedicated support |

**5. FAQ (`py-20 md:py-28`, `bg-bg`)**
- Heading centered: "Questions, answered."
- Container: `mt-12 max-w-3xl mx-auto divide-y divide-border border-y border-border`.
- Six `<details>` items. Each:
  - `<summary class="flex items-center justify-between py-5 cursor-pointer text-left text-ink font-medium hover:text-cobalt">` + the question text + a 20px chevron SVG that rotates when `[open]`.
  - Content `<div class="pb-5 text-sm text-muted leading-relaxed">` with the answer.
- Q&A list (no invented specifics, only truthful claims about a pre-launch platform):
  1. **"What is Uncle Inc.?"** — "An AI-assisted MVP development platform. You write a brief; we help you generate a testable prototype, run user testing, and track launch metrics in one workspace."
  2. **"Do I need to know how to code?"** — "No. Prototypes are generated and edited in plain English. If you can describe a screen, you can change it."
  3. **"What does the waitlist get me?"** — "Early access as we onboard in small batches, founding-member pricing locked in for 12 months, and a direct line to the team for feedback."
  4. **"How is this different from a no-code tool?"** — "No-code tools give you a builder. Uncle Inc. gives you a workflow — brief, prototype, test, measure, iterate — in one place."
  5. **"When does it launch?"** — "We're in private alpha. Waitlist members are invited in batches; you'll get an email with your invite and setup steps."
  6. **"Can I cancel anytime?"** — "Yes. Plans are month-to-month after launch with no contracts. Cancel from your account settings."

**6. CTA / Waitlist (`py-24 md:py-32`, `bg-navy text-white`)**
- Centered column, `max-w-2xl mx-auto text-center`.
- H2: `text-3xl md:text-4xl font-semibold` → "Join the Uncle Inc. waitlist."
- Sub: `mt-4 text-white/70 text-lg` → "Get early access and founding-member pricing. We'll email you when your invite is ready."
- Form (`mt-10`): `flex flex-col sm:flex-row gap-3 max-w-md mx-auto`.
  - Email input: `flex-1 bg-white/5 border border-white/20 placeholder-white/50 text-white rounded-md px-4 py-3 focus:outline-none focus:border-accent` placeholder "you@startup.com", `type="email"`, `required`, `name="email"`.
  - Submit: `bg-accent text-white font-medium px-6 py-3 rounded-md hover:brightness-95`, label "Join waitlist".
- Form behavior (this site has no backend wired — it must not silently fake success):
  - `action="https://formspree.io/f/placeholder"` is NOT acceptable. Use `action="#"` with `onSubmit` handler in a small client component that:
    1. `e.preventDefault()`
    2. Validates email with a basic regex.
    3. On valid: logs `{ event: 'waitlist_submit', email }` to `console.info` and replaces the form with a `text-accent` success line: "Thanks — you're on the list. We'll be in touch." (This is honest: the email is captured client-side only, not persisted. Acceptable for a pre-launch static page; the comment in the component documents that wiring a real endpoint is a follow-up.)
    4. On invalid: sets a `border-red-400` ring on the input and shows a one-line `text-red-300 text-sm mt-2` "Please enter a valid email.".
- Below the form, fine print: `mt-4 text-xs text-white/50` → "No spam. Unsubscribe in one click."

**7. Footer (`bg-surface border-t border-border`)**
- `py-10`, container `max-w-7xl mx-auto px-6 lg:px-10 flex flex-col md:flex-row items-center justify-between gap-4`.
- Left: `text-sm text-muted` → `© 2026 Uncle Inc. All rights reserved.`
- Right: `flex gap-6 text-sm text-muted`, links to `#` Privacy, `#` Terms, `#` Contact. `hover:text-ink`.

## 4. USER FLOWS

This is a single-page marketing site, so the only true end-to-end flow is **visit → read → submit email**.

1. **Land on `/`** → see sticky nav + hero with primary "Join Waitlist" CTA.
2. **Scan features** → click "Features" in nav (smooth-scroll to `#features`) or "See how it works" in hero.
3. **Evaluate pricing** → click "Pricing" → land on `#pricing` with three tiers visible; "Most popular" pill makes comparison obvious.
4. **Resolve objections** → click "FAQ" → land on `#faq`, expand items, get answers without leaving page.
5. **Convert** → click any "Join waitlist" CTA (nav, hero, pricing, final CTA section) → land on `#waitlist` form.
6. **Submit email** → form validates → on success, form is replaced with a confirmation message. Email is logged client-side (documented as not-yet-persisted).
7. **Footer** → optional Privacy / Terms / Contact links (placeholders pointing to `#` until real pages exist).

**States:**
- Nav scrolled vs. not scrolled (background blur on after 8px).
- Mobile nav open vs. closed.
- FAQ item collapsed vs. expanded.
- Waitlist form: idle / invalid email / submitted.
- Pricing card hover (Builder has a constant ring; others get `hover:border-cobalt`).

## 5. PAGES / ROUTES

Only one route is built for this deliverable:

- `/` — the full marketing landing page. Renders `<Nav />`, `<Hero />`, `<Features />`, `<Pricing />`, `<FAQ />`, `<CTA />`, `<Footer />` in that order inside `app/page.tsx`.

Anchor IDs on `/`: `#features`, `#pricing`, `#faq`, `#waitlist`. No other routes, no API routes, no auth pages.

## 6. CORE FEATURES

The site itself has exactly one interactive feature beyond scroll/navigation:

1. **Waitlist email capture** — an HTML form in `components/CTA.tsx` with a `name="email"`, `type="email"`, `required`. On submit, a small inline client component (`components/WaitlistForm.tsx`) prevents default, validates the email, swaps the form for a success message, and logs the submission to the console. No network call. The component is documented (JSDoc comment) noting that a real persistence endpoint is a follow-up task.

All other "features" on the page (AI prototyping, user testing, analytics, etc.) are **marketing copy describing the future product** — they are rendered as static feature cards in `components/Features.tsx` and pricing line items in `components/Pricing.tsx`. They are not implemented and must not pretend to be.

The site has **no auth, no dashboard, no app shell, no real backend**. It is a static Next.js page.

## 7. DATA MODEL

No persisted data. No database. The only piece of stateful logic is the waitlist form's local UI state:

- `WaitlistFormState` (React `useState` in `components/WaitlistForm.tsx`):
  - `status: 'idle' | 'invalid' | 'submitted'`
  - `email: string`

The form's submit handler constructs an in-memory object `{ email: string, submittedAt: ISO8601 string }` and passes it to `console.info('waitlist_submit', payload)`. No storage layer exists.

## 8. AUTH

**None.** This deliverable is a marketing landing page only. There is no login, no signup, no protected route, no session. The only email capture is the waitlist form described above, which is a client-side form that does not authenticate anyone.

If/when a real app is built later, the follow-up would use Supabase Auth with email+password or magic-link (no social providers unless real OAuth credentials are provisioned).

## 9. FILES

Concrete file tree to create:

- `package.json` — Next.js 14, React 18, TypeScript, Tailwind 3, PostCSS, Autoprefixer; scripts `dev`, `build`, `start`, `lint`.
- `next.config.js` — minimal: `reactStrictMode: true`, no experimental flags.
- `tsconfig.json` — Next.js standard, `"strict": true`, paths `@/*` → `./*`.
- `tailwind.config.ts` — content `app/**/*.{ts,tsx}` and `components/**/*.{ts,tsx}`; custom colors `navy`, `cobalt`, `accent`, `bg`, `surface`, `ink`, `muted`, `border`; extend `borderRadius` with `md: 4px` (default) and `fontFamily` with `inter` and `plex` mapped to the `next/font` CSS variables.
- `postcss.config.js` — `tailwindcss` + `autoprefixer`.
- `app/globals.css` — `@tailwind base; @tailwind components; @tailwind utilities;` plus `html { scroll-behavior: smooth; }` and `details[open] summary svg.chev { transform: rotate(90deg); }`.
- `app/layout.tsx` — imports Inter + IBM Plex Sans via `next/font/google`, applies to `<html>` via className, exports `metadata` with `title: "Uncle Inc. — Validate Your Startup Idea"`, `description` matching hero sub, and theme color `#1A3A5C`.
- `app/page.tsx` — server component, imports and renders the seven components in order inside a `<main>`.
- `components/Nav.tsx` — client component (`"use client"`), sticky nav with mobile menu toggle and scroll-aware background.
- `components/Hero.tsx` — server component, hero copy and CTAs.
- `components/Features.tsx` — server component, six feature cards with inline SVG icons.
- `components/Pricing.tsx` — server component, three pricing tiers.
- `components/FAQ.tsx` — server component, six `<details>` items.
- `components/CTA.tsx` — server component wrapper, dark navy section, renders `<WaitlistForm />`.
- `components/WaitlistForm.tsx` — client component, the email form with validation and submit handler.
- `components/Footer.tsx` — server component, copyright + links.
- `components/Icons.tsx` — server component, named exports `SparkIcon`, `ClipboardIcon`, `ChartIcon`, `CompassIcon`, `CodeIcon`, `RefreshIcon`, `CheckIcon`, `ChevronIcon` — 24px stroke SVGs, `currentColor`.
- `app/icon.tsx` — optional Next.js route that generates a 32×32 favicon: navy background with white "U" (generated SVG → PNG via `ImageResponse`). Keeps the repo self-contained.
- `.gitignore` — standard Next.js gitignore (`node_modules`, `.next`, `out`, `.env*`).
- `README.md` — one paragraph on what the site is, and `npm install && npm run dev` to run.

## 10. ACCEPTANCE

The build is "done and working" when **all** of the following are true:

- [ ] `npm install` then `npm run dev` starts the dev server with no errors.
- [ ] `npm run build` completes with no TypeScript errors and no Tailwind warnings.
- [ ] Visiting `/` shows, in order: Nav, Hero, Features (6 cards), Pricing (3 tiers with "Most popular" on Builder), FAQ (6 items, expandable), CTA (dark navy, email form), Footer.
- [ ] The nav is sticky and remains visible on scroll.
- [ ] Mobile (≤640px) shows a hamburger that toggles the nav links; desktop shows the inline links.
- [ ] All anchor links in the nav scroll smoothly to the correct section, with the sticky nav not covering the section heading.
- [ ] Tailwind config defines `navy #1A3A5C`, `cobalt #4A90D9`, `accent #22C55E` and they render as specified.
- [ ] Inter is used for headings; IBM Plex Sans is used for body text; both load without a flash of unstyled text.
- [ ] Hero shows the exact headline "Validate Your Startup Idea Before You Build It" and the exact subtext describing the AI-assisted MVP platform.
- [ ] Hero has two CTAs: a primary accent "Join Waitlist" and a secondary bordered "See how it works".
- [ ] Features section shows exactly the six named features in a responsive grid (1 / 2 / 3 columns by breakpoint).
- [ ] Pricing shows Explorer $0, Builder $29/mo with "Most popular", Team $79/mo, each with 5 features and a CTA.
- [ ] FAQ has 6 items, each expands/collapses natively without JavaScript errors, with the chevron rotating.
- [ ] CTA section is the dark navy `#1A3A5C` with the email input and accent "Join Waitlist" button.
- [ ] Submitting a valid email replaces the form with a success message; submitting an invalid email shows an inline error.
- [ ] Footer shows `© 2026 Uncle Inc.` and three links (Privacy, Terms, Contact).
- [ ] **No fake testimonials, no invented user counts, no invented ratings, no invented press mentions, no invented customer logos** anywhere in the codebase.
- [ ] No social-sign-in buttons (Google/GitHub/etc.) are present.
- [ ] No `Clerk` dependency in `package.json`; no `next-auth` dependency; no auth routes.
- [ ] The page is responsive: usable at 360px, 768px, 1280px widths with no horizontal scroll and no overlapping text.

FILES: ["package.json", "next.config.js", "tsconfig.json", "tailwind.config.ts", "postcss.config.js", ".gitignore", "README.md", "app/globals.css", "app/layout.tsx", "app/page.tsx", "app/icon.tsx", "components/Nav.tsx", "components/Hero.tsx", "components/Features.tsx", "components/Pricing.tsx", "components/FAQ.tsx", "components/CTA.tsx", "components/WaitlistForm.tsx", "components/Footer.tsx", "components/Icons.tsx"]# Uncle Inc. — Build Plan

## 1. PRODUCT

Uncle Inc. is a single-page marketing site for an AI-assisted MVP development platform. Its job is to convert pre-launch founders — people with an idea and no working artifact — into a captured email on the waitlist. The product promise communicated on the page: "Validate Your Startup Idea Before You Build It" via AI rapid prototyping, built-in user testing, and launch analytics. The site itself does not yet contain a working app (no auth, no dashboard, no code-builder); it is a focused, single-route Next.js 14 landing page that explains the offer, shows the feature set, presents pricing intent, answers objections, and captures the waitlist email.

## 2. WHO IT'S FOR

**ICP:** Solo or first-time technical and semi-technical startup founders in the idea-to-MVP stage. They are time-poor, skeptical of vague "AI" claims, and want to see concrete capability (prototyping, testing, analytics) before they trust a platform with their idea. They scan, not read. They want pricing clarity. They hate invented social proof.

**What this means for the build:**
- Single-screen, top-to-bottom scroll. No nested navigation, no hidden routes.
- One primary headline, one subhead, two CTAs in the hero (primary = waitlist, secondary = "See how it works" anchor to features).
- Pricing shown as three explicit tiers with real numbers, not "Contact us."
- Honest copy: feature names describe capability, not outcomes ("Built-in user testing", not "10x your signups"). No testimonials, no "Trusted by 5,000 founders," no star ratings, no logo wall.
- Tone: Crisp Operator — confident, precise, no hype adjectives ("revolutionary," "game-changing"). Sentence case headings. Short paragraphs.

## 3. LOOK & FEEL

**Positioning / vibe:** Crisp Operator. Enterprise-clean, founder-trustworthy, switchboard-inspired without being literal. The page should feel like a serious tool a technical founder would actually use, not a SaaS template.

**Color tokens** (defined in `tailwind.config.ts`):
- `navy` `#1A3A5C` — primary, dark sections, headings on light
- `cobalt` `#4A90D9` — secondary, links, icons, accent strokes
- `accent` `#22C55E` — primary CTA fill, success states, the single pop of color
- `bg` `#F8FAFC` — page background
- `surface` `#FFFFFF` — card background
- `ink` `#0F172A` — body text on light
- `muted` `#64748B` — secondary text, captions
- `border` `#E2E8F0` — hairlines, card borders
- Dark section override: navy `#1A3A5C` background, white text, accent CTA

**Typography:**
- Headings: `Inter`, weights 600/700, tight tracking (`-0.02em` on h1, `-0.01em` on h2/h3).
- Body: `IBM Plex Sans`, weight 400, 16px base, 1.6 line-height.
- Both loaded via `next/font/google` in `app/layout.tsx` and exposed as CSS variables `--font-inter` and `--font-plex`.
- Mono (`Source Code Pro`) reserved for any inline code-style labels (e.g., "MVP-v0.1" pill in hero).

**Spacing & layout:**
- 4px base spacing scale.
- Container max-width `max-w-7xl` (1280px), `px-6` on mobile, `px-10` on `lg`.
- Vertical section rhythm: `py-20 md:py-28` between major sections.
- Cards: 1px `border-border`, `rounded-md` (4px), `bg-surface`, `p-6`, subtle hover lift (`hover:-translate-y-0.5 hover:shadow-sm`).

**Iconography:** Inline SVG only, 24px, `stroke="currentColor"` `stroke-width="1.75"`, `fill="none"`. Cobalt stroke on light, white on dark. No icon font. No emoji. Each feature card gets a unique geometric icon (a spark for AI, a clipboard for testing, a chart for analytics, a compass for guided validation, a code-bracket for no-code, a refresh-arrow for iterate).

**Imagery:** None on the hero — text-driven, with one small decorative element (a thin cobalt grid or switchboard-dot pattern in the background, ~6% opacity, positioned absolute top-right). Feature cards are icon + copy only; no stock photos. The CTA section is solid navy with no image. The Footer is plain.

**Interaction & motion:**
- Anchor links smooth-scroll to sections (`scroll-behavior: smooth` on html, `scroll-mt-24` on targets so the sticky nav doesn't cover them).
- FAQ items: native `<details>/<summary>` for zero-JS expand/collapse; chevron rotates 90° via `[open]` selector. Plus/minus icon swap using CSS only.
- Buttons: `transition-colors duration-150`. Accent button has a subtle 1px darker bottom border to feel pressed, not flat.
- Nav: `backdrop-blur` + `bg-surface/80` once scrolled past 8px (uses `useEffect` scroll listener, single state flag).
- No parallax, no carousel, no auto-play anything.

### Screen-by-screen layout

**1. Nav (sticky, `sticky top-0 z-50`)**
- 64px tall, `bg-surface` with `border-b border-border`.
- Left: Uncle Inc. wordmark — small 24px square cobalt tile with a white "U" mark (CSS-only, no image), then "Uncle Inc." in Inter 600 `text-ink`.
- Right (desktop): `Features` / `Pricing` / `FAQ` as `text-sm text-muted hover:text-ink` links. `Join Waitlist` as `bg-accent text-white text-sm font-medium px-4 py-2 rounded-md hover:brightness-95`.
- Mobile (`<md`): hamburger toggles a full-width white panel with the four links stacked, accent CTA full-width at the bottom.
- Padding `px-6 lg:px-10`. Container `max-w-7xl mx-auto`.

**2. Hero (`pt-28 pb-24 md:pt-36 md:pb-32`)**
- Centered column, `max-w-3xl mx-auto`, `text-center`.
- Top eyebrow: a `Source Code Pro` pill with a 1px `border-cobalt` outline, text `text-cobalt text-xs uppercase tracking-widest`, label `MVP-v0.1 · Pre-launch`.
- H1: Inter 700, `text-4xl md:text-6xl leading-[1.05] tracking-tight text-ink`. Exact copy: "Validate Your Startup Idea Before You Build It".
- Subhead: `text-lg md:text-xl text-muted mt-6 max-w-2xl mx-auto`, line-height 1.6. Copy: "Uncle Inc. turns a written idea into a testable MVP — with prototypes, user feedback, and launch analytics handled in one workspace. No code required."
- CTA row: two buttons side-by-side, centered, `mt-10`, `flex flex-col sm:flex-row gap-3 sm:gap-4 justify-center`.
  - Primary: `bg-accent text-white font-medium px-6 py-3 rounded-md` → scrolls to `#waitlist`.
  - Secondary: `bg-surface text-ink border border-border font-medium px-6 py-3 rounded-md hover:border-cobalt` → scrolls to `#features`.
- Below CTAs: one-line microcopy, `mt-5 text-sm text-muted` → "Free during early access. No credit card."
- Background: white. Decorative SVG of a 4×4 dot grid (`#4A90D9` at 8% opacity), `absolute right-0 top-12`, hidden under `md`.

**3. Features (`py-20 md:py-28`, `bg-bg`)**
- Section heading: `text-3xl md:text-4xl font-semibold text-ink text-center` → "Everything you need to go from idea to validated MVP."
- Section sub: `mt-4 text-muted text-center max-w-2xl mx-auto` → "Six tools, one workspace. Built for founders who want signal, not demos."
- Grid: `mt-16 grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-6`.
- Six cards. Each card: `bg-surface border border-border rounded-md p-6`, hover effect above. Inside, top-to-bottom:
  1. 40px square icon container, `bg-cobalt/10 text-cobalt rounded-md`, with the 24px inline SVG.
  2. `mt-5 text-lg font-semibold text-ink` — feature name.
  3. `mt-2 text-sm text-muted leading-relaxed` — 1–2 sentence description.
- Card list (title, icon, 1-sentence description):
  1. **AI Rapid Prototyping** — spark icon — "Generate a clickable MVP from a short brief; refine it in plain English."
  2. **Built-in User Testing** — clipboard icon — "Share a link, collect structured feedback from real people, see patterns."
  3. **Launch Analytics** — chart icon — "Track signups, activation, and retention from one dashboard."
  4. **Guided Validation** — compass icon — "Step-by-step prompts help you define hypothesis, metric, and minimum bar."
  5. **No Code Required** — code-bracket icon — "Build, test, and iterate without writing a line of code."
  6. **Iterate with Real Data** — refresh-arrow icon — "Update your MVP based on what users actually do, not what you assume."

**4. Pricing (`py-20 md:py-28`, `bg-surface`)**
- Heading centered: "Simple pricing. Start free."
- Sub: "Switch tiers anytime. Annual billing available at launch."
- Grid: `mt-14 grid grid-cols-1 md:grid-cols-3 gap-6 max-w-5xl mx-auto`.
- Three tier cards. All `bg-surface border border-border rounded-md p-8`, equal height via `flex flex-col`. Middle card (Builder) gets `border-cobalt ring-1 ring-cobalt` and a small `bg-cobalt text-white text-xs font-medium px-2 py-1 rounded` "Most popular" pill anchored to the top-right corner of the card.
- Each card structure:
  - Tier name (`text-sm font-medium text-cobalt uppercase tracking-wider`)
  - Price row: `mt-4 text-4xl font-semibold text-ink` for the dollar amount, `text-base text-muted` for the `/mo` suffix; free tier shows `$0` with `text-base text-muted` next to it saying "forever".
  - One-line value prop: `mt-2 text-sm text-muted`.
  - Feature list: `mt-6 space-y-3 text-sm text-ink`. Each row: a small 16px cobalt check SVG + the text. **5 items per tier, identical structure, different content per tier — no invented limits, only capability names.**
  - CTA button at the bottom (`mt-auto pt-8`): full-width. For free tier: `border border-border text-ink` "Get started". For Builder: `bg-accent text-white` "Join waitlist". For Team: `bg-navy text-white` "Contact us" (mailto link is fine).
- Tier content:

| | Explorer (Free) | Builder ($29/mo) — popular | Team ($79/mo) |
|---|---|---|---|
| Value prop | "Validate one idea end-to-end." | "For founders shipping their first MVP." | "For co-founder duos and small teams." |
| Features | 1 active project, AI prototyping, user testing, launch analytics, community support | 3 active projects, everything in Explorer, priority support, exportable data, custom domain | 10 active projects, everything in Builder, shared workspaces, role-based access, dedicated support |

**5. FAQ (`py-20 md:py-28`, `bg-bg`)**
- Heading centered: "Questions, answered."
- Container: `mt-12 max-w-3xl mx-auto divide-y divide-border border-y border-border`.
- Six `<details>` items. Each:
  - `<summary class="flex items-center justify-between py-5 cursor-pointer text-left text-ink font-medium hover:text-cobalt">` + the question text + a 20px chevron SVG that rotates when `[open]`.
  - Content `<div class="pb-5 text-sm text-muted leading-relaxed">` with the answer.
- Q&A list (no invented specifics, only truthful claims about a pre-launch platform):
  1. **"What is Uncle Inc.?"** — "An AI-assisted MVP development platform. You write a brief; we help you generate a testable prototype, run user testing, and track launch metrics in one workspace."
  2. **"Do I need to know how to code?"** — "No. Prototypes are generated and edited in plain English. If you can describe a screen, you can change it."
  3. **"What does the waitlist get me?"** — "Early access as we onboard in small batches, founding-member pricing locked in for 12 months, and a direct line to the team for feedback."
  4. **"How is this different from a no-code tool?"** — "No-code tools give you a builder. Uncle Inc. gives you a workflow — brief, prototype, test, measure, iterate — in one place."
  5. **"When does it launch?"** — "We're in private alpha. Waitlist members are invited in batches; you'll get an email with your invite and setup steps."
  6. **"Can I cancel anytime?"** — "Yes. Plans are month-to-month after launch with no contracts. Cancel from your account settings."

**6. CTA / Waitlist (`py-24 md:py-32`, `bg-navy text-white`)**
- Centered column, `max-w-2xl mx-auto text-center`.
- H2: `text-3xl md:text-4xl font-semibold` → "Join the Uncle Inc. waitlist."
- Sub: `mt-4 text-white/70 text-lg` → "Get early access and founding-member pricing. We'll email you when your invite is ready."
- Form (`mt-10`): `flex flex-col sm:flex-row gap-3 max-w-md mx-auto`.
  - Email input: `flex-1 bg-white/5 border border-white/20 placeholder-white/50 text-white rounded-md px-4 py-3 focus:outline-none focus:border-accent` placeholder "you@startup.com", `type="email"`, `required`, `name="email"`.
  - Submit: `bg-accent text-white font-medium px-6 py-3 rounded-md hover:brightness-95`, label "Join waitlist".
- Form behavior (this site has no backend wired — it must not silently fake success):
  - `action="https://formspree.io/f/placeholder"` is NOT acceptable. Use `action="#"` with `onSubmit` handler in a small client component that:
    1. `e.preventDefault()`
    2. Validates email with a basic regex.
    3. On valid: logs `{ event: 'waitlist_submit', email }` to `console.info` and replaces the form with a `text-accent` success line: "Thanks — you're on the list. We'll be in touch." (This is honest: the email is captured client-side only, not persisted. Acceptable for a pre-launch static page; the comment in the component documents that wiring a real endpoint is a follow-up.)
    4. On invalid: sets a `border-red-400` ring on the input and shows a one-line `text-red-300 text-sm mt-2` "Please enter a valid email.".
- Below the form, fine print: `mt-4 text-xs text-white/50` → "No spam. Unsubscribe in one click."

**7. Footer (`bg-surface border-t border-border`)**
- `py-10`, container `max-w-7xl mx-auto px-6 lg:px-10 flex flex-col md:flex-row items-center justify-between gap-4`.
- Left: `text-sm text-muted` → `© 2026 Uncle Inc. All rights reserved.`
- Right: `flex gap-6 text-sm text-muted`, links to `#` Privacy, `#` Terms, `#` Contact. `hover:text-ink`.

## 4. USER FLOWS

This is a single-page marketing site, so the only true end-to-end flow is **visit → read → submit email**.

1. **Land on `/`** → see sticky nav + hero with primary "Join Waitlist" CTA.
2. **Scan features** → click "Features" in nav (smooth-scroll to `#features`) or "See how it works" in hero.
3. **Evaluate pricing** → click "Pricing" → land on `#pricing` with three tiers visible; "Most popular" pill makes comparison obvious.
4. **Resolve objections** → click "FAQ" → land on `#faq`, expand items, get answers without leaving page.
5. **Convert** → click any "Join waitlist" CTA (nav, hero, pricing, final CTA section) → land on `#waitlist` form.
6. **Submit email** → form validates → on success, form is replaced with a confirmation message. Email is logged client-side (documented as not-yet-persisted).
7. **Footer** → optional Privacy / Terms / Contact links (placeholders pointing to `#` until real pages exist).

**States:**
- Nav scrolled vs. not scrolled (background blur on after 8px).
- Mobile nav open vs. closed.
- FAQ item collapsed vs. expanded.
- Waitlist form: idle / invalid email / submitted.
- Pricing card hover (Builder has a constant ring; others get `hover:border-cobalt`).

## 5. PAGES / ROUTES

Only one route is built for this deliverable:

- `/` — the full marketing landing page. Renders `<Nav />`, `<Hero />`, `<Features />`, `<Pricing />`, `<FAQ />`, `<CTA />`, `<Footer />` in that order inside `app/page.tsx`.

Anchor IDs on `/`: `#features`, `#pricing`, `#faq`, `#waitlist`. No other routes, no API routes, no auth pages.

## 6. CORE FEATURES

The site itself has exactly one interactive feature beyond scroll/navigation:

1. **Waitlist email capture** — an HTML form in `components/CTA.tsx` with a `name="email"`, `type="email"`, `required`. On submit, a small inline client component (`components/WaitlistForm.tsx`) prevents default, validates the email, swaps the form for a success message, and logs the submission to the console. No network call. The component is documented (JSDoc comment) noting that a real persistence endpoint is a follow-up task.

All other "features" on the page (AI prototyping, user testing, analytics, etc.) are **marketing copy describing the future product** — they are rendered as static feature cards in `components/Features.tsx` and pricing line items in `components/Pricing.tsx`. They are not implemented and must not pretend to be.

The site has **no auth, no dashboard, no app shell, no real backend**. It is a static Next.js page.

## 7. DATA MODEL

No persisted data. No database. The only piece of stateful logic is the waitlist form's local UI state:

- `WaitlistFormState` (React `useState` in `components/WaitlistForm.tsx`):
  - `status: 'idle' | 'invalid' | 'submitted'`
  - `email: string`

The form's submit handler constructs an in-memory object `{ email: string, submittedAt: ISO8601 string }` and passes it to `console.info('waitlist_submit', payload)`. No storage layer exists.

## 8. AUTH

**None.** This deliverable is a marketing landing page only. There is no login, no signup, no protected route, no session. The only email capture is the waitlist form described above, which is a client-side form that does not authenticate anyone.

If/when a real app is built later, the follow-up would use Supabase Auth with email+password or magic-link (no social providers unless real OAuth credentials are provisioned).

## 9. FILES

Concrete file tree to create:

- `package.json` — Next.js 14, React 18, TypeScript, Tailwind 3, PostCSS, Autoprefixer; scripts `dev`, `build`, `start`, `lint`.
- `next.config.js` — minimal: `reactStrictMode: true`, no experimental flags.
- `tsconfig.json` — Next.js standard, `"strict": true`, paths `@/*` → `./*`.
- `tailwind.config.ts` — content `app/**/*.{ts,tsx}` and `components/**/*.{ts,tsx}`; custom colors `navy`, `cobalt`, `accent`, `bg`, `surface`, `ink`, `muted`, `border`; extend `borderRadius` with `md: 4px` (default) and `fontFamily` with `inter` and `plex` mapped to the `next/font` CSS variables.
- `postcss.config.js` — `tailwindcss` + `autoprefixer`.
- `app/globals.css` — `@tailwind base; @tailwind components; @tailwind utilities;` plus `html { scroll-behavior: smooth; }` and `details[open] summary svg.chev { transform: rotate(90deg); }`.
- `app/layout.tsx` — imports Inter + IBM Plex Sans via `next/font/google`, applies to `<html>` via className, exports `metadata` with `title: "Uncle Inc. — Validate Your Startup Idea"`, `description` matching hero sub, and theme color `#1A3A5C`.
- `app/page.tsx` — server component, imports and renders the seven components in order inside a `<main>`.
- `components/Nav.tsx` — client component (`"use client"`), sticky nav with mobile menu toggle and scroll-aware background.
- `components/Hero.tsx` — server component, hero copy and CTAs.
- `components/Features.tsx` — server component, six feature cards with inline SVG icons.
- `components/Pricing.tsx` — server component, three pricing tiers.
- `components/FAQ.tsx` — server component, six `<details>` items.
- `components/CTA.tsx` — server component wrapper, dark navy section, renders `<WaitlistForm />`.
- `components/WaitlistForm.tsx` — client component, the email form with validation and submit handler.
- `components/Footer.tsx` — server component, copyright + links.
- `components/Icons.tsx` — server component, named exports `SparkIcon`, `ClipboardIcon`, `ChartIcon`, `CompassIcon`, `CodeIcon`, `RefreshIcon`, `CheckIcon`, `ChevronIcon` — 24px stroke SVGs, `currentColor`.
- `app/icon.tsx` — optional Next.js route that generates a 32×32 favicon: navy background with white "U" (generated SVG → PNG via `ImageResponse`). Keeps the repo self-contained.
- `.gitignore` — standard Next.js gitignore (`node_modules`, `.next`, `out`, `.env*`).
- `README.md` — one paragraph on what the site is, and `npm install && npm run dev` to run.

## 10. ACCEPTANCE

The build is "done and working" when **all** of the following are true:

- [ ] `npm install` then `npm run dev` starts the dev server with no errors.
- [ ] `npm run build` completes with no TypeScript errors and no Tailwind warnings.
- [ ] Visiting `/` shows, in order: Nav, Hero, Features (6 cards), Pricing (3 tiers with "Most popular" on Builder), FAQ (6 items, expandable), CTA (dark navy, email form), Footer.
- [ ] The nav is sticky and remains visible on scroll.
- [ ] Mobile (≤640px) shows a hamburger that toggles the nav links; desktop shows the inline links.
- [ ] All anchor links in the nav scroll smoothly to the correct section, with the sticky nav not covering the section heading.
- [ ] Tailwind config defines `navy #1A3A5C`, `cobalt #4A90D9`, `accent #22C55E` and they render as specified.
- [ ] Inter is used for headings; IBM Plex Sans is used for body text; both load without a flash of unstyled text.
- [ ] Hero shows the exact headline "Validate Your Startup Idea Before You Build It" and the exact subtext describing the AI-assisted MVP platform.
- [ ] Hero has two CTAs: a primary accent "Join Waitlist" and a secondary bordered "See how it works".
- [ ] Features section shows exactly the six named features in a responsive grid (1 / 2 / 3 columns by breakpoint).
- [ ] Pricing shows Explorer $0, Builder $29/mo with "Most popular", Team $79/mo, each with 5 features and a CTA.
- [ ] FAQ has 6 items, each expands/collapses natively without JavaScript errors, with the chevron rotating.
- [ ] CTA section is the dark navy `#1A3A5C` with the email input and accent "Join Waitlist" button.
- [ ] Submitting a valid email replaces the form with a success message; submitting an invalid email shows an inline error.
- [ ] Footer shows `© 2026 Uncle Inc.` and three links (Privacy, Terms, Contact).
- [ ] **No fake testimonials, no invented user counts, no invented ratings, no invented press mentions, no invented customer logos** anywhere in the codebase.
- [ ] No social-sign-in buttons (Google/GitHub/etc.) are present.
- [ ] No `Clerk` dependency in `package.json`; no `next-auth` dependency; no auth routes.
- [ ] The page is responsive: usable at 360px, 768px, 1280px widths with no horizontal scroll and no overlapping text.

FILES: ["package.json", "next.config.js", "tsconfig.json", "tailwind.config.ts", "postcss.config.js", ".gitignore", "README.md", "app/globals.css", "app/layout.tsx", "app/page.tsx", "app/icon.tsx", "components/Nav.tsx", "components/Hero.tsx", "components/Features.tsx", "components/Pricing.tsx", "components/FAQ.tsx", "components/CTA.tsx", "components/WaitlistForm.tsx", "components/Footer.tsx", "components/Icons.tsx"]