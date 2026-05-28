---
name: vectorguest-brand-doc
description: >-
  Andre's VectorGuest / TSS / Harold OS knowledge-base house style. Use
  whenever he asks for a new VectorGuest, Vector Guest, TSS, or Harold OS
  document — strategy memo, architecture doc, integrations map, payment
  stack writeup, build plan, operating model, market & competition, vision
  doc, README, role spec, anything for the Vector Guest knowledge base or
  Drive. Also trigger on "in my usual format", "like the integrations map",
  "match the brand", "knowledge base style", or references to existing docs
  by name (01_Product_Overview, 03_Market_and_Competition,
  05_Integrations_Map, 04_Long_Term_Vision, 01_Payment_Stack). Captures the
  anatomy, heading hierarchy, inline-bold sub-section labels, callout-box
  convention, table-as-grouping-device pattern, prose voice, reasoning flow,
  and Arial / TSS-red formatting that make every doc indistinguishable from
  05_Integrations_Map. Pair with the docx skill for .docx output.
---

# VectorGuest knowledge-base brand & format

The Vector Guest / TSS / Harold OS knowledge base is a single visual and rhetorical system. Every doc in the canon (`00_README_Drive_Navigation`, `01_Product_Overview`, `03_Market_and_Competition`, `04_Long_Term_Vision`, `05_Integrations_Map`, `01_Payment_Stack`, etc.) follows the same anatomy, heading patterns, callout conventions, and prose voice. New documents must be indistinguishable from `05_Integrations_Map` in structure, formatting, and reasoning flow.

The canonical example to mimic is **`05_Integrations_Map`** in Andre's Drive (file id `16FSTT0bRNUB6k_8gjTCm3q4MI-S82TpD9FubxWBpVkw`). When in doubt, open it and copy the pattern.

## Order of work

1. **Research first.** Pull whatever context the doc needs — search the VectorGuest Obsidian vault via the `vectorguest-vault` skill, read the relevant Drive files via the Google Drive MCP tools, fetch anything external. Do not start drafting until the substance is in hand.
2. **Outline against the reasoning flow in §7.** Map every section of the new doc onto the canonical opening → landscape → critical few → important rest → discipline → reference → status → summary skeleton. Drop steps that don't apply, never reorder them.
3. **Draft in markdown** using the heading hierarchy in §2 and the inline-bold label vocabulary in §3.
4. **Lean on the `docx` skill** for the actual `.docx` build. Use `docx-js` (`new Document({...})`) — it gives full control over fonts, colours, table borders, and the callout-box layout described in §5. Do not try to author the brand via Markdown→Pandoc; the callout boxes and code blocks won't round-trip.
5. **Verify** against the brand-spec checklist in §10 before declaring done.

## 1. Document anatomy — strict opening sequence

Top-to-bottom, every document opens with:

1. **Title** in the Title style — Arial bold, 20pt, black, left-aligned. Just the document name (e.g. `Integrations Map`). **No breadcrumb line above it.**
2. **Title repeated as a normal bold paragraph** — same text, bold 20pt, immediately under the Title-styled line. This duplication is intentional house style (it survives the Google Docs export and is what every doc in the canon looks like).
3. **One-line italic subtitle** — italic Arial 11pt, color `#555555`. Terse, declarative, often metaphorical. Examples to study:
   - *"Every external system Harold OS talks to, what data flows, and which agent owns each connection. The plumbing of the platform."*
   - *"Two rails — Stripe for cards, Ponto for SEPA. How each works, when each is used, and where they meet."*
   - *"What Harold OS is, how it is structured, and how its pieces fit together."*

   Pattern: short framing clause + em-dash + payoff clause, OR a one-sentence metaphor.
4. **Opening callout box** (single-cell table — see §5) with one of these banner headings:
   - `SCOPE OF THIS DOCUMENT` (for technical / reference docs)
   - `HOW TO USE THIS SECTION` (for section-opener docs)
   - `READ THIS FIRST` (for navigation / overview docs)
   - `HOW WE APPROACH THIS` (for opinionated docs — market, competition, vision)
   - `HOW TO READ THIS` (for long-horizon / vision docs)
   - `V<n> CHANGES FROM V<n-1>` (for versioned revisions)

   Body of the callout: 1–3 sentences naming the scope and pointing to the canonical deeper source (`for exhaustive detail — payloads, endpoints, OAuth flows — see the canonical tss-integrations.md in the source-of-truth set`).
