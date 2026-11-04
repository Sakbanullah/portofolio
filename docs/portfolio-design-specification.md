# Portfolio Design Specification — "The Long Horizon"

**Owner:** Sakbanullah Dwi Oktavian
**Version:** 1.0 (draft for approval)
**Date:** 2026-11-04
**Status:** DESIGN SPEC ONLY — no Figma frames, no code, no assets generated yet.
**Supersedes conceptually:** the ink-scroll "Scroll-Style Report" theme documented in `AGENT.md` and implemented in `front/` as of 2026-10-29.

Legend used throughout:

- `PROPOSED` — a decision made in this document that still needs owner approval.
- `NEEDS USER INPUT` — information that cannot be invented and must come from the owner.
- `VERIFIED` — fact supplied by the owner or already present in the repository.

---

## 1. Project Overview

### 1.1 What this is

A complete visual and interaction redesign of a personal developer portfolio, built as **one continuous cinematic journey through a landscape**. The site is not a template with sections stacked on it; the environment *is* the navigation. Six chapters, six moods, one horizon.

| Item | Value |
|---|---|
| Subject | Sakbanullah Dwi Oktavian `VERIFIED` |
| Positioning | Junior Full-Stack Developer, Backend Focus `VERIFIED` |
| Audience | International software engineering recruiters and hiring managers |
| Language | English (site content) `PROPOSED` |
| Type | Single-page scroll, no router |
| Primary goal | Convert a recruiter's 90 seconds into a project review and a contact |
| Secondary goal | Demonstrate engineering craft through the site itself |

### 1.2 Success criteria

1. A recruiter understands who this is, what they build, and how to reach them **without scrolling more than one viewport past the hero**.
2. The first viewport is unmistakably designed — not a template. It should be describable to a colleague in one sentence.
3. All four projects are readable and credible; no metric appears that the owner cannot defend in an interview.
4. Lighthouse (mobile, throttled): Performance ≥ 85, Accessibility = 100, no CLS, LCP < 2.5s.
5. Fully usable at 360px width and with `prefers-reduced-motion: reduce`.
6. Zero console errors, zero horizontal scroll from 320px to 2560px.

### 1.3 Constraints

