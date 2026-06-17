# Uncle Inc. — Build Plan

## 1. PRODUCT

Uncle Inc. is a single-route marketing landing page for an AI-assisted MVP development platform. The page does one job: convert pre-launch founders who are sitting on an unvalidated idea into waitlist signups. It positions Uncle Inc. as the operator that turns a rough hypothesis into a tested, instrumented MVP without forcing the founder to write code or run a validation sprint by hand. The core value communicated is "validate before you build" — six capability pillars (AI prototyping, user testing, launch analytics, guided validation, no-code, real-data iteration), three transparent pricing tiers, six objection-handling FAQs, and a single email-capture CTA at the bottom. Pain solved: first-time founders waste months building the wrong thing; Uncle Inc. collapses the build→measure→learn loop into a guided, AI-assisted flow so they can confirm demand before sinking serious time and money.

## 2. WHO IT'S FOR

The ICP is a non-technical or lightly technical first-time founder, typically 25–45, working on a side project or early-stage startup, who has an idea but no team, no design/dev capacity, and no validated signal that anyone actually wants what they plan to build. They are time-poor, skeptical of vague AI hype, and want concrete answers: what does it do, what does it cost, do I have to code, how do I know it works. The product and tone are shaped accordingly: zero jargon, feature cards named after concrete outcomes (not buzzwords), prices shown as plain dollars, no invented social proof, no fake logos. Tone is calm, confident, "Crisp Operator" — the page reads like a competent technical cofounder, not a growth-hacker. The hero is one sentence, the CTAs are two specific actions, the FAQ answers real objections a skeptic would type into Google.

## 3. LOOK & FEEL

**Visual system**
- Vibe/positioning: Crisp Operator. Clean enterprise UI, precise grids, confident whitespace. No gradients, no glassmorphism, no neon. Solid colors, hairline borders, tight type.
- Color palette (Tailwind theme):
  - `navy` #1A3A5C — primary, used for dark sections, footer, dark CTA band, heading accents
  - `cobalt` #4A90D9 — interactive accent, links, primary buttons on light backgrounds
  - `accent` #22C55E — single-purpose: "popular" badge, success micro-copy, the underline mark on the wordmark logo, and the "in stock / live" dot on the CTA
  - `bg` #F8FAFC — page background
  - `surface` #FFFFFF — cards
  - `ink` #0F172A — body/heading text
  - `muted` #64748B — secondary text
  - `border` #E2E8F0 — 1px hairlines