5. **First H1** — almost always a framing question or thematic claim. Patterns: `"Why X is a first-class concern"`, `"What X is"`, `"The market shape"`, `"The end state we are building toward"`.

## 2. Heading hierarchy

- **H1** — major sections. Naming patterns: `"Why X is a first-class concern"`, `"The N <thing>s"` (e.g. `"The six integration categories"`, `"The four layers"`), `"The critical X"`, `"How each X works"`, `"Data model"`, `"Operational discipline"`, `"Summary reference"`, `"What's built vs what's planned"`, `"Summary"`. Compound docs may also use top-level numbered openers as H1: `"01 Payment Stack"`, `"02 Communications"`.
- **H2** — individual entities being detailed in depth. Naming pattern is **always** `"<Name> — <one-line role>"` with an em-dash, not a colon, not a hyphen. Examples: `"Channex — the channel manager"`, `"Stripe — card payments"`, `"Card payments — Stripe"`, `"Jurny — the SaaS-for-operators cautionary tale"`, `"Phase 1 — Setup"`.
- **H3** — sub-aspects within an H2 or asides. Examples: `"Pay-in skeleton"`, `"Failure matrix"`, `"OTAs (Booking.com, Expedia, Airbnb)"`, `"What they do well"`.
- **H4** — used sparingly; italic blue Arial 11pt (`#2e74b5`). Only when an H3 needs a finer split.

## 3. Inline-bold sub-section labels (the canonical vocabulary)

Inside an H2 entity-detail block, the doc **never bullets**. It uses fixed bold inline labels followed by a colon, then a prose paragraph. Each label opens its own paragraph. Reuse this vocabulary verbatim wherever it fits:

- `**Owning agent:**` (who's accountable inside Harold OS)
- `**What it does:**` (one-paragraph functional description)
- `**What flows:**` (data in / data out)
- `**Why it matters:**` (what breaks if it fails)
- `**Why we chose it:**` / `**Why this rail:**` (decision rationale, including what was rejected)
- `**Contract:**` (the API/integration contract shape)
- `**Webhook truth:**` / `**Settlement:**` / `**Refunds:**` / `**Fees:**` (operational specifics)
- `**Failure:**` / `**Cancellation:**` / `**Chasing:**` / `**Reversal:**`
- `**Decision point:**` / `**Detection latency:**`
- `**Honesty about current state:**` (for unfinished work)

The order inside an entity H2 is also fixed: Owning agent → What it does → What flows → Why it matters → Why we chose it → operational specifics. Drop labels that don't apply; do not reorder.

## 4. Tables — the dominant grouping device

Categorical content is **always a table**, never a bullet list. Examples:

- `Category | Purpose | Examples` (the N-category landscape pattern — used in every major doc)
- `Group | What they sell | Relationship to Vector Guest`
- `Folder | What's in it | Read when`
- `Integration | Primary agent | Criticality | What fails if it breaks` (summary references)
- `Code | Cause | Response` (failure matrices)
- `Field | Table` (data-model field lists)

Format rules (from the canonical styles.xml):

- Full-width (9360 dxa / about 6.5 inches).
- 0.5pt black outer border + 0.5pt inside borders.
- Header row: shading `#f0f0f0`, light grey 0.5pt cell borders, **bold 10pt** text.
- Cell padding 100/140/100/140 dxa.
- Default alignment **left** (Andre's docs show `:-:` in markdown round-trips but the live XML is `<w:jc w:val="left"/>` — render left in the .docx).
- The header row's first column is usually `Category` / `Group` / `Field` / `Integration` — the discriminator comes first.

## 5. Callout / sidebar boxes

Callouts are implemented as a **single-cell table** (one row, one cell), full-width:

- Cell shading `#fafafa`.
- **Top border 0.75pt `#c0303a`** (TSS red). This red top stripe is the single most recognisable brand cue in the canon.
- Side and bottom borders 0.5pt `#e5e5e5`.
- Cell padding 160/200/160/200 dxa.
- First paragraph: **ALL-CAPS banner heading** — bold, 8pt, color `#c0303a`, left-aligned, 80 twip spacing after.
- Second paragraph onwards: body prose at default 11pt black.

Canonical banner phrases (use verbatim where they fit; coin new ones in the same register — 2–6 words, ALL CAPS, imperative or declarative invariant):

- Scope/framing: `SCOPE OF THIS DOCUMENT`, `HOW TO USE THIS SECTION`, `READ THIS FIRST`, `HOW WE APPROACH THIS`, `HOW TO READ THIS`, `V2 CHANGES FROM V1`
- Hard invariants: `WEBHOOK IS CANONICAL`, `SAME RAIL IN, SAME RAIL OUT`, `NEVER STORE RAW CARD DATA`, `ONE UNIT, ONE ADAPTER`
- Why-this-matters asides: `WHY THIS LAYER IS WORTH NAMING EXPLICITLY`, `WHY THIS MATTERS FOR VECTOR GUEST`, `WHAT WE ARE BUILDING`
- Philosophy: `DESIGN FOR FAILURE`
- Open work: `TODO — VERIFY PARTIAL-CAPTURE FLOW AGAINST STRIPE API`

Use one callout right after the title block, and 0–3 more sprinkled through the doc — typically one after a counter-intuitive trade-off, one stating a hard invariant, one at the section that introduces a structural bet.

## 6. Prose voice

- **Cadence**: medium sentences (~22 words on average), built around em-dashes. The canon uses ~190 em-dashes per ~17K words. Em-dashes insert precise qualifiers mid-sentence — never decorative, never as a substitute for a comma.
- **Paragraphs**: 2–4 sentences. Single-sentence paragraphs are common right after a section opener or a bold label.
- **Voice**: direct, declarative, **zero hedging**. No "might", "could", "perhaps", "seems". Where uncertainty is real, name it explicitly with `**Honesty about current state:**` or a `TODO —` callout, not weasel words.
- **British spelling**: behaviour, recognised, organisation, optimise.
- **Canonical recurring phrases**: "first-class concern", "system of record", "deliberate choice", "the canonical X", "for exhaustive detail, see…", "the canonical event", "hard invariant", "rail-agnostic", "source of truth", "graceful degradation", "the trigger to revisit is X, not Y", "deferred deliberately".
- **Trade-off / honesty markers** (use these constructions when discussing decisions): "we deferred it deliberately. The trigger to revisit is product-driven, not financial:"; "this is a deliberate regulatory architecture choice, not just a fee choice"; "structurally a better fit for the long term — we defer it deliberately".
- **Metaphor in subtitles and section openers** — judicious, never overused: "the plumbing of the platform", "the disciplined core", "the reasoning substrate", "the integration layer is where systems silently break".

Three calibration paragraphs (study these before drafting):

> Harold OS is the system of record for operators. That means it does not integrate with the operator's PMS — it replaces it. But Harold OS does integrate with a specific set of external systems, the ones that are genuinely infrastructure the operation depends on: channel managers, payment rails, lock systems, market data providers, messaging platforms. Every integration is a deliberate choice about which functions TSS will never build and which it must call.

> **Why this rail:** Stripe Connect is right for the stage Harold OS is in, not right forever. The v1 binding constraints are integration speed, developer ergonomics, operator self-onboarding, and regulatory perimeter — Stripe wins on all four. Standard accounts bring an operator online in minutes with KYC handled by Stripe, and the operator is the regulated entity holding the funds. TSS therefore operates outside the regulated payments perimeter and avoids registering as a Payment Institution with the NBB. **This is a deliberate regulatory architecture choice, not just a fee choice.**

> A wallet-based EMI such as Mangopay is structurally a better fit for the long-term shape of this business — multi-party allocation, wallet-based escrow under Mangopay's own EMI licence, native deposit holds without expiry constraints. We defer it deliberately. The trigger to revisit is product-driven, not financial: the moment the roadmap commits to platform-held funds (escrow, guarantee, deposit pooling), Mangopay or equivalent becomes mandatory because the alternative is a TSS PI licence.

## 7. Reasoning flow (the canonical section order)

For each major section (H1), follow this rhetorical pattern:

1. **Why this matters** — one paragraph opening the section, framing the concern in business/architectural terms.
2. **The landscape** — a categorisation table (the N-categories pattern) listing every item in scope.
3. **The critical few** — H2 per item, each using the fixed bold-label vocabulary from §3.
4. **The important rest** — H3 per item, paragraph-length, lighter treatment.
5. **Supporting / nice-to-have** — bullet list, one-line per item (the only place bullets are welcome).
6. **What looks like it but isn't** — explicit "Internal capabilities that look like X but aren't" subsection to forestall confusion.
7. **Operational discipline** — health monitoring, graceful degradation, retry/idempotency. One H1.
8. **Callout with the hard invariant** (`DESIGN FOR FAILURE`, `WEBHOOK IS CANONICAL`, etc.) immediately after the discipline section.
9. **Summary reference table** — every item, with criticality and failure mode in one row each.
10. **What's built vs what's planned** — bullet list, honest status.
11. **Summary** — one paragraph, naming the categories, the critical items, and the discipline.

Drop steps that don't apply. Never reorder.

## 8. Formatting specifics (from the canonical styles.xml + theme1.xml)

| Element | Font | Size | Colour | Other |
|---------|------|------|--------|-------|
| Body | Arial | 11pt | `#000000` | Line spacing 1.15 |
| Title | Arial bold | 20pt | `#000000` | 120 twip after |
| Subtitle | Arial italic | 11pt | `#555555` | 240 twip after |
| H1 | Arial bold | 15pt | `#000000` | 360 before / 180 after |
| H2 | Arial bold | 13pt | `#000000` | 280 before / 140 after |
| H3 | Arial bold | 11.5pt | `#000000` | 220 before / 100 after |
| H4 | Arial italic | 11pt | `#2e74b5` | sparingly |
| Callout banner | Arial bold | 8pt | `#c0303a` | ALL CAPS |
| Inline code | Roboto Mono | 11pt | `#188038` | identifiers, field names |
| Code block | Roboto Mono | 9pt | `#000000` | inside a `#f4f4f4` single-cell table |

- **Accent colour**: `#c0303a` (TSS red). Only used on callout top borders and ALL-CAPS banner headings. Everything else in the doc is monochrome by design.
- **Page**: US Letter (12240 × 15840 twips). Margins **1.0 inch on all four sides** (1440 twip). Header 720 / footer 720.
- **Theme major/minor fonts** (Calibri/Cambria) are declared but **overridden everywhere by Arial in actual runs**. Do not let docx-js fall back to Calibri.

## 9. Monospace / code

The canon switches to monospace in two situations, both via **Roboto Mono** (never Courier/Consolas):

1. **Inline code identifiers** — field names, API parameters, account names. Roboto Mono, 11pt, color `#188038`. Examples: `amount`, `application_fee_amount`, `charge.succeeded`, `pending_card_holds`.
2. **Code blocks** — implemented as a **single-cell full-width table** with shading `#f4f4f4`, 0.75pt `#e5e5e5` border, cell padding 160/200/160/200 dxa. Code at 9pt Roboto Mono, one paragraph per line, tabs preserved for indentation. There is no fenced ``` markdown — every code block lives inside its own light-grey table cell.

## 10. Pre-flight checklist (run before declaring done)

- Title appears twice at the top (Title style + bold paragraph), no breadcrumb above.
- Italic grey subtitle in the canonical short-clause-plus-payoff register.
- Opening callout with an ALL-CAPS red banner heading.
- Every H2 follows `Name — role` with an em-dash.
- Inside each entity H2, the bold-label vocabulary appears in canonical order.
- At least one categorisation table with `#f0f0f0` header row, bold 10pt header text, left-aligned cells.
- At least one hard-invariant callout (red top border, ALL-CAPS banner).
- Arial everywhere; Roboto Mono only on identifiers and code blocks.
- British spelling throughout.
- Zero hedging language (`might`, `could`, `perhaps`, `seems`) outside explicit `Honesty about current state:` or `TODO —` markers.
- Em-dashes used as precision punctuation, not as comma substitutes.
- Section order follows §7: why-it-matters → landscape table → critical few (H2) → important rest (H3) → supporting (bullets) → discipline → invariant callout → summary reference → status → one-paragraph summary.
- Closing summary paragraph names the categories, the critical items, and the discipline in one sweep.

## Files in this skill

- `reference/integrations_map_anatomy.md` — annotated walk-through of `05_Integrations_Map`, mapping every section onto the §7 reasoning flow. Read this when the abstract spec isn't enough and you need a concrete worked example.

## When to use the docx skill alongside

If the deliverable is a `.docx` file, hand the formatting work to the `docx` skill (`docx-js` route) once the content is drafted. Pass the §8 style table verbatim into the docx-js style configuration. Callouts and code blocks need explicit `Table` constructions — Markdown blockquotes and fenced code won't reproduce the brand.