- **No copyrighted Alto's Adventure / Odyssey assets, characters, sprites, or exact compositions.** Only *atmosphere* — colour temperature, layer depth, restraint, horizon. Any referenced frame must be an original composition.
- `VERIFIED` — the current `front/` codebase is React 19 + Vite + Tailwind 4 + framer-motion + Lenis + GSAP. No router, no TypeScript, no form library. `AGENT.md` forbids adding router/TypeScript/test framework without approval.
- Content currently in `front/src/data/*.json` is **placeholder and factually wrong** (name "Ren Aizawa", employers "Saku Finance", "Kite Studio", "Hana Labs", four backend projects that are not the owner's). All of it must be replaced. This spec defines the replacement content.
- Backend (`back/`) does not exist. Contact form must therefore be a `mailto:` link, not a form. `VERIFIED`

### 1.4 Out of scope for this phase

Figma construction, illustration production, copy finalisation, implementation, deployment, deleting or archiving existing design files.

---

## 2. Design Vision and Creative Direction

### 2.1 The one-sentence vision

> **A quiet journey across a changing landscape, where the horizon line is the page and each chapter is a different hour of the same day.**

### 2.2 What we take from Alto's Adventure / Odyssey — and what we do not

| Taken (atmosphere) | Rejected (surface) |
|---|---|
| Layered depth: foreground silhouette, middle ridges, distant haze | Character silhouettes, scarf trails, coins, chasms |
| Flat-but-rich colour: large areas of one hue, one accent | Mobile-game UI: score, buttons, HUD |
| The horizon as a compositional anchor | Exact mountain profiles from the game |
| Time-of-day as emotional pacing | A literal day/night cycle animation loop |
| Restraint: one motion idea per moment | Continuous particle systems, weather VFX |
| Silence: long empty passages between events | Constant scrolling stimulation |

### 2.3 The core mechanic: **scroll is time**

The page has **one continuous colour script**. Scroll position drives a global hue/temperature interpolation across the whole document. Chapters are not panels with their own backgrounds — they are *moments on the same horizon*.

- Chapter 01 — dawn, cold, high altitude
- Chapter 02 — morning light breaking over forest
- Chapter 03 — high warm noon / desert
- Chapter 04 — blue hour
- Chapter 05 — night
- Chapter 06 — sunrise returning, distant horizon

`PROPOSED` — **No manual light/dark theme toggle.** The landscape is the theme. A user-controlled toggle would break the single-journey metaphor and double the QA surface. Owner must confirm.

### 2.4 Editorial spine

The layout is a **magazine feature**, not a web app. Conventions used deliberately:

- A narrow measure (~62 characters) for all body copy, regardless of viewport.
- An asymmetric content column that sits left-of-centre on desktop, leaving the landscape open to the right.
- Chapter numerals set enormous and low-contrast, behind content — the "plate number" of a magazine section.
- Captions and labels in small caps/tracking, never inside rounded pills.
- Generous vertical silence between content blocks: the landscape gets air.

### 2.5 Emotional arc

| Chapter | Feeling | What the visitor should think |
|---|---|---|
| 01 Arrival | Awe, calm, orientation | "This is a real person with taste." |
| 02 Journey | Grounded, human | "This person's path makes sense." |
| 03 Expeditions | Focus, craft | "These are substantial, and they can explain them." |
| 04 Toolkit | Confidence, breadth | "They have depth, not a checklist." |
| 05 Quiet Moment | Reflection, respect | "They think about software seriously." |
| 06 Next Horizon | Warmth, invitation | "I should email them." |

---

## 3. Design Principles and Anti-Patterns

### 3.1 Principles

1. **The landscape never competes with the words.** Every layer under text must sit below a measured contrast floor (see §14). Content lives in the "calm band" of the composition.
2. **One accent per environment.** Each chapter has a single highlight hue. No rainbow UI.
3. **Depth by value, not by blur.** Layers separate through lightness and saturation, not backdrop-filter. Glass is banned.
4. **Motion is weather, not animation.** Things move because the world is moving, in one direction, at one speed family. No bounce, no elastic, no spring overshoot.
5. **Silence is a design element.** At least 40% of vertical space carries no text at all.
6. **Every element earns its pixels.** No decorative borders, no empty containers, no icon repeating the label beside it.
7. **Typography carries hierarchy.** Weight, size, and space — not coloured boxes, not cards.
8. **The site must work with JavaScript half-broken.** Content readable if scroll animation fails (progressive enhancement, already a project rule in `AGENT.md`).
9. **Mobile is a different composition, not a smaller one.** The landscape becomes portrait; type reflows; navigation becomes a chapter sheet.
10. **Facts only.** No invented metrics, employers, user counts, accuracy figures, or URLs.

### 3.2 Anti-patterns — explicit bans

| Banned | Why |
|---|---|
| Cards nested inside cards | Already burned this project once (`AGENT.md`, box-in-box incident 2026-10-29) |
| Rounded containers > 4px on large surfaces | Reads as SaaS template |
| Glassmorphism / frosted panels | Breaks the painted-landscape metaphor; kills mobile perf |
| Decorative gradients (buttons, chips) | Only *atmospheric* sky gradients allowed |
| Skill bars, percentages, star ratings | Unverifiable claims |
| Bento grids | Dashboard aesthetic; explicitly rejected |
| Emoji as iconography | Tone mismatch |
| Auto-playing carousels, typewriter text, cursor trails | Noise |
| Scroll-jacking / forced chapter snapping | Accessibility and power-user hostility |
| Parallax on text | Nausea, misreads |
| More than 2 typefaces + 1 mono | Visual noise |
| Generic AI-generated illustration style (vector blobs, 3D abstract shapes) | Instant credibility loss |
| Stock UI-kit components dropped in unchanged | Template smell |
| Reveal-on-scroll for every element | Rejected in the previous theme; keep content visible by default |

---

## 4. Portfolio Information Architecture

### 4.1 Single page, six chapters

```
/  (single document)
├── 01  THE ARRIVAL            #arrival      — identity, positioning, CTAs
├── 02  THE JOURNEY            #journey      — background, education, experience, philosophy
├── 03  THE EXPEDITIONS        #expeditions  — four projects
│     ├── Raccoon Coffee       #raccoon
│     ├── Gawe                 #gawe
│     ├── BAPAS OKU Connect    #bapas
│     └── AgroLedger           #agroledger
├── 04  THE TOOLKIT            #toolkit      — capability groups
├── 05  THE QUIET MOMENT       #quiet        — engineering philosophy, current focus
└── 06  THE NEXT HORIZON       #horizon      — contact, links, closing
```

### 4.2 Navigation model

`PROPOSED` — **A persistent minimal chapter rail on the right edge (desktop)**, and a chapter-sheet overlay (mobile).

- Desktop ≥ 1024px: vertical rail, 2px ticks, one per chapter; active chapter's numeral and short name reveal on hover/focus. It doubles as a scroll-progress indicator via a hairline fill.
- The rail is **not** a nav bar. There is no sticky header. The identity is not repeated after Chapter 01.
- Keyboard: `<nav aria-label="Chapters">` with real anchor links, focusable, `aria-current="true"` on the active one.

`PROPOSED` — **No top navigation bar.** The only persistent chrome is the chapter rail plus a small fixed "next chapter" chevron at bottom-right appearing after the first viewport.

### 4.3 Editorial rhythm per chapter

Every chapter follows the same rhythm so the site feels authored, not assembled:

```
[chapter numeral — huge, low contrast]
[kicker — small caps, 1 line, tracking +0.18em]
[chapter title — serif display, 2–4 words]
[lede — 1 sentence, slightly larger, max 2 lines]
[body — 3–6 short paragraphs, measure 62ch]
[content unit — timeline | project rundown | capability field]
[quiet exit — space, then the horizon shifts]
```

### 4.4 Scroll depth budget

| Chapter | Desktop height | Mobile height |
|---|---|---|
| 01 Arrival | 100 + 60vh | ~1.4 screens |
| 02 Journey | ~180vh | ~3.5 screens |
| 03 Expeditions | ~420vh (4 × ~105vh) | ~7 screens |
| 04 Toolkit | ~110vh | ~2 screens |
| 05 Quiet Moment | ~120vh | ~2 screens |
| 06 Horizon | ~100vh | ~1.5 screens |
| **Total** | **~1090vh** | **~17 screens** |

Long, deliberately. The journey must feel like distance. Reduced-motion visitors get the same content with no scroll-linked art.

---

## 5. Six-Chapter Detailed Specification

For each chapter: purpose, content, composition, landscape state, entry/exit behaviour.

### 5.1 Chapter 01 — THE ARRIVAL

**Purpose.** Establish identity, positioning, and atmosphere in one viewport.

**Content (`VERIFIED` except where marked):**

| Field | Value |
|---|---|
| Name | Sakbanullah Dwi Oktavian |
| Positioning line | Junior Full-Stack Developer · Backend Focus |
| Intro (≤ 28 words) | `NEEDS USER INPUT` — draft below for approval |
| Location | Indonesia |
| Education | Informatics Engineering, Bina Darma University, 2021–2025 |
| GPA | 3.72 / 4.00 |
| Primary CTA | Explore Projects → `#expeditions` |
| Secondary CTA | Contact Me → `#horizon` |

**Draft intro copy** `PROPOSED`:
> "I build backend systems that hold up under real use — APIs, data models, authentication. Then I build the interface that makes them usable."

**Composition (desktop, 1440×900):**

```
┌────────────────────────────────────────────────────────────┐
│                                                    ░ hazy  │
│        01                                          ░ ░     │
│                                                    ░ ░░    │  ← distant ridge
│        THE ARRIVAL           (kicker)              ░░░░    │
│                                                    ░░░░░   │  ← mid ridge
│    Sakbanullah Dwi                                 ░░░░░░  │
│    Oktavian                    ← serif display     ░░░░░░░ │
│    (two lines, left aligned)                       ░░░░░░░░│  ← near ridge silhouette
│                                                             │
│    Junior Full-Stack Developer · Backend Focus              │
│    Indonesia · Bina Darma University · 3.72/4.00            │
│                                                             │
│    [ Explore Projects ]   Contact Me →                      │
│                                                             │
│  ↓ scroll                                          (rail)   │
└────────────────────────────────────────────────────────────┘
```

- The lower ~38% of the viewport is a **near-silhouette ridge**, within 6–10% lightness of the sky. Text never enters it.
- Name at `clamp(2.75rem, 7vw, 6.5rem)`, line-height 0.95, letter-spacing −0.02em, colour = chapter ink token.
- The `01` numeral at `clamp(6rem, 18vw, 16rem)`, weight 200–300, opacity 0.16, may be clipped by the ridge silhouette.
- No portrait in this chapter. The portrait, if one exists, lives in Chapter 02. `PROPOSED`

**Entry behaviour.** 1200ms "elevation" reveal: sky fades in from `opacity 0`; ridges arrive `translateY(24px) → 0` in 90ms staggered steps; name mask-reveals left→right over 700ms with `power2.out`; CTAs fade last. One play on load, nothing loops.

**Exit.** On scroll the near ridge rises faster than the far ridge (parallax, §12.4). At the chapter end the ridge line reaches mid-viewport and dissolves into Chapter 02's forest floor. No hard cut.

---

### 5.2 Chapter 02 — THE JOURNEY

**Purpose.** Background, education, experience, philosophy, direction — grounded and human.

**Content blocks (in order):**

1. **Kicker:** "Background"
2. **Title:** "The Journey"
3. **Lede** `PROPOSED`: "Formal training in Informatics, then real systems built for real users."
4. **Education** — Bina Darma University, Informatics Engineering, 2021–2025, GPA 3.72/4.00. `VERIFIED`
5. **Experience** — two entries required, content `NEEDS USER INPUT`:
   - Internship (organisation, role, period, 2–3 responsibilities, stack)
   - BAPAS OKU Connect (organisation, role, period, 2–3 responsibilities, stack)
6. **Development philosophy** — 2 short paragraphs. `NEEDS USER INPUT` (draft below)
7. **Career direction** — 1 paragraph: backend depth first, full-stack breadth second. `PROPOSED`

**Philosophy draft** `PROPOSED`:
> "I would rather ship a small system I understand completely than a large one I mostly understand. Most of my decisions are about where a rule should live — in the database, in the API, or in the interface — and I try to put it as low in the stack as correctness allows."

**Composition.** A vertical thread runs the chapter's full height — a 1px rule at x=18% on desktop. Entries attach to it as text blocks, not boxed cards. Dates sit in the margin, small, uppercase, tracking +0.14em. This is the only place in the site where a vertical rule is used.

```
   │
2021─┼─ Bina Darma University
   │  Informatics Engineering · 2021–2025
   │  GPA 3.72 / 4.00
   │
20XX─┼─ [Internship role]
   │  [Organisation] · [period]
   │  · responsibility
   │  · responsibility
   │
20XX─┼─ BAPAS OKU Connect
   │  ...
   │
   └─ Philosophy
      [two paragraphs]
```

**Landscape state.** Morning light entering from the right; forest ridge layers; a low warm glow that strengthens with chapter progress.

**Exit.** The vertical thread fades out over the last 15% of the chapter; forest gives way to open dunes and the palette warms perceptually.

---

### 5.3 Chapter 03 — THE EXPEDITIONS

**Purpose.** The centre of gravity. Four projects, each given real space and real reasoning.

**Structure.** Four sequential full-height project movements — **not** a grid of cards.

`PROPOSED` — Each project occupies ~105vh on desktop:

```
┌──────────────────────────────────────────────────────────┐
│  03 · EXPEDITIONS                            01 / 04      │  ← progress index
│                                                           │
│  ┌──────────────┐   PROJECT NAME (serif, large)          │
│  │              │   Role · Period · Stack line            │
│  │  landscape   │                                          │
│  │  vignette /  │   Problem — 2 sentences                  │
│  │  diagram     │   Approach — 2–3 sentences               │
│  │              │                                          │
│  └──────────────┘   ▸ Technology decisions                │
│                      ▸ What I built                       │
│                      ▸ Challenges                         │
│                                                           │
│                      [ Case Study ]  [ GitHub ]           │
└──────────────────────────────────────────────────────────┘
```

- **The visual slot** (left, 44% width) holds either an abstract landscape vignette in the chapter's environment **or** an original architecture diagram (SVG, §7.6). Never a fake browser screenshot. Never a stock mockup.
- **Differentiation between projects** comes from the environment and the diagram — not coloured card borders.
- **Detail depth:** the full case study opens in an in-page sheet. The existing `ProjectDetail` lightbox pattern is retained in spirit, restyled: full-viewport sheet on mobile, centred 880px sheet on desktop. Esc / close / backdrop close it; focus trapped and returned. `VERIFIED` (pattern already implemented)
- **No hover-only information.** Every essential fact is visible without interaction; hover adds only motion and affordance.

**Landscape state.** Warm desert, high sun, dust haze. Strongest saturation of the site — still flat, still ~4 hues.

**Exit.** Dust rises over the last project; the desert drains to blue.

---

### 5.4 Chapter 04 — THE TOOLKIT

**Purpose.** Technical capability without childish skill bars.

**Content** — six groups, drawn only from technologies evidenced in the four projects `VERIFIED`:

| Group | Items |
|---|---|
| Backend Engineering | NestJS, Node.js, REST API design, TypeScript |
| Frontend Development | Next.js, React, TypeScript, HTML/CSS, Tailwind CSS `NEEDS USER INPUT` (confirm) |
| Databases | MySQL, Prisma ORM, relational schema design |
| Authentication & Security | HttpOnly JWT, CSRF double-submit, bcrypt, RBAC, refresh-token rotation, session revocation, login throttling |
| Development Tools | `NEEDS USER INPUT` — only what was actually used (Git, GitHub, Postman, VS Code assumed) |
| Testing & Quality | `NEEDS USER INPUT` — list only real practice; do not claim Jest/Supertest without evidence |

**Presentation.** A single asymmetric field — group name in small caps at left, items as plain text separated by mid-dots, flowing in natural lines. No boxes, chips, pills, icons, or proficiency.

```
BACKEND ENGINEERING    NestJS · Node.js · REST API design · TypeScript
FRONTEND DEVELOPMENT   Next.js · React · TypeScript · HTML/CSS
DATABASES              MySQL · Prisma ORM · Relational schema design
AUTHENTICATION         HttpOnly JWT · CSRF double-submit · bcrypt
                       RBAC · Refresh-token rotation · Session revocation
DEV TOOLS              [NEEDS USER INPUT]
TESTING & QUALITY      [NEEDS USER INPUT]
```

`PROPOSED` — items the owner has not actually used must be cut. A shorter honest list is stronger than a long one.

**Landscape state.** Blue hour. Sky Glacier Blue → Midnight; ridge values compressed into a narrow mid-toned band; the few highlights are Golden Hour.

---

### 5.5 Chapter 05 — THE QUIET MOMENT

**Purpose.** Slow down. Communicate how the owner thinks about software. This is the chapter that makes a senior reviewer take a junior seriously.

**Content** — 4–5 short statements, each 1–2 sentences, wide vertical spacing. Themes: reliability, backend architecture, API design, authentication and authorization, database design, security-conscious development, continuous learning.

**Draft copy** `PROPOSED`:

> **Reliability is a design decision, not a quality phase.**
> The database should refuse bad states even if the API forgets to.

> **An API is a contract with someone you will never meet.**
> Names, errors, and status codes are documentation.

> **Authentication is where a product is most easily wrong.**
> HttpOnly cookies, rotating refresh tokens, CSRF protection, and revocation are not extras.

> **Security is cheaper the lower it lives.**
> Validate at the boundary; constrain in the schema; never trust the client.

> **Still learning.**
> Currently deepening backend architecture patterns and production-grade error handling.

**Presentation.** Extremely spare. One statement per viewport on mobile; two per viewport on desktop. No imagery except the night sky and a single horizon line.

**Landscape state.** Midnight. Near-black sky, a faint static star field (CSS radial-gradient dot tile — not a particle engine), a very low ridge. Text in Warm Ivory.

**Exit.** Slow warm lightening from the bottom edge — the night is ending.

---

### 5.6 Chapter 06 — THE NEXT HORIZON

**Purpose.** Convert interest into contact; close the journey.

**Content:**

| Item | Value |
|---|---|
| Closing statement | `PROPOSED` — "There's more being built. If any of it is relevant to your team, I'd like to hear from you." |
| Email | `NEEDS USER INPUT` |
| GitHub | `NEEDS USER INPUT` |
| LinkedIn | `NEEDS USER INPUT` |
| Resume | `NEEDS USER INPUT` — PDF, filename `NEEDS USER INPUT` |
| Location line | Indonesia |

**Composition.** The horizon sits at ~62% height — lowest of the site, maximum sky. Content is bottom-weighted, small, quiet. Email is the largest element, set as a text link (not a button), with a 1px underline that grows on hover.

```
                      (vast sky)
──────────────────────────────────────  ← horizon, golden
   NEXT HORIZON

   Sakbanullah Dwi Oktavian
   Junior Full-Stack Developer · Backend Focus

   [email — large serif link]
   GitHub · LinkedIn · Resume (PDF)

   © 2026 · Built and maintained by hand.
```

**Landscape state.** Sunrise — Golden Hour bleeding into Pale Sky; silhouettes at the day's lowest value; a long shadow gradient from the bottom.

**Exit.** Nothing after it but the horizon and a hairline footer. No "back to top" button; the chapter rail is enough. `PROPOSED`

---

## 6. Project Content Specifications

Rules for all four: **describe only functionality actually implemented.** Numbers supplied by the owner are `VERIFIED` and may be used. Anything absent is `NEEDS USER INPUT` and must never be filled in.

### 6.1 Raccoon Coffee

**Overview** `VERIFIED`
A full-stack coffee shop website with a custom admin CMS. Public visitors browse the menu and a moderated anonymous photo wall; staff manage content without touching the codebase.

**Problem**
Small coffee shops usually run their web presence through generic CMS plugins or third-party menu apps: content lives outside the product, image handling is uncontrolled, and there is no moderation layer for user-submitted photos. `PROPOSED` framing — owner to confirm.

**Why it was built** `NEEDS USER INPUT` — coursework, client, or self-directed. Do not invent.

**Contributions** `VERIFIED` (confirm solo/team)
- Full-stack implementation: Next.js/React front end, NestJS/Prisma/MySQL back end.
- Admin CMS: menu and category management; content and image management.
- Moderated anonymous photo wall (public upload → moderation queue).
- 48 API endpoints; 8-model database schema.
- Secure file upload validation.
- HttpOnly JWT authentication, CSRF double-submit protection, bcrypt hashing, login throttling, server-side session revocation.

**Technical decisions** (present the reasoning; confirm in owner's own words)

| Decision | Reasoning to present |
|---|---|
| JWT in HttpOnly cookies, not localStorage | Removes the XSS token-exfiltration path |
| CSRF double-submit | Required compensation once auth lives in cookies |
| bcrypt | Slow-by-design hashing, per-password salt |
| Login throttling + server-side revocation | Limits credential stuffing; lets sessions actually be killed |
| Prisma + MySQL | Typed queries over a relational schema; migrations as source of truth |
| Eight models | Small explicit schema — content, categories, media, moderation queue, users |

**Architecture highlights** — API/module outline; request path for an authenticated admin mutation; request path for an anonymous photo submission. `NEEDS USER INPUT`: does the front end call NestJS directly or through Next.js route handlers?

**Challenges and solutions** `NEEDS USER INPUT`. Safe candidates implied by the verified feature list: file-upload validation (MIME vs extension vs magic bytes), moderation workflow states, session revocation bookkeeping alongside stateless JWTs.

**Verified results** — 48 endpoints; 8-model schema; the features above. **No performance, user, or business metrics.**

**Stack** `VERIFIED`: Next.js · React · TypeScript · NestJS · Prisma · MySQL

**Links** — GitHub `NEEDS USER INPUT`. Live demo `NEEDS USER INPUT`; omit the control entirely if none.

**Visual storytelling direction** — dawn-dune environment. Visual slot: simplified tier diagram, *browser → Next.js app → NestJS API → Prisma → MySQL*, with the auth boundary drawn as a distinct horizontal rule and the moderation queue called out as a state machine.

---

### 6.2 Gawe

**Overview**
A career discovery and application workflow platform built around a "master CV" that becomes the single source of truth for every downstream artefact. Component scope `VERIFIED`; overall scope statement `NEEDS USER INPUT`.

**Problem**
Applying broadly means rewriting the same document, losing track of which version went where, and guessing whether a posting is worth the effort. Gawe centralises the source, evaluates fit, and tracks the application through to export.

**Why it was built** `NEEDS USER INPUT`

**Implemented areas** `VERIFIED` — describe only these:
- **Master CV** — canonical profile/document source.
- **Job discovery** — collecting postings.
- **Eligibility evaluation** — rule-based check against hard requirements.
- **Job-fit assessment** — scoring a posting against the master CV.
- **Application document generation** — tailored documents from the master CV.
- **Approval workflow** — review step before documents leave the system.
- **Export workflow** — final output.

**Technical decisions** `NEEDS USER INPUT` — the brief gives no stack. Do not assume. Confirm: is fit assessment deterministic rules or model-assisted? Where are generated documents stored? Is approval single- or multi-step?

**Challenges and solutions** `NEEDS USER INPUT`

**Verified results** — the seven implemented areas. **Do not invent: accuracy percentages, time saved, number of jobs processed.**

**Stack** `NEEDS USER INPUT`

**Links** — GitHub `NEEDS USER INPUT`; demo `NEEDS USER INPUT`.

**Visual storytelling direction** — forest-alpine environment. Visual slot: the pipeline `Master CV → Discovery → Eligibility → Fit → Generate → Approve → Export`, one horizontal arrow chain with the master CV as a forking source. This is the one project where the diagram must carry the story.

---

### 6.3 BAPAS OKU Connect

**Overview**
An internal management application built collaboratively by a team. `VERIFIED`

**Problem** `NEEDS USER INPUT` — describe the workflow it replaces, without naming individuals or disclosing sensitive institutional data.

**Why it was built** `NEEDS USER INPUT`

**My contribution — must be visually separated from team functionality** `VERIFIED`:
- **Role-Based Access Control (RBAC)** — roles, permissions, enforcement.
- **Refresh-token authentication** — refresh-token issuance, rotation, validation.

Everything else is presented as **team-wide**. The page must render this distinction explicitly — a two-column block, *"What I built"* / *"Built by the team"* (team column `NEEDS USER INPUT`).

**Technical decisions** `NEEDS USER INPUT` — confirm stack and the RBAC model (role → permission mapping? resource-level?).

**Challenges and solutions** `NEEDS USER INPUT`

**Verified results** — RBAC and refresh-token auth only.

**Stack** `NEEDS USER INPUT`

**Links** — likely private. If no public repository exists, render GitHub disabled with an honest note ("internal project — repository private"). `PROPOSED` Never fabricate a URL.

**Visual storytelling direction** — blue-hour environment. Visual slot: the authorization path `request → token verification → role resolution → permission check → handler`, with the two owner-built stages highlighted and the rest rendered lighter. Makes the contribution legible without a claim.

---

### 6.4 AgroLedger

**Overview**
Agricultural financial management for palm oil and rubber operations — recording, categorising, and reconciling operational costs and income for smallholder-scale estates. `VERIFIED` at domain level; scope detail `NEEDS USER INPUT`.

**Problem**
Palm oil and rubber smallholders track costs across harvest cycles, labour, fertiliser, and transport in informal ledgers, which makes per-block profitability invisible and reconciliation painful. `PROPOSED` — confirm as the real motivation.

**Why it was built** `NEEDS USER INPUT`

**My contribution** `NEEDS USER INPUT` (solo or team?)

**Technical approach** `NEEDS USER INPUT` — stack, data model, offline/deployment assumptions.

**Challenges and solutions** `NEEDS USER INPUT`. Safe candidates: modelling per-block accounting, variable harvest cycles, keeping data entry fast enough for field use.

**Verified results** — problem domain and domain scope only. **Explicitly must not invent:** user counts, OCR accuracy, productivity gains, time savings, financial impact.

**Stack** `NEEDS USER INPUT`

**Links** — GitHub `NEEDS USER INPUT`; demo `NEEDS USER INPUT`.

**Visual storytelling direction** — warm desert-to-dusk environment. Visual slot: the data model as an abstract landscape — plots/blocks as terraced bands, transactions as marks flowing down into a single ledger line. Metaphor carries meaning; no charts with invented numbers.

---

### 6.5 Cross-project content rules

1. Every project shows exactly one **evidence line** — a verified, checkable fact (e.g. "48 API endpoints · 8-model schema"). No other numbers.
2. "Case Study" opens the full detail in a real dialog with focus management.
3. GitHub is a text link, never a button-styled box.
4. Empty demo → the control is omitted, not disabled, unless omission would read as an oversight (BAPAS case, §6.3).
5. Order: Raccoon Coffee → Gawe → BAPAS OKU Connect → AgroLedger. `PROPOSED` — strongest and most complete first.

---

## 7. Landscape and Environmental Art Direction

### 7.1 The six-layer stack

Every chapter uses the same stack, always in this order (back to front):

| # | Layer | Content | Parallax factor | Implementation |
|---|---|---|---|---|
| 0 | Sky | Vertical gradient, chapter-dependent | 0.00 (fixed) | CSS `linear-gradient` on a sticky layer |
| 1 | Celestial | Sun/moon glow, stars | 0.02 | Radial gradient, 1 element |
| 2 | Far ridge | Distant profile, 12–18% sky contrast | 0.06 | Inline SVG path |
| 3 | Mid ridge | Second profile, 20–30% contrast | 0.14 | Inline SVG path |
| 4 | Near ridge | Foreground silhouette, highest contrast | 0.30 | Inline SVG path |
| 5 | Atmosphere | Haze band at the horizon seam | 0.10 | CSS gradient overlay |

The sky never moves: it is the frame. Content always sits above layer 5 in z-order. Text never overlaps layer 4's silhouette.

### 7.2 Chapter environments

| Ch | Environment | Sky | Ridges | Accent | Notes |
|---|---|---|---|---|---|
| 01 | Snow mountains, dawn | Pale Sky → Snow Mist | 3 layers, cool, low contrast | Golden Hour rim light | Highest key; must show full identity in the first viewport |
| 02 | Forest / alpine morning | Snow Mist → Glacier Blue | 3 layers, warmer mid, softer edges | Golden Hour glow from right | Light source becomes lateral |
| 03 | Warm desert, high sun | Desert Sand → Pale Sky | 2 low dunes + distant mesa | Mountain Blue shadows | Highest saturation; strongest haze |
| 04 | Blue hour | Glacier Blue → Mountain Blue | 3 compressed layers | Golden Hour last light, minimal | Sky almost flat; ridges merge |
| 05 | Midnight | Midnight → near-black | 1 low ridge only | Warm Ivory text, faint stars | Quietest composition |
| 06 | Sunrise | Golden Hour → Pale Sky | 2 layers, silhouettes at lowest value | Warm Ivory | Horizon at 62% height |

### 7.3 Composition rules

1. **Horizon position varies by chapter** — 46%, 52%, 44%, 58%, 70%, 62% of viewport height. This is the site's rhythm; never keep it constant across two consecutive chapters.
2. **Inverted thirds:** the landscape occupies the *lower and right* of the frame; text sits upper-left in a column ≤ 620px. The text may shift right at most once, in Chapter 04. `PROPOSED`
3. **Ridge profiles are original.** Hand-drawn bezier paths, 6–12 control points, subtly irregular, no symmetric peaks, no recognisable game silhouette.
4. **Value discipline:** at most 3 distinct values in the ridge stack at any time. Depth comes from 6–10% lightness steps, never from blur.
5. **The horizon seam** is always softened by an atmosphere band (60–120px gradient) so ridges never look like cut paper — except Chapter 05, where one hard edge is allowed, deliberately.

### 7.4 Atmospheric depth and lighting transitions

- The document interpolates one set of CSS custom properties (`--sky-top`, `--sky-bottom`, `--ridge-1`, `--ridge-2`, `--ridge-3`, `--ink`, `--ink-muted`, `--accent`) as a function of scroll progress. Values are defined per chapter and blended by a small colour ramp (sRGB acceptable; `oklab` preferred where supported).
- Interpolation is **scrubbed**, not timed: it advances with scroll and never runs ahead of the visitor.
- Chapter transitions overlap: the last 20% of the outgoing chapter blends with the first 10% of the incoming one. No visible seam, no snap.

### 7.5 Detail budget

No birds, no snowfall, no drifting clouds, no particles, no grain animation, no lens flares, no light rays, no floating grass. One static noise texture at ≤ 3% opacity may be used globally to prevent gradient banding. That is the entire budget. `PROPOSED`

### 7.6 Implementation format

- All landscape art is **inline SVG paths + CSS gradients**, not raster. Rationale: ~2–4 kB gzipped total, resolution-independent, recolourable by token, no CLS, no image CDN.
- If an owner-supplied photograph is used anywhere, it is the only raster asset and is served at 3 widths with `srcset`, AVIF/WebP.
- Diagrams are SVG too: 1px strokes, no fills except one accent tint at ≤ 12% opacity, labels in mono at 12–13px.

---

## 8. Color System

### 8.1 Tokens

Components use semantic names only; palette names never appear in UI code.

```css
:root {
  /* palette — source of truth */
  --snow-mist:     #E8E9E3;
  --glacier-blue:  #B7CDD0;
  --pale-sky:      #DCE6E4;
  --golden-hour:   #D8A46A;
  --desert-sand:   #F0D7A6;
  --mountain-blue: #263B4A;
  --midnight:      #111D2B;
  --warm-ivory:    #F7F4EB;

  /* derived ink ramp — required for AA on light environments */
  --ink-strong:    #263B4A;  /* 10.57:1 on Warm Ivory */
  --ink-body:      #46586A;  /* 6.67:1 on Warm Ivory  (added) */
  --ink-quiet:     #5C6E7E;  /* decorative / large text only */
  --ink-inverse:   #F7F4EB;  /* 10.57:1 on Mountain Blue */
  --ink-inv-muted: #9FB0BC;  /* 7.62:1 on Midnight */
  --accent:        #8C5A2B;  /* deep golden hour — text-safe on light */
  --accent-bright: #D8A46A;  /* on dark environments only */
}
```

**Refinements to the supplied palette** `PROPOSED`, with measured justification:

| Addition | Reason |
|---|---|
| `--ink-body: #46586A` | Full Mountain Blue body copy is heavy; a blue-grey stays in family while easing the page. 6.67:1 on Warm Ivory, 6.00:1 on Snow Mist. |
| `--accent: #8C5A2B` | Literal `#D8A46A` fails as text on Warm Ivory and Desert Sand. Used only as a fill/highlight on light chapters; text links use `--accent`. |
| `--accent-bright: #D8A46A` | On dark chapters it reaches 7.65:1 on Midnight — correct accent there. |
| `--ink-inv-muted: #9FB0BC` | Secondary text on dark chapters: 7.62:1 on Midnight, 5.21:1 on Mountain Blue. |
| Snow Mist / Pale Sky / Glacier Blue | **Atmosphere only.** Never text, never a content surface. |

### 8.2 Per-chapter assignment (measured)

| Ch | Sky top → bottom | Ink | Ink muted | Accent | Contrast |
|---|---|---|---|---|---|
| 01 | `--pale-sky` → `--snow-mist` | `--mountain-blue` | `--ink-body` | `--accent` | 9.12 / 5.75 — pass |
| 02 | `--snow-mist` → `--glacier-blue` | `--mountain-blue` | `--ink-body` | `--accent` | 9.52 / 6.00 — pass |
| 03 | `--desert-sand` → `--pale-sky` | `--mountain-blue` | `--mountain-blue` @88% | `--mountain-blue` | 8.29 / — pass |
| 04 | `--glacier-blue` → `--mountain-blue` | `--warm-ivory` | `--ink-inv-muted` | `--accent-bright` | 10.57 / 5.21 — pass |
| 05 | `--midnight` → `#0A121C` | `--warm-ivory` | `--ink-inv-muted` | `--accent-bright` | 15.47 / 7.62 — pass |
| 06 | `--golden-hour` → `--pale-sky` | `--mountain-blue` | `--ink-body` | `--mountain-blue` | 5.22 → 8.29 — pass |

Ratios computed with WCAG 2.1 relative luminance. Chapter 06 Mountain Blue on Golden Hour is 5.22:1 — passes AA normal text but marginal at 14px, so body copy in Chapter 06 sits on the Pale Sky portion of the gradient, never inside the golden band.

### 8.3 Rules

- Every colour in a component comes from a token. No hex literals in JSX or component CSS.
- Overlays over raster use a token at a fixed opacity; never inline `rgba()`.
- No state colours (success/error) — the site has no forms in this phase.
- Focus ring: `--accent` 2px, offset 2px on light chapters; `--accent-bright` on dark. Must reach 3:1 against the adjacent colour.

---

## 9. Typography System

### 9.1 Pairing `PROPOSED`

| Role | Family | Axes/weights | Why |
|---|---|---|---|
| Display | **Fraunces** (variable) | 300 / 400, `opsz` 72–144, SOFT 0, WONK 0 | Expressive, high-contrast editorial serif with real personality at large sizes; optical size axis keeps small headings from looking brittle |
| Body / UI | **Inter** (variable) | 400 / 500 | Neutral, legible at 16–18px, excellent small-caps tracking |
| Data | **JetBrains Mono** | 400 | Endpoint counts, stack lists, diagram labels — a deliberate engineering voice |

Google Fonts only, `display=swap`; preload Fraunces display subset and Inter 400. JetBrains Mono loads lazily or is self-hosted at one weight.

Fallbacks: `Georgia, 'Times New Roman', serif` and `system-ui, -apple-system, 'Segoe UI', sans-serif`.

**Rejected for the record:** Playfair Display (over-familiar, wedding-invitation), Cormorant (fragile at 16px), Space Grotesk (startup template smell), any mono display face.

### 9.2 Fluid type scale

Base 16px; ratio ≈ 1.25 on mobile, 1.333 on desktop.

| Token | `clamp()` | Line-height | Tracking | Use |
|---|---|---|---|---|
| `--type-display` | `clamp(2.75rem, 7.2vw, 6.5rem)` | 0.95 | −0.02em | Chapter 01 name only |
| `--type-h1` | `clamp(2rem, 4.6vw, 3.75rem)` | 1.02 | −0.015em | Chapter titles, project names |
| `--type-h2` | `clamp(1.5rem, 2.6vw, 2.25rem)` | 1.12 | −0.01em | Subsection titles, philosophy statements |
| `--type-h3` | `clamp(1.125rem, 1.6vw, 1.375rem)` | 1.25 | 0 | Entry titles, group names |
| `--type-lede` | `clamp(1.125rem, 1.5vw, 1.375rem)` | 1.55 | 0 | Chapter lede, max 2 lines |
| `--type-body` | `clamp(1rem, 1.05vw, 1.0625rem)` | 1.68 | 0 | All body copy |
| `--type-small` | `0.875rem` | 1.55 | 0 | Captions, metadata |
| `--type-kicker` | `0.75rem` | 1.2 | +0.18em uppercase | Kickers, labels, rail |
| `--type-mono` | `0.8125rem` | 1.5 | +0.02em | Stack lists, diagram labels |
| `--type-numeral` | `clamp(6rem, 18vw, 16rem)` | 0.8 | −0.04em | Chapter numerals (decorative, `aria-hidden`) |

Rules:
- Body measure `max-width: 62ch`. Never wider.
- No text below 14px. No arbitrary `text-[11px]` sizes (a prior bug in this project).
- Headings `text-wrap: balance`; body `text-wrap: pretty` where supported.
- `font-variant-numeric: tabular-nums` only in tables/specs.
- Baseline rhythm: 8px.

---

## 10. Layout and Spacing System

### 10.1 Grid

- **Desktop ≥ 1200px:** 12 columns, 24px gutter, outer margin `max(24px, 6vw)`, max content width 1280px.
- **Editorial column occupies columns 1–6** (≈600px max). Columns 7–12 are landscape-only, except the project visual slot, which claims 7–10.
- **Tablet 768–1199px:** 8 columns, 20px gutter, content 1–6.
- **Mobile < 768px:** 4 columns, 16px gutter, 16px outer margin, content spans 1–4.

### 10.2 Spacing scale

Base 4px; these steps only:

```
2  4  8  12  16  24  32  48  64  96  128  192  (px)
```

| Token | Value | Use |
|---|---|---|
| `--space-block` | 24px | Between paragraphs / list items |
| `--space-group` | 64px desktop / 40px mobile | Between content groups |
| `--space-chapter` | 192px desktop / 96px mobile | Before a chapter title |
| `--space-air` | 40vh | Deliberate emptiness before an environment shift |

### 10.3 Horizontal composition

- Content left-aligned at the outer margin on mobile, column 1 on desktop.
- Hard maximums: 62ch body, 28ch display headings (forces the two-line name).
- Nothing is centred except the Chapter 06 closing block and the Chapter 05 statements. Centring is a signal, used twice.

### 10.4 Breakpoints

| Name | Min-width | Purpose |
|---|---|---|
| `xs` | 380px | Existing token; keep |
| `sm` | 640px | Landscape becomes side-lit; project visual slot moves beside text |
| `md` | 768px | Tablet; 8-column grid |
| `lg` | 1024px | Chapter rail appears; full parallax enabled |
| `xl` | 1440px | Max content width reached; landscape gains air |
| `2xl` | 1920px | Landscape layers extend; content stays capped |

---

## 11. Component and Interaction Specifications

### 11.1 Component inventory

| Component | Purpose | Notes |
|---|---|---|
| `ChapterShell` | Wraps a chapter, owns environment state | Sets CSS vars from scroll progress |
| `ChapterMarker` | Numeral + kicker + title + lede | One per chapter |
| `ChapterRail` | Fixed right-edge navigation | Desktop only |
| `ChapterSheet` | Mobile chapter menu | Full-screen overlay |
| `Prose` | Body copy with measure + rhythm | Variants: `lede`, `body`, `small` only |
| `EntryRow` | Timeline entry, Chapter 02 | Not a card |
| `ProjectMovement` | One project, Chapter 03 | Composition per §5.3 |
| `ProjectSheet` | Full case-study detail | Replaces `ProjectDetail` |
| `Diagram` | Inline SVG architecture figure | Mono labels |
| `SkillField` | Chapter 04 groups | Plain text rows |
| `Statement` | Chapter 05 block | Large, centred, one per beat |
| `ContactLink` | Email / GitHub / LinkedIn / Resume | Text link, growing underline |
| `HorizonRule` | 1px hairline | Used sparingly; never inside content |

**Removed from the current codebase** `PROPOSED`: `Card`, `Stamp`, `Divider`, `ChapterNav`, `ThemeToggle`, `.paper-cut`, `.vertical-title`, `.roller`, kanji ornaments. The redesign has no cards, no stamps, no vertical Japanese glyphs.

### 11.2 Buttons and links

Exactly **one** button style and **two** link styles. No pills, ghost buttons, or icon buttons.

**Primary action** (used twice: "Explore Projects", "Email"):
```
background: transparent
border: 1px solid currentColor @ 60%
padding: 14px 22px
radius: 2px
type: Inter 500, 15px, tracking +0.01em
hover:  background currentColor @ 6%, border 100%, arrow translateX(3px)
focus-visible: 2px accent outline, offset 2px
active: translateY(1px)
```

**Inline link** (GitHub, LinkedIn, references): `currentColor`; 1px underline at 40% opacity; `text-underline-offset: 3px`; hover → underline 100%, no colour change.

**Chapter link** (rail/sheet): kicker-size uppercase; accent dot when active.

### 11.3 States

| State | Definition |
|---|---|
| Hover | Pointer devices only (`@media (hover:hover)`). One property change + one transform ≤3px. |
| Focus-visible | 2px accent outline, 2px offset, never removed. |
| Active | 1px translate; nothing else. |
| Visited | No distinct style (single document). |
| Disabled | Only a private-repo GitHub link: 45% opacity, `aria-disabled="true"`, inline explanation. |

### 11.4 Project interaction

- Each `ProjectMovement` is fully readable without interaction.
- "Case Study" is a link-styled `<button>` opening `ProjectSheet`.
- `ProjectSheet`: `role="dialog" aria-modal="true"`, labelled by the project title, focus trapped, Esc closes, backdrop closes, focus returns to trigger. Inner scroll native; body scroll locked via the existing `getLenis()` stop/start pattern.
- Mobile: full-viewport sheet, 44px close target top-right, sticky 56px title bar.

### 11.5 Mobile navigation

- No conventional hamburger. Top-right shows current chapter numeral plus a 3-line mark, 44×44px.
- Tapping opens `ChapterSheet`: full-screen, sky-coloured, six rows — numeral (small, mono), title (serif, 28px), one-line description (small, muted). Current chapter marked with an accent dot.
- Closes on row activation (navigates + closes), Esc, or the close mark. Focus trapped; returns to the index mark.

### 11.6 Contact interaction

- Email is a `mailto:` with the address visible as text (`NEEDS USER INPUT`).
- Resume opens in a new tab, `rel="noopener"`, `download` where appropriate.
- `PROPOSED` — no toast, no inline confirmation; the mail client opening is the feedback.

---

## 12. Motion and Transition Specifications

### 12.1 Principles

1. **Scrubbed, not timed,** for anything scroll-linked. It cannot desync.
2. **Entrances use `once`** and never replay.
3. **No element animated by two libraries.** Existing `AGENT.md` rule, retained.
4. **Motion is optional by construction:** every effect has a complete static resting state (content visible, colours set at the chapter's mid value).
5. **Nothing moves faster than the visitor scrolls.**

### 12.2 Libraries and responsibilities

| Concern | Tool |
|---|---|
| Smooth scroll + global rAF ticker | Lenis `1.3.x` (existing) |
| Scroll-scrubbed colour interpolation, parallax, progress | GSAP + ScrollTrigger `3.15.x` (existing) |
| Load-time entrance, sheet/menu enter-exit | framer-motion `14.x` (existing) |
| Hover / focus | CSS only |

No new dependencies. **No WebGL, no canvas animation library, no Lottie.** `PROPOSED`

### 12.3 Duration and easing

| Event | Trigger | Duration | Easing |
|---|---|---|---|
| Load — sky | `load` +100ms | 900ms | `power1.out` |
| Load — ridge stagger | `load` +250ms, 90ms stagger | 700ms each | `power2.out` |
| Load — name reveal | `load` +600ms | 700ms | `power2.out` |
| CTAs fade | `load` +1100ms | 400ms | `power1.out` |
| Chapter colour blend | scroll scrub | continuous | `power1.inOut` per segment |
| Ridge parallax | scroll scrub `0.6` | continuous | — |
| Chapter numeral drift | scroll scrub | continuous | — |
| Project visual reveal | viewport enter, `once` | 600ms | `power2.out` |
| Project sheet open / close | click | 320ms / 220ms | `power2.out` / `power2.in` |
| Chapter sheet open | click | 280ms | `power2.out` |
| Hover | pointer enter | 160ms | `ease-out` |
| Focus ring | immediate | 0ms | — |
| Rail active marker | IntersectionObserver | 200ms opacity | `ease-out` |

**Ceiling:** nothing above 1200ms; nothing above 600ms except the load sequence.

### 12.4 Parallax ranges (desktop ≥ 1024px)

Per chapter, layered `translateY` from chapter start to end:

| Layer | Range | Notes |
|---|---|---|
| Far ridge | 0 → −40px | Never more than 5% of viewport |
| Mid ridge | 0 → −90px | |
| Near ridge | 0 → −180px | Must never cover text; content sits above in z-order |
| Celestial glow | 0 → −12px | |
| Chapter numeral | 0 → +60px | Counter-parallax with content intent |
| Text content | **0** | Text never parallaxes |

At ≤767px all ridge ranges halve. At `prefers-reduced-motion: reduce` all are 0.

### 12.5 Reduced motion

`prefers-reduced-motion: reduce` →

- No Lenis, no smooth scroll (instant anchors).
- No parallax, no numeral drift.
- Colour interpolation snaps per chapter — each chapter gets its assigned palette at its start, no blend.
- Load sequence becomes one 200ms page fade.
- Sheets still open and close, instantly, with correct focus management.
- **All content visible at rest.** No `opacity: 0` resting states anywhere (retained project rule).

### 12.6 Mobile performance

- Parallax uses `transform` only, on ≤3 elements per chapter, with `will-change` applied at chapter enter and removed at exit.
- No `backdrop-filter`, no `filter: blur()`, no large box-shadows during scroll.
- `ScrollTrigger` with `scrub: 0.6`; **no pinning anywhere** — the main source of jank and a11y trouble.
- Colour interpolation writes CSS custom properties on one node per frame (`:root` or the chapter shell), never inline styles on many nodes.
- Target ≤8ms per frame on a mid-range Android; verify with DevTools CPU 4× throttle.

---

## 13. Responsive Design Specifications

### 13.1 Desktop ≥1440px

- Landscape occupies ~45% of the frame; text column 620px starting at column 1.
- Chapter rail visible, 24px from the right edge, vertically centred.
- Full parallax; full-length load sequence.
- Project movements alternate visual-left/text-right, then text-left/visual-right — twice each. `PROPOSED`

### 13.2 Tablet 768–1199px

- 8-column grid; content 1–6; landscape still full-bleed behind.
- Chapter rail only ≥1024px; below that the mobile chapter index takes over.
- Project visual moves **above** the text, full width, 16:9 — side-by-side gets cramped in portrait.
- Parallax halved.

### 13.3 Mobile <768px (design target 390×844)

Mobile is a **separate composition**, not a shrink:

1. **Landscape is portrait.** Ridge profiles are regenerated per chapter for a tall frame — a wide silhouette letterboxed into a phone reads as a banner, not a vista. Sky occupies ~60% of the first viewport.
2. **The horizon sits lower** (68–72%) so the first screen is mostly sky + name.
3. **Name at `clamp(2.75rem, 12vw, 4rem)`**, up to three lines ("Sakbanullah" / "Dwi" / "Oktavian").
4. **Tracked small caps persist** at a smaller size — they carry the editorial voice.
5. **Chapter index** replaces the rail (§11.5).
6. **Project movements go vertical:** title → evidence line → visual → problem → contribution → case-study link. Visual slot 4:3, full-bleed to the gutters.
7. **Chapter 05 statements** become one per viewport, centred, with 40vh of sky above.
8. **Tap targets ≥44×44px**; text links get ±8px invisible padding.
9. **No hover states** — `@media (hover:hover)` guards every hover rule.
10. **Parallax ≤90px total on 2 layers only.**

### 13.4 Test widths

`320, 360, 390, 430, 768, 1024, 1280, 1440, 1920, 2560` — assert `scrollWidth === innerWidth` at each, in both reduced-motion states.

---

## 14. Accessibility Requirements

1. **Semantics.** One `<h1>` (the name); `<h2>` per chapter title; `<h3>` per project/entry. `<main>`, `<nav aria-label="Chapters">`, `<footer>`. Numerals, kickers, and decorative landscape SVGs are `aria-hidden="true"`. Diagrams are `role="img"` with a `<title>`.
2. **Contrast.** All text meets WCAG AA (4.5:1 body, 3:1 large/UI). §8.2 ratios are computed, not estimated. Because scroll interpolation passes through intermediate colours, the text colour interpolates alongside the background so the pair stays compliant at **every** scroll position — assert this at multiple progress points during QA, not only at chapter endpoints.
3. **Keyboard.** Everything reachable in DOM order. Visible 2px focus ring, never removed. "Skip to content" as the first focusable element. Sheet/menu traps focus and restores it. Anchor navigation moves focus to the chapter heading (`tabindex="-1"`).
4. **Reduced motion.** Full support per §12.5, including disabled smooth scroll and scrubbed motion.
5. **Zoom.** Usable at 200% zoom and 24px root font. No fixed-height text containers.
6. **Text alternatives.** No text inside SVG paths; diagram content duplicated in adjacent prose. Resume link states the file type.
7. **Never colour alone.** The active chapter is marked by numeral weight/size, not only an accent dot.
8. **Motion safety.** No flashing, no autoplay, no looping animation longer than 5s.
9. **Language.** `<html lang="en">`.
10. **Touch.** 44×44px minimum, 8px between adjacent targets.

---

## 15. Performance Requirements

| Metric | Target | Method |
|---|---|---|
| LCP | <2.0s mobile 4G | First viewport is CSS + SVG only; no image in the LCP path |
| CLS | 0.00 | All layers sized in CSS; fonts with matched fallback metrics |
| INP | <150ms | No heavy JS on interaction |
| JS (gzip) | <190 kB | Current stack ≈178 kB gzip; measure before cutting framer-motion |
| CSS (gzip) | <12 kB | Tailwind 4 + tokens |
| Requests | ≤12 | JS bundle, CSS, 2–3 fonts |
| Landscape assets | 0 raster | Inline SVG |
| Third-party scripts | 0 | No analytics unless requested |
| Lighthouse | Perf ≥85 mobile / ≥95 desktop; A11y 100 | Run on built `dist/` |

Implementation rules:

- Fonts: `preconnect`; `display=swap`; preload only Inter 400 and Fraunces display; `size-adjust` on fallbacks to prevent CLS.
- Do not lazy-load diagrams — they are small inline SVG. Instead **defer scroll-trigger setup** until after LCP (`requestIdleCallback` or `load`).
- Any raster image: `srcset` at 480/960/1440, AVIF then WebP, explicit `width`/`height`, `loading="lazy"`, `decoding="async"`.
- No layout-affecting JS at load. The page must render completely before JS executes.
- QA: Lighthouse mobile + desktop, width sweep, console check, reduced-motion pass.

---

## 16. Content and Asset Requirements

### 16.1 Content to be written or replaced

| Asset | Status | Owner |
|---|---|---|
| Name, role, location, education, GPA | Provided `VERIFIED` | — |
| Intro paragraph, tagline | `NEEDS USER INPUT` (draft §5.1) | Owner review |
| Email, GitHub, LinkedIn URLs | `NEEDS USER INPUT` | Owner |
| Resume PDF | `NEEDS USER INPUT` | Owner |
| Experience entries (internship, BAPAS) | `NEEDS USER INPUT` | Owner |
| Philosophy + career direction | `NEEDS USER INPUT` (draft §5.2) | Owner review |
| Four project case studies | Partly `VERIFIED`; gaps per §6 | Owner |
| Dev tools / testing skill lists | `NEEDS USER INPUT` | Owner |
| Gawe + AgroLedger stacks | `NEEDS USER INPUT` | Owner |

### 16.2 Asset production list

| Asset | Format | Notes |
|---|---|---|
| Six chapter ridge sets (desktop + mobile) | Inline SVG | 12 paths; 6–12 control points each |
| Six sky gradients | CSS | Token pairs per §8.2 |
| Star field (Ch. 05) | CSS radial-gradient tile | ≤2 kB, static |
| Four project diagrams | Inline SVG | Per §7.6 |
| Portrait (optional) | AVIF/WebP, 3 sizes | `NEEDS USER INPUT` |
| Favicon | SVG + ICO | Monogram or horizon mark |
| OG image | 1200×630 PNG | Landscape + name |

**No new raster photography is required.** Deliberate: keeps the site fast, keeps it original, removes any art commission from the critical path.

### 16.3 Data shape (`front/src/data/`) — `PROPOSED`

Retains the "single JSON source of truth" rule from `AGENT.md`.

```jsonc
// profile.json
{
  "name": "Sakbanullah Dwi Oktavian",
  "role": "Junior Full-Stack Developer",
  "focus": "Backend",
  "location": "Indonesia",
  "email": "",
  "education": { "school": "Bina Darma University", "program": "Informatics Engineering", "years": "2021–2025", "gpa": "3.72/4.00" },
  "intro": "",
  "socials": [{ "label": "GitHub", "href": "" }, { "label": "LinkedIn", "href": "" }],
  "resume": { "href": "", "label": "Resume (PDF)" }
}
```

```jsonc
// projects.json — per project
{
  "slug": "raccoon-coffee",
  "name": "Raccoon Coffee",
  "role": "",
  "period": "",
  "evidence": "48 API endpoints · 8-model schema",
  "overview": "",
  "problem": "",
  "why": "",
  "contribution": [],
  "teamScope": [],                       // BAPAS only
  "decisions": [{ "choice": "", "reason": "" }],
  "highlights": [],
  "challenges": [{ "challenge": "", "solution": "" }],
  "results": [],
  "stack": [],
  "links": { "repo": "", "demo": "" },
  "visual": "diagram"                    // "diagram" | "landscape"
}
```

Removed: `size`, `size.col`, `size.row`, `featured`, and the bento grid — Chapter 03 is no longer a grid.

---

## 17. Figma Page and Frame Organization

*(Specification for the next phase. Nothing is created yet.)*

**File:** `Portfolio — The Long Horizon` `PROPOSED`
**Pages:**

| # | Page | Contents |
|---|---|---|
| 00 | `Cover` | Title, version, palette swatches, type specimen |
| 01 | `Foundations` | Colour tokens, type scale, spacing, grid, motion tokens |
| 02 | `Landscape` | Six environment studies + layer stack, desktop & mobile |
| 03 | `Chapters — Desktop` | Six frames at 1440×900, plus scroll-extended frames |
| 04 | `Chapters — Mobile` | Six frames at 390×844 |
| 05 | `Chapters — Tablet` | Six frames at 834×1112 |
| 06 | `Projects` | Four movements, desktop + mobile, plus four detail sheets |
| 07 | `Components` | Buttons, links, rail, chapter sheet, statements, diagrams |
| 08 | `Prototype` | Scroll-flow prototype + reduced-motion variant |
| 09 | `Archive (do not build)` | Previous explorations moved here — **not deleted** |

**Naming:** `CH01 / Arrival / Desktop 1440`, `CH03 / Expeditions / Raccoon / Desktop`, `CMP / Button / Primary`.

**Frame sizes:** 1440×900, 390×844, 834×1112; plus 1440×900 reduced-motion variants for chapters 01, 03, 05.

---

## 18. Prototype Interaction Map

| From | Action | To | Motion |
|---|---|---|---|
| Load | automatic | CH01 complete | Load sequence §12.3 |
| CH01 "Explore Projects" | click | `#expeditions` | Smooth scroll 900ms, lands 8px below rail |
| CH01 "Contact Me" | click | `#horizon` | Smooth scroll 600ms (long jump) |
| Any chapter | scroll | next chapter | Colour interpolation + parallax |
| CH03 project | "Case Study" | Project sheet | 320ms upward |
| Project sheet | Esc / backdrop / close | back to movement | 220ms, focus restored |
| Rail tick | click | chapter start | Smooth scroll |
| Rail tick | hover/focus | numeral + name expand | 160ms |
| Mobile index | tap | Chapter sheet | 280ms full-screen |
| Chapter sheet row | tap | navigate + close | 280ms out |
| CH06 email | click | `mailto:` | none |
| CH06 resume | click | new tab | none |

**Deliverable:** one continuous scroll prototype, desktop, wired at exactly these points, plus a motion-disabled variant.

---

## 19. Design Quality Checklist

Each item must pass before handoff to implementation.

**Composition**
- [ ] First viewport readable and identifiable with JavaScript disabled.
- [ ] No chapter shares a horizon height with the one before it.
- [ ] Every chapter has ≥35% of vertical space carrying no text.
- [ ] No element is a box inside a box.
- [ ] Nothing rounded beyond 4px except the 2px button radius.

**Colour**
- [ ] Every text/background pair measured ≥4.5:1 (≥3:1 for ≥24px).
- [ ] Contrast holds at every scroll position, not just chapter endpoints.
- [ ] One accent per chapter; no decorative gradients.
- [ ] No raw hex in component specs — tokens only.

**Typography**
- [ ] Body measure ≤62ch everywhere.
- [ ] No text below 14px.
- [ ] Only three families; only tokens from §9.2.
- [ ] Display headings balance to 2 lines desktop, ≤3 mobile.

**Content**
- [ ] Zero invented metrics, employers, or URLs.
- [ ] Every `NEEDS USER INPUT` resolved or the element removed.
- [ ] BAPAS contribution clearly separated from team scope.
- [ ] Every claim traceable to a verified feature.

**Motion**
- [ ] Reduced-motion variant fully designed and reviewed.
- [ ] No element animated by two libraries.
- [ ] No scroll pinning.
- [ ] All durations within §12.3.

**Responsive**
- [ ] 320px has no horizontal scroll and no clipped text.
- [ ] Mobile landscape uses its own SVG paths, not letterboxed desktop art.
- [ ] Tap targets ≥44×44px.

**Accessibility**
- [ ] Tab order maps to visual order.
- [ ] Focus visible on every interactive element.
- [ ] Sheets trap and restore focus.
- [ ] Decorative art is `aria-hidden`.

**Performance**
- [ ] No raster in the LCP path.
- [ ] Inline SVG total <24 kB uncompressed.
- [ ] JS budget respected and measured.

---

## 20. Open Questions and Decisions Requiring Approval

### 20.1 Decisions taken in this spec

| # | Decision | Rationale | Default if rejected |
|---|---|---|---|
| D1 | No manual theme toggle; scroll drives colour | Preserves the single-journey metaphor | Add a toggle overriding chapter palettes — doubles QA, weakens concept |
| D2 | No top nav bar; chapter rail only | Editorial restraint | Sticky minimal header with name + 3 links |
| D3 | Landscape as inline SVG/CSS, no WebGL | Performance, originality, zero asset cost | WebGL shader (rejected on mobile perf) |
| D4 | No cards; Chapter 03 is a sequence, not a grid | Breaks template smell | Grid reintroduces dashboard aesthetics |
| D5 | Fraunces + Inter + JetBrains Mono | Expressive serif, neutral sans, engineering mono | Instrument Serif + Inter; or Newsreader + Public Sans |
| D6 | Remove Card/Stamp/Divider/kanji ornaments/theme toggle | Belong to the superseded theme | Keep as dead code |
| D7 | Body ink `#46586A`, accent `#8C5A2B` for AA | Measured contrast | Keep literal palette and accept AA failures |
| D8 | Project visuals are diagrams, not screenshots | Screenshots date badly and add weight | Real screenshots (owner supplies + optimises) |
| D9 | Mobile gets separate ridge art | Composition quality | Reuse desktop art (worse) |
| D10 | Order: Raccoon → Gawe → BAPAS → AgroLedger | Strongest first | Any other order |
| D11 | Site language English | Recruiter audience is international | Indonesian (narrows reach) |

### 20.2 Information still needed from the owner

| # | Question | Blocks |
|---|---|---|
| Q1 | Intro paragraph — approve draft or supply your own? | CH01 copy |
| Q2 | Email address? | CH06, mailto |
| Q3 | GitHub URL? | CH06, all project links |
| Q4 | LinkedIn URL? | CH06 |
| Q5 | Resume PDF exists? | CH06 |
| Q6 | Internship: organisation, role, dates, responsibilities, stack? | CH02 |
| Q7 | BAPAS: your role title, dates, stack, team scope? | CH02, CH03 |
| Q8 | Gawe and AgroLedger stacks? | CH03, CH04 |
| Q9 | Dev tools and testing/quality tools actually used? | CH04 |
| Q10 | Raccoon Coffee: solo or team? Real motivation? Real challenges solved? | CH03 |
| Q11 | Raccoon Coffee live URL? | CH03 |
| Q12 | BAPAS repository public or private? | CH03 |
| Q13 | AgroLedger: solo/team, stack, real scope? | CH03 |
| Q14 | Portrait photo available, and do you want it on the site? | CH02 |
| Q15 | English confirmed? | All copy |
| Q16 | Domain / deployment target? | Assets, OG image |

### 20.3 Previous explorations — archive candidates (documented only, nothing moved)

| File | Verdict |
|---|---|
| `design/portfolio-design-exploration-2026.figcraft` | Archive — superseded taste |
| `design/portfolio-paper-vermilion-2026.figcraft` | Archive — ink/vermilion direction, superseded |
| `design/portfolio-a3-paper-vermilion-2026.figcraft` | Archive — variant of the same direction |

The shipped "Scroll-Style Report" implementation in `front/` is conceptually superseded but is live code: it should be **replaced in place** during implementation, not deleted up front.

---

## 21. Recommended Next Steps

1. **Owner answers §20.2 (Q1–Q16).** Everything else is blocked on content truthfulness.
2. **Owner approves or rejects D1–D11.** Written replies suffice; no design work needed.
3. **Visual companion pass** — three small landscape studies (CH01 desktop, CH01 mobile, CH03 desert) rendered quickly in a browser tab for direction gut-check before Figma. Cheap; catches errors early.
4. **Figma foundations page** — tokens, type specimen, grid.
5. **Figma chapters** — six desktop frames, then mobile.
6. **Prototype + reduced-motion variant.**
7. **Implementation plan** — written plan, then rebuild `front/` against this spec: new data schema, new components, removal of the superseded theme.
8. **QA** — contrast sweep at multiple scroll positions, width sweep 320–2560, Lighthouse, reduced-motion pass, keyboard pass.

**Do not start step 3 or later without the owner's instruction.**

---

## Appendix A — Fact ledger

Everything the design is allowed to assert, and its provenance.

| Claim | Status |
|---|---|
| Name: Sakbanullah Dwi Oktavian | `VERIFIED` (owner brief) |
| Junior Full-Stack Developer, Backend Focus | `VERIFIED` |
| Location: Indonesia | `VERIFIED` |
| Informatics Engineering, Bina Darma University, 2021–2025 | `VERIFIED` |
| GPA 3.72/4.00 | `VERIFIED` |
| Raccoon Coffee stack (Next.js, React, TS, NestJS, Prisma, MySQL) | `VERIFIED` |
| Raccoon Coffee: 48 API endpoints, 8-model schema | `VERIFIED` |
| Raccoon Coffee security set (HttpOnly JWT, CSRF, bcrypt, throttling, revocation, upload validation) | `VERIFIED` |
| Raccoon Coffee: admin CMS, menu/category, content/image management, moderated anonymous wall | `VERIFIED` |
| Gawe: seven implemented areas (§6.2) | `VERIFIED` |
| BAPAS OKU Connect: RBAC + refresh-token auth contributed | `VERIFIED` |
| BAPAS OKU Connect: team-built, internal | `VERIFIED` |
| AgroLedger: agricultural finance for palm oil and rubber | `VERIFIED` |
| Any user count, accuracy %, time saving, cost saving, financial impact | **FORBIDDEN — not supplied** |
| Any GitHub/demo/email/LinkedIn URL | **FORBIDDEN — not supplied** |
| Employment history, internship details, dates beyond education | **NOT SUPPLIED** |