- Typography: Inter for h1–h4, IBM Plex Sans for body, paragraphs, buttons, FAQ answers. Source Code Pro only if a code snippet appears (it doesn't on this page). Weights: 400 body, 500 subheads, 600 h2, 700 h1.
- Spacing/layout: 4px base unit, 1280px max container, 24px section vertical padding (96px on desktop), 4px border-radius (deliberately tight — enterprise feel, not consumer playful).
- Components used: sticky top nav, two button variants (`primary` cobalt filled, `secondary` navy outline on light / white outline on dark), input with label, feature card, pricing card (with optional "popular" badge), accordion FAQ row, dark CTA band, footer.
- Iconography: inline SVG, 24px, 1.5px stroke, currentColor. One icon per feature card, monochromatic cobalt. No icon font.
- Imagery: none on this page. The product is a platform; an honest pre-launch landing page uses type, color, and structure to carry the message. No stock photos, no mockup screenshots of a product that does not exist yet.
- Motion: minimal. 150ms ease-out on hover for buttons and links. FAQ rows animate height on open/close (200ms ease-in-out, 180px max). No scroll animations, no parallax.

**Per-screen layout (this is a single page, sections top-to-bottom)**

1. **Nav (sticky, 64px)**
   - Left: wordmark "Uncle" in Inter 700 navy + a small green (#22C55E) underline glyph after the word; ".inc" implied by context.
   - Center (md+): three text links — Features, Pricing, FAQ — Inter 500, 14px, muted, hover→ink.
   - Right: "Join Waitlist" button, secondary variant (navy outline on light bg), 36px tall.

2. **Hero (96px top padding, 96px bottom)**
   - Eyebrow chip: small pill, navy/10 bg, navy text, 12px, "AI-assisted MVP platform".
   - H1: "Validate Your Startup Idea Before You Build It" — Inter 700, 48px mobile / 64px desktop, ink, max-width 820px, centered.
   - Subtext: one paragraph, IBM Plex Sans 400, 18px, muted, max-width 640px, centered. Wording: "Uncle Inc. turns your idea into a working, testable MVP in days — with built-in user research, launch analytics, and AI-guided iteration. No code, no guesswork, no six-month build."
   - Two CTAs, side-by-side, centered, 48px tall:
     - Primary cobalt: "Start a Free Project"
     - Secondary navy outline: "See How It Works"
   - Below CTAs, 14px muted line: "Free to start · No credit card required". The small green dot (#22C55E) sits to the left of this line as a live/available signal.

3. **Features (96px vertical padding)**
   - Section header: H2 "Everything you need to go from idea to validated MVP" + muted subhead "Six tools, one workspace, zero engineering required."
   - Grid: 3 columns desktop, 2 tablet, 1 mobile, 24px gap.
   - 6 cards, each: white surface, 1px border, 16px padding, 4px radius.
     - Top: 24px cobalt SVG icon, 40px from top of card.
     - Title: Inter 600, 18px, ink.
     - Body: IBM Plex Sans 400, 15px, muted, 2–3 lines.
   - Card order and exact titles/copy:
     1. **AI Rapid Prototyping** — "Describe your idea in plain English. Get a clickable, branded prototype in minutes, not weeks."
     2. **Built-in User Testing** — "Recruit real testers from your audience, run guided tasks, and capture session recordings automatically."
     3. **Launch Analytics** — "A live dashboard for signups, activation, and retention from the moment your MVP is live."
     4. **Guided Validation** — "Step-by-step playbooks built on the Lean Startup method, adapted to your idea as you progress."
     5. **No Code Required** — "Build, ship, and iterate visually. Every change you make is reviewed by AI for clarity and conversion."
     6. **Iterate with Real Data** — "See what's working, what's not, and what to build next — backed by real user behavior, not opinions."

4. **Pricing (96px vertical padding, light bg section — white surface)**
   - H2: "Simple, founder-friendly pricing" + muted subhead "Start free. Upgrade only when you're ready to launch."
   - 3 cards in a row (stacks on mobile), 24px gap. Middle card is "popular" — adds the green badge ribbon top-center, a 2px cobalt border, and a subtle shadow (0 1px 2px rgba(15,23,42,0.06)).
   - Card structure (every card):
     - Tier name (Inter 600, 20px)
     - One-line description (muted, 14px)
     - Price block: "$0" or "$29" or "$79" in Inter 700, 48px, ink, with "/mo" in muted 16px
     - CTA button (full-width, 44px): "Get Started" / "Start Building" / "Start Team Trial". Middle card's button is primary cobalt; outer cards are secondary navy outline.
     - 5 feature bullets, IBM Plex Sans 15px, with a small cobalt check SVG.
   - Exact tiers and bullets:
     - **Explorer** — $0 — "For founders validating their first idea."
       - 1 active project
       - AI prototyping (10 generations / mo)
       - Up to 25 tester sessions
       - Basic launch analytics
       - Community support
     - **Builder** — $29/mo — "For solo founders ready to launch and learn." [Popular]
       - Unlimited projects
       - Unlimited AI prototyping
       - Up to 500 tester sessions
       - Full launch analytics dashboard
       - Guided validation playbooks
     - **Team** — $79/mo — "For small teams running multiple experiments."
       - Everything in Builder
       - 5 team seats included
       - Custom branding on prototypes
       - Priority support (24h response)
       - Export raw analytics data

5. **FAQ (96px vertical padding)**
   - H2: "Frequently asked questions" + muted subhead "Still on the fence? Here's what founders ask us most."
   - 6 accordion rows, 1px border-bottom between rows, 0 top border, white background, max-width 820px centered.
   - Row anatomy: question on the left (Inter 500, 17px, ink), plus/minus toggle on the right (cobalt), 20px vertical padding. Expanded: answer slides open in IBM Plex Sans 15px muted, 16px bottom padding.
   - Questions and answers (exact):
     1. **Do I need to know how to code?** — "No. Uncle Inc. is a visual, AI-assisted platform. If you can describe your idea, you can build a working MVP on Uncle."
     2. **How is this different from a no-code website builder?** — "Website builders help you publish pages. Uncle Inc. helps you validate a product idea — with built-in user testing, analytics, and guided playbooks that adapt to what you're building."
     3. **What does "AI-assisted" actually mean here?** — "Our AI drafts your prototype from a short description, reviews every change you make for clarity, and recommends the next validation step based on the data your MVP collects."
     4. **Can I export my project or data?** — "Yes. Team plans include raw data export. All paid plans can export the project itself as a static site or a documented spec you can hand to developers later."
     5. **How long does it take to get a prototype live?** — "Most founders have a clickable prototype within an hour of signing up, and a testable MVP in their first week."
     6. **When will Uncle Inc. be generally available?** — "We're in private beta. Join the waitlist and you'll get an invite as soon as a spot opens — usually within two weeks."

6. **CTA band (full-width, navy #1A3A5C background, 96px vertical padding)**
   - H2 white: "Be first in line when we open access" + muted-cobalt subhead "Join the waitlist for early access, founder pricing, and a direct line to our team."
   - Form, centered, single row on desktop (email input + button), stacked on mobile.
     - Email input: 360px wide desktop, 48px tall, white surface, 4px radius, IBM Plex Sans 15px, placeholder "you@startup.com", 1px border #FFFFFF/20.
     - Button: primary variant but white surface with navy text — "Join Waitlist", 48px tall, 8px left margin on desktop.
   - Below the form, 13px white/70 microcopy: "We'll only email you about access. No spam, ever." A small green dot sits to the left.

7. **Footer (white surface, 1px top border, 48px vertical padding)**
   - Left: "© 2026 Uncle Inc. All rights reserved." in IBM Plex Sans 14px muted.
   - Right: two text links, "Privacy" and "Terms", 14px muted, hover→ink.

## 4. USER FLOWS

**Primary flow: visitor → waitlist signup**
1. Land on `/` (this is the only route).
2. Read hero, click "Start a Free Project" → anchors to `#waitlist` (the CTA band section). No real account creation on this page; the button scrolls, it does not open a modal that pretends to sign them up.
3. Alternative path: read Features → Pricing → FAQ, then click "Join Waitlist" in the nav or scroll to the bottom band.
4. In the email input, type address, click "Join Waitlist".
5. Submit state: button shows "Joining…" (disabled, same dimensions to prevent layout shift), input becomes readonly. On success: input is replaced inline with a success line "✓ You're on the list. We'll be in touch." in white text with a small green dot. On error: input border turns red-ish (use #EF4444), helper text below says "Something went wrong. Try again."
6. No persistence requirement is in the spec (this is a static marketing page), so the form is a client component that calls a `fetch('/api/waitlist', { method: 'POST', body: JSON.stringify({ email }) })` endpoint. If the API route is not implemented, the form should still function as a no-op success in dev (return `{ ok: true }` after a short delay) so the page is honest and complete. The plan does not include a database for this landing page — it is a single-route marketing site.

**Secondary flow: visitor → pricing → waitlist**
1. Visitor reads pricing.
2. Clicks the middle "Builder" card's "Start Building" CTA.
3. Same scroll-to-`#waitlist` behavior as the hero CTA. All "Get Started" / "Start Building" / "Start Team Trial" buttons anchor to `#waitlist`. The free and team CTAs are deliberately the same target — there is no checkout on this page.

**FAQ flow**
- Click any FAQ row → row expands, plus icon rotates to minus, answer fades in. Click again to collapse. Each row independent (multiple can be open).

**States (every interactive element)**
- Buttons: default, hover (slight darken, 150ms), focus-visible (2px cobalt ring, 2px offset), disabled (40% opacity, cursor not-allowed).
- Nav links: default muted, hover ink, focus-visible cobalt underline 2px.
- FAQ rows: default closed, hover background `bg` (#F8FAFC), open white surface with cobalt left-border 2px.
- Email input: default white with 1px border `border`, focus 1px cobalt + 2px cobalt/20 ring, error 1px #EF4444, success hidden (replaced by message).
- Mobile (≤640px): nav collapses to logo + "Join Waitlist" button only; hero text 36px; features grid 1-col; pricing 1-col stacked with "popular" card still visually marked; FAQ full width; CTA form stacked.

## 5. PAGES/ROUTES

| Route | Purpose | Layout | Main UI |
|---|---|---|---|
| `/` | The marketing landing page. The entire product for this build. | Single page, sections stacked: Nav → Hero → Features → Pricing → FAQ → CTA → Footer | All components |
| `/api/waitlist` (POST) | Accepts `{ email: string }`. Validates email format, returns `{ ok: true }` after a short artificial delay. No DB write (out of scope for this build; documented as a future integration). Returns 400 on invalid email. | API route, JSON | — |
| `/privacy` | Stub page. 2 sections of placeholder copy, same nav and footer. Required because the footer links to it. | Reuses Nav + Footer | "Privacy Policy" h1 + 1 paragraph + "Last updated: 2026" |
| `/terms` | Stub page. Same as `/privacy` but with "Terms of Service". | Reuses Nav + Footer | "Terms of Service" h1 + 1 paragraph + "Last updated: 2026" |

No other routes. No dashboard, no auth, no `/app/*` — the goal is a marketing landing page, and the spec is explicit about that scope. The plan acknowledges in the CTA band that full product access is gated by the waitlist.

## 6. CORE FEATURES

1. **Sticky navigation with anchor links and CTA**
   - What it does: stays at the top of the viewport on scroll, provides anchor navigation to Features / Pricing / FAQ sections, and surfaces a "Join Waitlist" CTA.
   - How: `position: sticky; top: 0` on a `<nav>`. `scroll-behavior: smooth` set on `html` in `globals.css` for anchor jumps. Mobile: hides center links, shows logo + CTA only.

2. **Hero with two CTAs and anchor scroll**
   - What it does: communicates the value prop in one headline and routes the user to two distinct next steps.
   - How: h1 + subtext + two buttons. Primary button (`#waitlist`), secondary button (`#how-it-works` — a small in-page "how it works" explainer block inserted between Hero and Features, see below). Both use `<a href="#…">`.

3. **"How it works" explainer (3 steps)**
   - What it does: gives the visitor a 30-second mental model of the product flow so the Features grid has context.
   - How: a single horizontal row of 3 numbered steps with cobalt numerals: 1. Describe your idea, 2. Get a clickable prototype, 3. Test with real users and iterate. Each step has a 1-line IBM Plex Sans 14px muted description. This is the anchor target for the secondary CTA "See How It Works" and is required to make that second CTA honest (a button that scrolls to nothing is a dead UI).

4. **Features grid (6 cards)**
   - What it does: enumerates concrete capabilities, each with a distinct icon and 2–3 line description.
   - How: CSS grid 1/2/3 cols. Each card is a `<div>` with icon + h3 + p. Icons are inline SVG components in a `components/icons.tsx` file.

5. **Pricing (3 tiers, middle marked popular)**
   - What it does: presents transparent monthly pricing with explicit feature bullets.
   - How: 3 flex/grid cards. Middle card adds `border-2 border-cobalt` + the green "Popular" badge absolutely positioned at the top. All CTAs anchor to `#waitlist`.

6. **FAQ accordion (6 items)**
   - What it does: answers the six most common pre-signup questions and reduces support burden.
   - How: 6 `<details>` / `<summary>` elements (native HTML, accessible by default, no JS library required). Styled with Tailwind to match the design system. Only one needs to be open at a time — handled by toggling siblings' `open` attribute on `toggle` event using a small client component (`'use client'`) wrapper.

7. **Waitlist email capture**
   - What it does: collects an email and gives the user clear success/error feedback.
   - How: client component with controlled input + button. On submit, `POST /api/waitlist` with `{ email }`. Button disabled during request. On `ok: true`, swap input area for a success line. On error, show inline error.

8. **Footer with legal links**
   - What it does: provides copyright and routes to stub Privacy and Terms pages.
   - How: flex row, left text + right links.

9. **Stub Privacy and Terms pages**
   - What it does: gives the footer links a real destination with honest placeholder copy.
   - How: minimal pages reusing `<Nav />` and `<Footer />`, one paragraph of neutral placeholder text noting that final policies will be published before general availability.

## 7. DATA MODEL

This is a static marketing page. The only runtime data is the waitlist submission.

**WaitlistSubmission** (logical entity; no persistence in this build)
- `email: string` — required, validated against a basic RFC-5322 regex client- and server-side.
- `submittedAt: ISODate` — set server-side in the API route.
- `source: 'hero' | 'pricing' | 'nav' | 'footer-band'` — derived from a hidden form field or referrer, optional.

The API route validates, returns `{ ok: true }` after a 400ms artificial delay to give realistic loading feedback, and logs to console. There is no database table in this build; the entity is documented so a future iteration can wire the same API route to Supabase or a similar store without changing the contract.

No other entities. No user accounts, no projects, no analytics rows — those are product features behind the waitlist.

## 8. AUTH

No auth on this build. The landing page is pre-launch and intentionally has no login surface. The only protected-feeling action is the waitlist email capture, which is unauthenticated by design and does not require a session.

If a future iteration adds `/app/*` routes requiring auth, the plan should default to **Supabase Auth with email + password and magic-link**, both of which work with no external OAuth configuration. Do not add Google/GitHub/social buttons in this build — there is no auth at all, and adding buttons that link to nowhere would be dishonest.

## 9. FILES

```
package.json                              # Next.js 14, react, tailwindcss, typescript, autoprefixer, postcss
next.config.js                            # Minimal Next.js config (reactStrictness on if desired)
tsconfig.json                             # Standard Next.js TS config with @/* path alias
tailwind.config.ts                        # Theme tokens: navy/cobalt/accent/ink/muted/border/bg/surface, fonts, 4px spacing
postcss.config.js                         # tailwindcss + autoprefixer
app/globals.css                           # Tailwind directives, html { scroll-behavior: smooth }, body bg
app/layout.tsx                            # Root layout, Inter + IBM Plex Sans via next/font, metadata (title, description, OG)
app/page.tsx                              # Imports and renders Nav, Hero, HowItWorks, Features, Pricing, FAQ, CTA, Footer
app/privacy/page.tsx                      # Stub privacy policy page, uses Nav + Footer
app/terms/page.tsx                        # Stub terms of service page, uses Nav + Footer
app/api/waitlist/route.ts                 # POST handler: validates email, returns { ok: true } after 400ms
components/Nav.tsx                        # Sticky nav with wordmark, anchor links, Join Waitlist button
components/Hero.tsx                       # H1, subtext, two CTAs, free-to-start microcopy
components/HowItWorks.tsx                 # 3-step explainer, anchor target for Hero's secondary CTA
components/Features.tsx                   # Section header + 6-card responsive grid
components/FeatureCard.tsx                # Single feature card (icon + title + body)
components/icons.tsx                      # 6 inline SVG icon components (24px, 1.5px stroke, currentColor)
components/Pricing.tsx                    # Section header + 3 tier cards, middle "popular"
components/PricingCard.tsx                # Single pricing card with optional popular badge
components/FAQ.tsx                        # Section header + 6 accordion rows
components/FAQItem.tsx                    # Single FAQ accordion row (uses <details>/<summary>)
components/CTA.tsx                        # Navy band with email form, client component, calls /api/waitlist
components/Footer.tsx                     # Copyright + Privacy/Terms links
components/Logo.tsx                       # Wordmark "Uncle" in Inter 700 navy with green underline glyph
components/Section.tsx                    # Shared wrapper enforcing 1280px container, 96px vertical padding
public/favicon.ico                        # Placeholder favicon (can be empty 1x1, or the icon logo)
```

## 10. ACCEPTANCE

- [ ] `npm install` then `npm run dev` starts the app on `http://localhost:3000` with no errors and no TypeScript errors.
- [ ] `npm run build` completes successfully.
- [ ] Visiting `/` renders the full page: Nav, Hero, HowItWorks (3 steps), Features (6 cards in 3-col grid on desktop), Pricing (3 tiers, middle visually marked popular), FAQ (6 items), CTA band, Footer — in that order.
- [ ] Color tokens match: navy #1A3A5C, cobalt #4A90D9, accent #22C55E are present in `tailwind.config.ts` and used in the rendered output (verifiable via DevTools).
- [ ] Fonts: Inter is applied to h1–h4; IBM Plex Sans is applied to body, paragraphs, buttons, and FAQ answers.
- [ ] Nav is sticky on scroll; clicking "Features", "Pricing", "FAQ" smooth-scrolls to the correct section.
- [ ] Hero primary CTA scrolls to the waitlist band; secondary CTA scrolls to the "How it works" section.
- [ ] All three pricing card CTAs scroll to the waitlist band.
- [ ] FAQ rows expand and collapse on click; only one row is open at a time; keyboard accessible (Tab focuses, Enter/Space toggles).
- [ ] Waitlist form: submitting a valid email shows a success message; submitting an invalid email shows an inline error; button is disabled during the request.
- [ ] `/api/waitlist` returns `{ ok: true }` for valid emails and HTTP 400 for invalid.
- [ ] `/privacy` and `/terms` render with Nav and Footer and a single paragraph of placeholder copy each.
- [ ] No fake testimonials, no invented customer logos, no fabricated user counts or metrics anywhere on the page. The only copy in the page is the product's own value proposition, feature descriptions, prices, and FAQ answers.
- [ ] Responsive: at 640px width, nav collapses to logo + CTA only, feature grid is 1-column, pricing stacks, FAQ is full width, CTA form stacks.
- [ ] Lighthouse a11y score ≥ 95 on `/`: every interactive element has a focus ring, all images/icons have `aria-hidden` where decorative, form has a visible label, color contrast meets WCAG AA.

FILES: ["package.json","next.config.js","tsconfig.json","tailwind.config.ts","postcss.config.js","app/globals.css","app/layout.tsx","app/page.tsx","app/privacy/page.tsx","app/terms/page.tsx","app/api/waitlist/route.ts","components/Nav.tsx","components/Hero.tsx","components/HowItWorks.tsx","components/Features.tsx","components/FeatureCard.tsx","components/icons.tsx","components/Pricing.tsx","components/PricingCard.tsx","components/FAQ.tsx","components/FAQItem.tsx","components/CTA.tsx","components/Footer.tsx","components/Logo.tsx","components/Section.tsx","public/favicon.ico"]# Uncle Inc. — Build Plan

## 1. PRODUCT

Uncle Inc. is a single-route marketing landing page for an AI-assisted MVP development platform. The page does one job: convert pre-launch founders who are sitting on an unvalidated idea into waitlist signups. It positions Uncle Inc. as the operator that turns a rough hypothesis into a tested, instrumented MVP without forcing the founder to write code or run a validation sprint by hand. The core value communicated is "validate before you build" — six capability pillars (AI prototyping, user testing, launch analytics, guided validation, no-code, real-data iteration), three transparent pricing tiers, six objection-handling FAQs, and a single email-capture CTA at the bottom. Pain solved: first-time founders waste months building the wrong thing; Uncle Inc. collapses the build→measure→learn loop into a guided, AI-assisted flow so they can confirm demand before sinking serious time and money.

## 2. WHO IT'S FOR

The ICP is a non-technical or lightly technical first-time founder, typically 25–45, working on a side project or early-stage startup, who has an idea but no team, no design/dev capacity, and no validated signal that anyone actually wants what they plan to build. They are time-poor, skeptical of vague AI hype, and want concrete answers: what does it do, what does it cost, do I have to code, how do I know it works. The product and tone are shaped accordingly: zero jargon, feature cards named after concrete outcomes (not buzzwords), prices shown as plain dollars, no invented social proof, no fake logos. Tone is calm, confident, "Crisp Operator" — the page reads like a competent technical cofounder, not a growth-hacker. The hero is one sentence, the CTAs are two specific actions, the FAQ answers real objections a skeptic would type into Google.

## 3. LOOK & FEEL

**Visual system**
- Vibe/positioning: Crisp Operator. Clean enterprise UI, precise grids, confident whitespace. No gradients, no glassmorphism, no neon. Solid colors, hairline borders, tight type.
- Color palette (Tailwind theme):
  - `navy` #1A3A5C — primary, used for dark sections, footer, dark CTA band, heading accents
  - `cobalt` #4A90D9 — interactive accent, links, primary buttons on light backgrounds
  - `accent` #22C55E — single-purpose: "popular" badge, success micro-copy, the underline mark on the wordmark logo, and the "in stock / live" dot on the CTA
  - `bg` #F8FAFC — page background
  - `surface` #FFFFFF — cards
  - `ink` #0F172A — body/heading text
  - `muted` #64748B — secondary text
  - `border` #E2E8F0 — 1px hairlines
- Typography: Inter for h1–h4, IBM Plex Sans for body, paragraphs, buttons, FAQ answers. Source Code Pro only if a code snippet appears (it doesn't on this page). Weights: 400 body, 500 subheads, 600 h2, 700 h1.
- Spacing/layout: 4px base unit, 1280px max container, 24px section vertical padding (96px on desktop), 4px border-radius (deliberately tight — enterprise feel, not consumer playful).
- Components used: sticky top nav, two button variants (`primary` cobalt filled, `secondary` navy outline on light / white outline on dark), input with label, feature card, pricing card (with optional "popular" badge), accordion FAQ row, dark CTA band, footer.
- Iconography: inline SVG, 24px, 1.5px stroke, currentColor. One icon per feature card, monochromatic cobalt. No icon font.
- Imagery: none on this page. The product is a platform; an honest pre-launch landing page uses type, color, and structure to carry the message. No stock photos, no mockup screenshots of a product that does not exist yet.
- Motion: minimal. 150ms ease-out on hover for buttons and links. FAQ rows animate height on open/close (200ms ease-in-out, 180px max). No scroll animations, no parallax.

**Per-screen layout (this is a single page, sections top-to-bottom)**

1. **Nav (sticky, 64px)**
   - Left: wordmark "Uncle" in Inter 700 navy + a small green (#22C55E) underline glyph after the word; ".inc" implied by context.
   - Center (md+): three text links — Features, Pricing, FAQ — Inter 500, 14px, muted, hover→ink.
   - Right: "Join Waitlist" button, secondary variant (navy outline on light bg), 36px tall.

2. **Hero (96px top padding, 96px bottom)**
   - Eyebrow chip: small pill, navy/10 bg, navy text, 12px, "AI-assisted MVP platform".
   - H1: "Validate Your Startup Idea Before You Build It" — Inter 700, 48px mobile / 64px desktop, ink, max-width 820px, centered.
   - Subtext: one paragraph, IBM Plex Sans 400, 18px, muted, max-width 640px, centered. Wording: "Uncle Inc. turns your idea into a working, testable MVP in days — with built-in user research, launch analytics, and AI-guided iteration. No code, no guesswork, no six-month build."
   - Two CTAs, side-by-side, centered, 48px tall:
     - Primary cobalt: "Start a Free Project"
     - Secondary navy outline: "See How It Works"
   - Below CTAs, 14px muted line: "Free to start · No credit card required". The small green dot (#22C55E) sits to the left of this line as a live/available signal.

3. **Features (96px vertical padding)**
   - Section header: H2 "Everything you need to go from idea to validated MVP" + muted subhead "Six tools, one workspace, zero engineering required."
   - Grid: 3 columns desktop, 2 tablet, 1 mobile, 24px gap.
   - 6 cards, each: white surface, 1px border, 16px padding, 4px radius.
     - Top: 24px cobalt SVG icon, 40px from top of card.
     - Title: Inter 600, 18px, ink.
     - Body: IBM Plex Sans 400, 15px, muted, 2–3 lines.
   - Card order and exact titles/copy:
     1. **AI Rapid Prototyping** — "Describe your idea in plain English. Get a clickable, branded prototype in minutes, not weeks."
     2. **Built-in User Testing** — "Recruit real testers from your audience, run guided tasks, and capture session recordings automatically."
     3. **Launch Analytics** — "A live dashboard for signups, activation, and retention from the moment your MVP is live."
     4. **Guided Validation** — "Step-by-step playbooks built on the Lean Startup method, adapted to your idea as you progress."
     5. **No Code Required** — "Build, ship, and iterate visually. Every change you make is reviewed by AI for clarity and conversion."
     6. **Iterate with Real Data** — "See what's working, what's not, and what to build next — backed by real user behavior, not opinions."

4. **Pricing (96px vertical padding, light bg section — white surface)**
   - H2: "Simple, founder-friendly pricing" + muted subhead "Start free. Upgrade only when you're ready to launch."
   - 3 cards in a row (stacks on mobile), 24px gap. Middle card is "popular" — adds the green badge ribbon top-center, a 2px cobalt border, and a subtle shadow (0 1px 2px rgba(15,23,42,0.06)).
   - Card structure (every card):
     - Tier name (Inter 600, 20px)
     - One-line description (muted, 14px)
     - Price block: "$0" or "$29" or "$79" in Inter 700, 48px, ink, with "/mo" in muted 16px
     - CTA button (full-width, 44px): "Get Started" / "Start Building" / "Start Team Trial". Middle card's button is primary cobalt; outer cards are secondary navy outline.
     - 5 feature bullets, IBM Plex Sans 15px, with a small cobalt check SVG.
   - Exact tiers and bullets:
     - **Explorer** — $0 — "For founders validating their first idea."
       - 1 active project
       - AI prototyping (10 generations / mo)
       - Up to 25 tester sessions
       - Basic launch analytics
       - Community support
     - **Builder** — $29/mo — "For solo founders ready to launch and learn." [Popular]
       - Unlimited projects
       - Unlimited AI prototyping
       - Up to 500 tester sessions
       - Full launch analytics dashboard
       - Guided validation playbooks
     - **Team** — $79/mo — "For small teams running multiple experiments."
       - Everything in Builder
       - 5 team seats included
       - Custom branding on prototypes
       - Priority support (24h response)
       - Export raw analytics data

5. **FAQ (96px vertical padding)**
   - H2: "Frequently asked questions" + muted subhead "Still on the fence? Here's what founders ask us most."
   - 6 accordion rows, 1px border-bottom between rows, 0 top border, white background, max-width 820px centered.
   - Row anatomy: question on the left (Inter 500, 17px, ink), plus/minus toggle on the right (cobalt), 20px vertical padding. Expanded: answer slides open in IBM Plex Sans 15px muted, 16px bottom padding.
   - Questions and answers (exact):
     1. **Do I need to know how to code?** — "No. Uncle Inc. is a visual, AI-assisted platform. If you can describe your idea, you can build a working MVP on Uncle."
     2. **How is this different from a no-code website builder?** — "Website builders help you publish pages. Uncle Inc. helps you validate a product idea — with built-in user testing, analytics, and guided playbooks that adapt to what you're building."
     3. **What does "AI-assisted" actually mean here?** — "Our AI drafts your prototype from a short description, reviews every change you make for clarity, and recommends the next validation step based on the data your MVP collects."
     4. **Can I export my project or data?** — "Yes. Team plans include raw data export. All paid plans can export the project itself as a static site or a documented spec you can hand to developers later."
     5. **How long does it take to get a prototype live?** — "Most founders have a clickable prototype within an hour of signing up, and a testable MVP in their first week."
     6. **When will Uncle Inc. be generally available?** — "We're in private beta. Join the waitlist and you'll get an invite as soon as a spot opens — usually within two weeks."

6. **CTA band (full-width, navy #1A3A5C background, 96px vertical padding)**
   - H2 white: "Be first in line when we open access" + muted-cobalt subhead "Join the waitlist for early access, founder pricing, and a direct line to our team."
   - Form, centered, single row on desktop (email input + button), stacked on mobile.
     - Email input: 360px wide desktop, 48px tall, white surface, 4px radius, IBM Plex Sans 15px, placeholder "you@startup.com", 1px border #FFFFFF/20.
     - Button: primary variant but white surface with navy text — "Join Waitlist", 48px tall, 8px left margin on desktop.
   - Below the form, 13px white/70 microcopy: "We'll only email you about access. No spam, ever." A small green dot sits to the left.

7. **Footer (white surface, 1px top border, 48px vertical padding)**
   - Left: "© 2026 Uncle Inc. All rights reserved." in IBM Plex Sans 14px muted.
   - Right: two text links, "Privacy" and "Terms", 14px muted, hover→ink.

## 4. USER FLOWS

**Primary flow: visitor → waitlist signup**
1. Land on `/` (this is the only route).
2. Read hero, click "Start a Free Project" → anchors to `#waitlist` (the CTA band section). No real account creation on this page; the button scrolls, it does not open a modal that pretends to sign them up.
3. Alternative path: read Features → Pricing → FAQ, then click "Join Waitlist" in the nav or scroll to the bottom band.
4. In the email input, type address, click "Join Waitlist".
5. Submit state: button shows "Joining…" (disabled, same dimensions to prevent layout shift), input becomes readonly. On success: input is replaced inline with a success line "✓ You're on the list. We'll be in touch." in white text with a small green dot. On error: input border turns red-ish (use #EF4444), helper text below says "Something went wrong. Try again."
6. No persistence requirement is in the spec (this is a static marketing page), so the form is a client component that calls a `fetch('/api/waitlist', { method: 'POST', body: JSON.stringify({ email }) })` endpoint. If the API route is not implemented, the form should still function as a no-op success in dev (return `{ ok: true }` after a short delay) so the page is honest and complete. The plan does not include a database for this landing page — it is a single-route marketing site.

**Secondary flow: visitor → pricing → waitlist**
1. Visitor reads pricing.
2. Clicks the middle "Builder" card's "Start Building" CTA.
3. Same scroll-to-`#waitlist` behavior as the hero CTA. All "Get Started" / "Start Building" / "Start Team Trial" buttons anchor to `#waitlist`. The free and team CTAs are deliberately the same target — there is no checkout on this page.

**FAQ flow**
- Click any FAQ row → row expands, plus icon rotates to minus, answer fades in. Click again to collapse. Each row independent (multiple can be open).

**States (every interactive element)**
- Buttons: default, hover (slight darken, 150ms), focus-visible (2px cobalt ring, 2px offset), disabled (40% opacity, cursor not-allowed).
- Nav links: default muted, hover ink, focus-visible cobalt underline 2px.
- FAQ rows: default closed, hover background `bg` (#F8FAFC), open white surface with cobalt left-border 2px.
- Email input: default white with 1px border `border`, focus 1px cobalt + 2px cobalt/20 ring, error 1px #EF4444, success hidden (replaced by message).
- Mobile (≤640px): nav collapses to logo + "Join Waitlist" button only; hero text 36px; features grid 1-col; pricing 1-col stacked with "popular" card still visually marked; FAQ full width; CTA form stacked.

## 5. PAGES/ROUTES

| Route | Purpose | Layout | Main UI |
|---|---|---|---|
| `/` | The marketing landing page. The entire product for this build. | Single page, sections stacked: Nav → Hero → Features → Pricing → FAQ → CTA → Footer | All components |
| `/api/waitlist` (POST) | Accepts `{ email: string }`. Validates email format, returns `{ ok: true }` after a short artificial delay. No DB write (out of scope for this build; documented as a future integration). Returns 400 on invalid email. | API route, JSON | — |
| `/privacy` | Stub page. 2 sections of placeholder copy, same nav and footer. Required because the footer links to it. | Reuses Nav + Footer | "Privacy Policy" h1 + 1 paragraph + "Last updated: 2026" |
| `/terms` | Stub page. Same as `/privacy` but with "Terms of Service". | Reuses Nav + Footer | "Terms of Service" h1 + 1 paragraph + "Last updated: 2026" |

No other routes. No dashboard, no auth, no `/app/*` — the goal is a marketing landing page, and the spec is explicit about that scope. The plan acknowledges in the CTA band that full product access is gated by the waitlist.

## 6. CORE FEATURES

1. **Sticky navigation with anchor links and CTA**
   - What it does: stays at the top of the viewport on scroll, provides anchor navigation to Features / Pricing / FAQ sections, and surfaces a "Join Waitlist" CTA.
   - How: `position: sticky; top: 0` on a `<nav>`. `scroll-behavior: smooth` set on `html` in `globals.css` for anchor jumps. Mobile: hides center links, shows logo + CTA only.

2. **Hero with two CTAs and anchor scroll**
   - What it does: communicates the value prop in one headline and routes the user to two distinct next steps.
   - How: h1 + subtext + two buttons. Primary button (`#waitlist`), secondary button (`#how-it-works` — a small in-page "how it works" explainer block inserted between Hero and Features, see below). Both use `<a href="#…">`.

3. **"How it works" explainer (3 steps)**
   - What it does: gives the visitor a 30-second mental model of the product flow so the Features grid has context.
   - How: a single horizontal row of 3 numbered steps with cobalt numerals: 1. Describe your idea, 2. Get a clickable prototype, 3. Test with real users and iterate. Each step has a 1-line IBM Plex Sans 14px muted description. This is the anchor target for the secondary CTA "See How It Works" and is required to make that second CTA honest (a button that scrolls to nothing is a dead UI).

4. **Features grid (6 cards)**
   - What it does: enumerates concrete capabilities, each with a distinct icon and 2–3 line description.
   - How: CSS grid 1/2/3 cols. Each card is a `<div>` with icon + h3 + p. Icons are inline SVG components in a `components/icons.tsx` file.

5. **Pricing (3 tiers, middle marked popular)**
   - What it does: presents transparent monthly pricing with explicit feature bullets.
   - How: 3 flex/grid cards. Middle card adds `border-2 border-cobalt` + the green "Popular" badge absolutely positioned at the top. All CTAs anchor to `#waitlist`.

6. **FAQ accordion (6 items)**
   - What it does: answers the six most common pre-signup questions and reduces support burden.
   - How: 6 `<details>` / `<summary>` elements (native HTML, accessible by default, no JS library required). Styled with Tailwind to match the design system. Only one needs to be open at a time — handled by toggling siblings' `open` attribute on `toggle` event using a small client component (`'use client'`) wrapper.

7. **Waitlist email capture**
   - What it does: collects an email and gives the user clear success/error feedback.
   - How: client component with controlled input + button. On submit, `POST /api/waitlist` with `{ email }`. Button disabled during request. On `ok: true`, swap input area for a success line. On error, show inline error.

8. **Footer with legal links**
   - What it does: provides copyright and routes to stub Privacy and Terms pages.
   - How: flex row, left text + right links.

9. **Stub Privacy and Terms pages**
   - What it does: gives the footer links a real destination with honest placeholder copy.
   - How: minimal pages reusing `<Nav />` and `<Footer />`, one paragraph of neutral placeholder text noting that final policies will be published before general availability.

## 7. DATA MODEL

This is a static marketing page. The only runtime data is the waitlist submission.

**WaitlistSubmission** (logical entity; no persistence in this build)
- `email: string` — required, validated against a basic RFC-5322 regex client- and server-side.
- `submittedAt: ISODate` — set server-side in the API route.
- `source: 'hero' | 'pricing' | 'nav' | 'footer-band'` — derived from a hidden form field or referrer, optional.

The API route validates, returns `{ ok: true }` after a 400ms artificial delay to give realistic loading feedback, and logs to console. There is no database table in this build; the entity is documented so a future iteration can wire the same API route to Supabase or a similar store without changing the contract.

No other entities. No user accounts, no projects, no analytics rows — those are product features behind the waitlist.

## 8. AUTH

No auth on this build. The landing page is pre-launch and intentionally has no login surface. The only protected-feeling action is the waitlist email capture, which is unauthenticated by design and does not require a session.

If a future iteration adds `/app/*` routes requiring auth, the plan should default to **Supabase Auth with email + password and magic-link**, both of which work with no external OAuth configuration. Do not add Google/GitHub/social buttons in this build — there is no auth at all, and adding buttons that link to nowhere would be dishonest.

## 9. FILES

```
package.json                              # Next.js 14, react, tailwindcss, typescript, autoprefixer, postcss
next.config.js                            # Minimal Next.js config (reactStrictness on if desired)
tsconfig.json                             # Standard Next.js TS config with @/* path alias
tailwind.config.ts                        # Theme tokens: navy/cobalt/accent/ink/muted/border/bg/surface, fonts, 4px spacing
postcss.config.js                         # tailwindcss + autoprefixer
app/globals.css                           # Tailwind directives, html { scroll-behavior: smooth }, body bg
app/layout.tsx                            # Root layout, Inter + IBM Plex Sans via next/font, metadata (title, description, OG)
app/page.tsx                              # Imports and renders Nav, Hero, HowItWorks, Features, Pricing, FAQ, CTA, Footer
app/privacy/page.tsx                      # Stub privacy policy page, uses Nav + Footer
app/terms/page.tsx                        # Stub terms of service page, uses Nav + Footer
app/api/waitlist/route.ts                 # POST handler: validates email, returns { ok: true } after 400ms
components/Nav.tsx                        # Sticky nav with wordmark, anchor links, Join Waitlist button
components/Hero.tsx                       # H1, subtext, two CTAs, free-to-start microcopy
components/HowItWorks.tsx                 # 3-step explainer, anchor target for Hero's secondary CTA
components/Features.tsx                   # Section header + 6-card responsive grid
components/FeatureCard.tsx                # Single feature card (icon + title + body)
components/icons.tsx                      # 6 inline SVG icon components (24px, 1.5px stroke, currentColor)
components/Pricing.tsx                    # Section header + 3 tier cards, middle "popular"
components/PricingCard.tsx                # Single pricing card with optional popular badge
components/FAQ.tsx                        # Section header + 6 accordion rows
components/FAQItem.tsx                    # Single FAQ accordion row (uses <details>/<summary>)
components/CTA.tsx                        # Navy band with email form, client component, calls /api/waitlist
components/Footer.tsx                     # Copyright + Privacy/Terms links
components/Logo.tsx                       # Wordmark "Uncle" in Inter 700 navy with green underline glyph
components/Section.tsx                    # Shared wrapper enforcing 1280px container, 96px vertical padding
public/favicon.ico                        # Placeholder favicon (can be empty 1x1, or the icon logo)
```

## 10. ACCEPTANCE

- [ ] `npm install` then `npm run dev` starts the app on `http://localhost:3000` with no errors and no TypeScript errors.
- [ ] `npm run build` completes successfully.
- [ ] Visiting `/` renders the full page: Nav, Hero, HowItWorks (3 steps), Features (6 cards in 3-col grid on desktop), Pricing (3 tiers, middle visually marked popular), FAQ (6 items), CTA band, Footer — in that order.
- [ ] Color tokens match: navy #1A3A5C, cobalt #4A90D9, accent #22C55E are present in `tailwind.config.ts` and used in the rendered output (verifiable via DevTools).
- [ ] Fonts: Inter is applied to h1–h4; IBM Plex Sans is applied to body, paragraphs, buttons, and FAQ answers.
- [ ] Nav is sticky on scroll; clicking "Features", "Pricing", "FAQ" smooth-scrolls to the correct section.
- [ ] Hero primary CTA scrolls to the waitlist band; secondary CTA scrolls to the "How it works" section.
- [ ] All three pricing card CTAs scroll to the waitlist band.
- [ ] FAQ rows expand and collapse on click; only one row is open at a time; keyboard accessible (Tab focuses, Enter/Space toggles).
- [ ] Waitlist form: submitting a valid email shows a success message; submitting an invalid email shows an inline error; button is disabled during the request.
- [ ] `/api/waitlist` returns `{ ok: true }` for valid emails and HTTP 400 for invalid.
- [ ] `/privacy` and `/terms` render with Nav and Footer and a single paragraph of placeholder copy each.
- [ ] No fake testimonials, no invented customer logos, no fabricated user counts or metrics anywhere on the page. The only copy in the page is the product's own value proposition, feature descriptions, prices, and FAQ answers.
- [ ] Responsive: at 640px width, nav collapses to logo + CTA only, feature grid is 1-column, pricing stacks, FAQ is full width, CTA form stacks.
- [ ] Lighthouse a11y score ≥ 95 on `/`: every interactive element has a focus ring, all images/icons have `aria-hidden` where decorative, form has a visible label, color contrast meets WCAG AA.

FILES: ["package.json","next.config.js","tsconfig.json","tailwind.config.ts","postcss.config.js","app/globals.css","app/layout.tsx","app/page.tsx","app/privacy/page.tsx","app/terms/page.tsx","app/api/waitlist/route.ts","components/Nav.tsx","components/Hero.tsx","components/HowItWorks.tsx","components/Features.tsx","components/FeatureCard.tsx","components/icons.tsx","components/Pricing.tsx","components/PricingCard.tsx","components/FAQ.tsx","components/FAQItem.tsx","components/CTA.tsx","components/Footer.tsx","components/Logo.tsx","components/Section.tsx","public/favicon.ico"]