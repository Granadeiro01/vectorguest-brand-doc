---
name: vectorguest-brand-doc
description: >-
  Andre's Vector Guest / TSS / Harold OS knowledge-base house style — refactored
  onto the Vector Guest brand system. Use whenever he asks for a new Vector
  Guest, VectorGuest, TSS, or Harold OS document — strategy memo, architecture
  doc, integrations map, payment stack writeup, build plan, operating model,
  market & competition, vision doc, README, role spec, anything for the Vector
  Guest knowledge base or Drive. Also trigger on "in my usual format", "like
  the integrations map", "match the brand", "knowledge base style", or
  references to 01_Product_Overview, 03_Market_and_Competition,
  05_Integrations_Map, 04_Long_Term_Vision, 01_Payment_Stack. Inherits Space
  Grotesk / Space Mono typography and the Linen / Paper / Ink / Ash / spectral
  palette from the vector-guest-brand skill; preserves Andre's monochrome +
  TSS-red diagram language unchanged (his version is the canon for diagrams).
  Pair with the docx skill for .docx output and with vector-guest-brand for
  shared assets (fonts, logo SVGs, token sheet).
---

# Vector Guest knowledge-base document style

A single visual and rhetorical system for every long-form Vector Guest doc — `00_README_Drive_Navigation`, `01_Product_Overview`, `03_Market_and_Competition`, `04_Long_Term_Vision`, `05_Integrations_Map`, `01_Payment_Stack`, and every doc that follows.

**This skill defines the document layer.** Everything visual — colours, type, spacing, hairlines, callouts, logo placement — inherits from the `vector-guest-brand` skill. This skill governs **document anatomy, heading hierarchy, recurring sub-section labels, table conventions, callout discipline, prose voice, reasoning flow, and diagram rendering** — the things that make a knowledge-base doc a knowledge-base doc, not a deck or a one-pager.

When a rule here conflicts with vector-guest-brand, vector-guest-brand wins on aesthetics, this skill wins on document structure.

## Order of work

1. **Research first.** Pull context from the Vector Guest Obsidian vault via the `vectorguest-vault` skill, read sibling Drive files, fetch anything external. Do not start drafting until the substance is in hand.
2. **Outline against the reasoning flow in §7.** Map every section of the new doc onto the canonical opening → landscape → critical few → important rest → discipline → reference → status → summary skeleton. Drop steps that don't apply, never reorder them.
3. **Draft in markdown** using the heading hierarchy in §2 and the inline-bold label vocabulary in §3.
4. **Apply the brand.** Load the `vector-guest-brand` skill alongside this one — link `assets/colors_and_type.css` for HTML output, or use Space Grotesk / Space Mono with the token values in §8 for docx. The Linen/Paper/Ink/Ash palette and the spectral gradient as "one luminous moment per view" come from there.
5. **Lean on the `docx` skill** for the actual `.docx` build (`docx-js` route). Markdown→Pandoc will not round-trip callouts, code blocks, or the brand's typography correctly.
6. **Verify** against the pre-flight checklist in §11 before declaring done.

## 1. Document anatomy — strict opening sequence

Top-to-bottom, every document opens with:

1. **Mono kicker line** — Space Mono uppercase, 11px, Ash `#8A8792`, tracking `0.16em`. Format: `VECTOR GUEST · KNOWLEDGE BASE` or section-specific like `VECTOR GUEST · KNOWLEDGE BASE · INTEGRATIONS`. This is the canonical Vector Guest signature element (the `.vg-label`); it sits where a breadcrumb would, but it is *not* navigation — it is positioning.
2. **Title** — Space Grotesk 700, display-size (32–48pt depending on doc weight), Ink `#18171A`, tracking `-0.05em`, line-height `0.9`. Just the document name (e.g. `Integrations Map`).
3. **Subtitle** — one line, Space Grotesk italic, 18–20pt (lead-size), Ash `#8A8792`, tracking `-0.03em`. Terse, declarative, often metaphorical. Examples to study:
   - *"Every external system Harold OS talks to, what data flows, and which agent owns each connection. The plumbing of the platform."*
   - *"Two rails — Stripe for cards, Ponto for SEPA. How each works, when each is used, and where they meet."*
   - *"What Harold OS is, how it is structured, and how its pieces fit together."*

   Pattern: short framing clause + em-dash + payoff clause, OR a one-sentence metaphor.
4. **Opening callout** (§5) with one of these mono-uppercase banner phrases:
   - `SCOPE OF THIS DOCUMENT` (technical / reference docs)
   - `HOW TO USE THIS SECTION` (section-opener docs)
   - `READ THIS FIRST` (navigation / overview docs)
   - `HOW WE APPROACH THIS` (opinionated docs — market, competition, vision)
   - `HOW TO READ THIS` (long-horizon / vision docs)
   - `V<n> CHANGES FROM V<n−1>` (versioned revisions)

   Body of the callout: 1–3 sentences naming the scope and pointing to the canonical deeper source (e.g. `for exhaustive detail — payloads, endpoints, OAuth flows — see the canonical tss-integrations.md in the source-of-truth set`).
5. **First H1** — almost always a framing question or thematic claim: `"Why X is a first-class concern"`, `"What X is"`, `"The market shape"`, `"The end state we are building toward"`.

The double-printed title from the old TSS template is gone. That was a Google-Docs export artefact. The Vector Guest brand is sharp infra-grade — title appears once, set at display size, with the mono kicker doing the orienting work.

## 2. Heading hierarchy

- **H1** — major sections. Space Grotesk 600, 28–32pt, Ink, tracking `-0.05em`. Naming patterns: `"Why X is a first-class concern"`, `"The N <thing>s"` (e.g. `"The six integration categories"`), `"The critical X"`, `"How each X works"`, `"Operational discipline"`, `"Summary reference"`, `"What's built vs what's planned"`, `"Summary"`.
- **H2** — individual entities. Space Grotesk 600, 20–22pt, Ink, tracking `-0.03em`. Naming pattern is **always** `"<Name> — <one-line role>"` with an em-dash. Examples: `"Channex — the channel manager"`, `"Stripe — card payments"`, `"Jurny — the SaaS-for-operators cautionary tale"`, `"Phase 1 — Setup"`.
- **H3** — sub-aspects. Space Grotesk 600, 16pt, Ink. Examples: `"Pay-in skeleton"`, `"Failure matrix"`, `"What they do well"`.
- **H4** — sparingly. Space Grotesk italic, 14pt, Ash `#8A8792`.

Headings always sit above a `.vg-hairline` (0.5pt Rule `#C8C4BC`) when a section needs visual separation. No background bands, no coloured pills.

## 3. Inline-bold sub-section labels (the canonical vocabulary)

Inside an H2 entity-detail block, the doc **never bullets**. It uses fixed inline labels in **Space Grotesk 600** followed by a colon, then a prose paragraph. Each label opens its own paragraph. Reuse this vocabulary verbatim wherever it fits:

- `**Owning agent:**` (who's accountable inside Harold OS)
- `**What it does:**` (one-paragraph functional description)
- `**What flows:**` (data in / data out)
- `**Why it matters:**` (what breaks if it fails)
- `**Why we chose it:**` / `**Why this rail:**` (decision rationale, including what was rejected)
- `**Contract:**` (API/integration contract shape)
- `**Webhook truth:**` / `**Settlement:**` / `**Refunds:**` / `**Fees:**` (operational specifics)
- `**Failure:**` / `**Cancellation:**` / `**Chasing:**` / `**Reversal:**`
- `**Decision point:**` / `**Detection latency:**`
- `**Honesty about current state:**` (for unfinished work)

The order inside an entity H2 is fixed: Owning agent → What it does → What flows → Why it matters → Why we chose it → operational specifics. Drop labels that don't apply; do not reorder.

## 4. Tables — the dominant grouping device

Categorical content is **always a table**, never a bullet list. Examples:

- `Category | Purpose | Examples` (the N-category landscape pattern)
- `Group | What they sell | Relationship to Vector Guest`
- `Folder | What's in it | Read when`
- `Integration | Primary agent | Criticality | What fails if it breaks` (summary references)
- `Code | Cause | Response` (failure matrices)
- `Field | Table` (data-model field lists)

Format rules:

- **Full-width** of the content column.
- **Hairlines only** — 0.5pt Rule `#C8C4BC` between rows and at the top/bottom edge. No vertical separators unless density requires them. No outer thick border.
- **Header row**: Space Mono uppercase, 11px (`--vg-text-meta`), Ash `#8A8792`, tracking `0.16em`. **No fill.** The mono uppercase label is the differentiator — that is the canonical "kicker" treatment from `vector-guest-brand` taste rule 5.
- **Body cells**: Space Grotesk 400, 16px, Ink. Left-aligned.
- **Padding**: 16px vertical / 12px horizontal per cell (`--vg-space-3` / inside `--vg-space-2`).
- The first column is the discriminator (`Category`, `Group`, `Field`, `Integration`).

Tables breathe. No grey shading on header rows, no zebra striping. The mono uppercase header carries the visual weight.

## 5. Callout boxes

Callouts are panels — implemented as a single-cell table (or `<aside>` in HTML) — full content-width:

- **Fill**: Paper `#FAFAF8` (surface, lighter than the Linen ground; the only place colour-vs-ground matters in a body doc).
- **Border**: 0.5pt hairline Rule `#C8C4BC` on all four sides. **No coloured top stripe.** The old TSS red top border is removed — accent moves elsewhere (see "Climax callout" below).
- **Inner padding**: 20–24px (`--vg-space-4`).
- **First line**: Space Mono uppercase banner, 11px, Ink `#18171A`, tracking `0.16em`, 12px space-after.
- **Body**: Space Grotesk 400, 16px, Ink. 1.55 leading.

### Climax callout — the one luminous moment

Every doc earns one and only one "luminous" callout — the place where the hard invariant lives (`DESIGN FOR FAILURE`, `WEBHOOK IS CANONICAL`, etc.). This is where the spectral gradient appears:

- **Top edge**: a 2px gradient hairline drawn with `--vg-spectrum` (`linear-gradient(100deg, #7B5EA7 0%, #4A90D9 55%, #38C9A8 100%)`) — replaces the top hairline only.
- **Banner**: Space Mono uppercase, Ink, same as a regular callout.
- **Body**: same Space Grotesk Ink, 16px.

This is the doc's single allowed instance of the spectral colour — vector-guest-brand taste rule 2 ("one quiet luminous moment per view — at most"). Pick the callout that carries the rhetorical climax of the doc; never use it twice.

### Canonical banner vocabulary

Use verbatim where they fit; coin new ones in the same register — 2–6 words, ALL CAPS, imperative or declarative invariant:

- Scope/framing: `SCOPE OF THIS DOCUMENT`, `HOW TO USE THIS SECTION`, `READ THIS FIRST`, `HOW WE APPROACH THIS`, `HOW TO READ THIS`, `V2 CHANGES FROM V1`
- Hard invariants (climax candidates): `WEBHOOK IS CANONICAL`, `SAME RAIL IN, SAME RAIL OUT`, `NEVER STORE RAW CARD DATA`, `ONE UNIT, ONE ADAPTER`, `DESIGN FOR FAILURE`
- Why-this-matters asides: `WHY THIS LAYER IS WORTH NAMING EXPLICITLY`, `WHY THIS MATTERS FOR VECTOR GUEST`, `WHAT WE ARE BUILDING`
- Open work: `TODO — VERIFY PARTIAL-CAPTURE FLOW AGAINST STRIPE API`

Use one opening callout right after the title block, and 0–3 more sprinkled through the doc — typically one stating a hard invariant (the climax), one after a counter-intuitive trade-off, one at the section that introduces a structural bet.

## 6. Prose voice

This is unchanged across the refactor — the voice is the system. Aesthetics changed; cadence did not.

- **Cadence**: medium sentences (~22 words on average), built around em-dashes. The canon uses ~190 em-dashes per ~17K words. Em-dashes insert precise qualifiers mid-sentence — never decorative, never as a substitute for a comma.
- **Paragraphs**: 2–4 sentences. Single-sentence paragraphs are common right after a section opener or a bold label.
- **Voice**: direct, declarative, **zero hedging**. No "might", "could", "perhaps", "seems". Where uncertainty is real, name it explicitly with `**Honesty about current state:**` or a `TODO —` callout, not weasel words.
- **British spelling**: behaviour, recognised, organisation, optimise.
- **Canonical recurring phrases**: "first-class concern", "system of record", "deliberate choice", "the canonical X", "for exhaustive detail, see…", "hard invariant", "rail-agnostic", "source of truth", "graceful degradation", "the trigger to revisit is X, not Y", "deferred deliberately".
- **Trade-off / honesty markers**: "we deferred it deliberately. The trigger to revisit is product-driven, not financial:"; "this is a deliberate regulatory architecture choice, not just a fee choice"; "structurally a better fit for the long term — we defer it deliberately".
- **Metaphor in subtitles and section openers** — judicious, never overused: "the plumbing of the platform", "the disciplined core", "the reasoning substrate", "the integration layer is where systems silently break".

Three calibration paragraphs:

> Harold OS is the system of record for operators. That means it does not integrate with the operator's PMS — it replaces it. But Harold OS does integrate with a specific set of external systems, the ones that are genuinely infrastructure the operation depends on: channel managers, payment rails, lock systems, market data providers, messaging platforms. Every integration is a deliberate choice about which functions TSS will never build and which it must call.

> **Why this rail:** Stripe Connect is right for the stage Harold OS is in, not right forever. The v1 binding constraints are integration speed, developer ergonomics, operator self-onboarding, and regulatory perimeter — Stripe wins on all four. **This is a deliberate regulatory architecture choice, not just a fee choice.**

> A wallet-based EMI such as Mangopay is structurally a better fit for the long-term shape of this business — multi-party allocation, wallet-based escrow under Mangopay's own EMI licence, native deposit holds without expiry constraints. We defer it deliberately. The trigger to revisit is product-driven, not financial: the moment the roadmap commits to platform-held funds, Mangopay or equivalent becomes mandatory because the alternative is a TSS PI licence.

## 7. Reasoning flow (the canonical section order)

For each major section (H1), follow this rhetorical pattern:

1. **Why this matters** — one paragraph opening the section, framing the concern in business/architectural terms.
2. **The landscape** — a categorisation table listing every item in scope.
3. **The critical few** — H2 per item, each using the fixed bold-label vocabulary from §3.
4. **The important rest** — H3 per item, paragraph-length, lighter treatment.
5. **Supporting / nice-to-have** — bullet list, one-line per item. The only place bullets are welcome.
6. **What looks like it but isn't** — explicit subsection to forestall confusion ("Internal capabilities that look like X but aren't").
7. **Operational discipline** — health monitoring, graceful degradation, retry/idempotency. One H1.
8. **Climax callout** — the hard invariant (`DESIGN FOR FAILURE`, `WEBHOOK IS CANONICAL`), with the spectral hairline. This is the single luminous moment.
9. **Summary reference table** — every item, with criticality and failure mode in one row each.
10. **What's built vs what's planned** — bullet list, honest status.
11. **Summary** — one paragraph naming the categories, the critical items, and the discipline.

Drop steps that don't apply. Never reorder.

## 8. Formatting tokens (inherited from vector-guest-brand)

All values come from `vector-guest-brand/references/TOKENS.md`. Use the CSS vars in HTML output, the literal values in docx/pptx generators.

| Element | Family | Size | Colour | Other |
|---|---|---|---|---|
| Page ground | — | — | Linen `#F0EDE6` | The default everywhere — never pure `#FFFFFF` |
| Body | Space Grotesk 400 | 16px | Ink `#18171A` | Line spacing 1.55 |
| Mono kicker | Space Mono 400 uppercase | 11px | Ash `#8A8792` | Tracking 0.16em |
| Title | Space Grotesk 700 | 32–48pt | Ink | Tracking −0.05em, leading 0.9 |
| Subtitle | Space Grotesk italic 400 | 18–20pt | Ash `#8A8792` | Tracking −0.03em |
| H1 | Space Grotesk 600 | 28–32pt | Ink | Tracking −0.05em |
| H2 | Space Grotesk 600 | 20–22pt | Ink | Tracking −0.03em |
| H3 | Space Grotesk 600 | 16pt | Ink | — |
| H4 | Space Grotesk italic 400 | 14pt | Ash | sparingly |
| Callout banner | Space Mono 700 uppercase | 11px | Ink | Tracking 0.16em |
| Callout body | Space Grotesk 400 | 16px | Ink | Paper fill `#FAFAF8` |
| Climax callout top edge | — | 2px | `--vg-spectrum` gradient | Replaces top hairline only |
| Inline code | Space Mono 400 | 14px (≈ 0.9× body) | Ink | No background fill |
| Code block | Space Mono 400 | 13–14px | Ink | Paper fill `#FAFAF8`, hairline border |
| Table header | Space Mono 400 uppercase | 11px | Ash | Tracking 0.16em, no fill |
| Table body | Space Grotesk 400 | 16px | Ink | Hairlines between rows only |
| Hairlines | — | 0.5pt | Rule `#C8C4BC` | The only separator |
| Caption | Space Grotesk italic 400 | 14px | Ash | 12px space-above |

**Geometry**: square corners by default. Cards / callouts at radius 4px (`--vg-radius-2`). Page margins 1.0 inch in docx (US Letter); content column max 720px in HTML.

**Wordmark**: every doc carries the VECTOR\GUEST wordmark monochrome Ink (`logo-ink.svg` from vector-guest-brand assets) in the document header. Place it at the top-left, 16–20px tall, with a hairline rule below it. In docx use the header region so it repeats per page. **Default is monochrome.** Reserve `logo-slash` (Ink wordmark + gradient slash) for the cover of a major doc; never use `logo-spectrum` on a knowledge-base doc — that gradient already lives in the climax callout, and the brand is one luminous moment per view.

**What changes versus the old TSS template**: Arial → Space Grotesk · Roboto Mono → Space Mono · `#000000` text → Ink `#18171A` · pure white ground → Linen `#F0EDE6` / Paper `#FAFAF8` · `#c0303a` red callout stripe → spectral hairline on the climax callout only · `#555555` subtitle grey → Ash `#8A8792` · `#188038` green inline code → Ink monochrome. The body voice and structural grammar are untouched.

## 9. Monospace / code

The doc uses **Space Mono** in two situations (never Courier, Consolas, or Roboto Mono):

1. **Inline code identifiers** — field names, API parameters, account names. Space Mono 14px, Ink, no fill, no green. Examples: `amount`, `application_fee_amount`, `charge.succeeded`, `pending_card_holds`.
2. **Code blocks** — single-cell full-width panel, Paper fill `#FAFAF8`, 0.5pt hairline border Rule `#C8C4BC`, 20–24px padding. Code at Space Mono 13–14px, Ink, one paragraph per line, tabs preserved for indentation. No fenced ` ``` ` syntax-highlighted rendering — the panel is the visual cue, the typography carries the rest.

Space Mono is for technical labels and code only. Never body copy.

## 10. Diagrams, plots, and schemas — preserved unchanged

**This section is the deliberate exception to the rest of the refactor.** The diagram language Andre has already defined is the canonical Vector Guest diagram style; it does not adopt the spectral gradient. Mermaid by default; rendered JPEG as fallback; monochrome with TSS-red `#c0303a` as the single focal accent. Treat §10 as the canon for every diagram, graph, plot, and schema in any Vector Guest doc.

Reference example: the two-leg corridor state machine (MONEY LEG / OBLIGATION LEG → expected · received · open · part_allocated · allocated · settled, with a red dashed `Allocation` bridge from `open` to `received`). That diagram is the reference for every diagram in the canon. See `reference/diagram_style.md` for the full spec.

### Mermaid (default)

Use Mermaid for anything Mermaid can express cleanly: flowcharts, sequence diagrams, state machines, class diagrams, ER diagrams, Gantt charts, timelines, mindmaps, journey maps, pie charts. Mermaid renders natively in GitHub, Obsidian, and most modern doc viewers, and stays editable as code.

In markdown source: use a fenced ` ```mermaid ` block. In .docx output: pre-render the Mermaid to a clean JPEG (e.g. `mmdc -i diagram.mmd -o diagram.jpg -t neutral -b transparent --width 1600`) and embed as an image. Keep the `.mmd` source alongside the doc so the diagram stays editable.

**Mermaid styling discipline**:

- Theme: `neutral` or default. No `dark`, no `forest`.
- Node fill: white / transparent. Stroke: black (`#000000`) at 1.5px.
- Node text: black, Arial or Space Grotesk — sans-serif.
- **One focal node** outlined in TSS red `#c0303a` (1.5px stroke) — the box the eye should land on first.
- **One focal arrow** drawn as a red `#c0303a` dashed curve — the relationship the diagram is making a point about. Solid black for all other edges.
- Lane labels (where used): mono uppercase, Ash `#8A8792`, small caps.
- No shadows, no gradients (in the diagram), no emoji, no colour fills inside nodes.

### Rendered JPEG (fallback only)

Escalate to JPEG when Mermaid can't express the diagram cleanly: custom-styled architecture diagrams with non-standard layout, multi-layer system maps with depth/grouping that Mermaid mangles, real-data charts (matplotlib / plotly / d3, rendered server-side, exported as JPEG).

Requirements:

- **Resolution**: minimum 1600px wide for full-width figures, 300 DPI for print.
- **Typography**: Space Grotesk (or Arial as a fallback if Space Grotesk is not embeddable in the chart toolchain) — all axis labels, legends, annotations. No Helvetica, no system-default.
- **Colour**: black text on white or transparent background. TSS red `#c0303a` as the single focal accent. Greys (`#888888`, `#cccccc`) for supporting elements.
- **Caption**: one line, Space Grotesk italic 14px Ash, centred below the figure with 12px space-above.
- **Layout in the .docx / HTML**: centred, full content-width (no wider than the body column). The figure sits between two hairlines if it needs visual containment; otherwise no border.
- **Source artefact**: keep the rendering script (`build_chart.py`, `build_diagram.mmd`) checked in next to the doc so the figure is regenerable when data or design changes.

### What's not acceptable

- ASCII art boxes-and-arrows inside code blocks.
- Bullet-list approximations of a flow ("first X, then Y, then Z").
- Markdown tables pretending to be diagrams.
- Plain-text "diagrams" inside callout boxes.
- Raw Graphviz `dot`, PlantUML, D2, or any DSL source pasted with no rendered output.
- Screenshots of whiteboards, photos of paper sketches, anything < 1200px wide.
- A diagram using the spectral gradient. **Diagrams are the one part of the system where the accent is TSS red, not spectral.** That is deliberate.

### Conversion procedure when revising an existing draft

1. Scan the source for: ASCII art, ` ```dot `, ` ```plantuml `, ` ```d2 `, any `graph LR` / `flowchart TD` outside a `mermaid` fenced block, prose stubs like `[diagram: ...]` or `[chart goes here]`.
2. For each one: rewrite as Mermaid if possible. If not, render to JPEG per the spec above and replace the source with an image embed plus caption.
3. Keep both the editable source (`.mmd`, `.py`) and the rendered output in the doc's folder.
4. Never leave a diagram as "TODO — draw later" without at least a Mermaid skeleton. Use a `TODO —` callout if the diagram genuinely isn't ready yet, with the diagram spec written out in prose.

## 11. Pre-flight checklist (run before declaring done)

- Mono kicker line above the title (Space Mono uppercase Ash, `0.16em` tracking).
- Title appears once, Space Grotesk 700 at display size, with the canonical italic Ash subtitle below it.
- Page ground is Linen `#F0EDE6` — never pure white, never blue-grey.
- Opening callout present, Paper fill, hairline border, mono-uppercase banner.
- Exactly **one** climax callout in the doc carries the spectral gradient hairline (top edge only). Zero other uses of the gradient anywhere.
- Every H2 follows `Name — role` with an em-dash.
- Inside each entity H2, the bold-label vocabulary appears in canonical order.
- At least one categorisation table — no header fill, mono-uppercase Ash header text, hairlines between rows only.
- Inline code in Space Mono 14px Ink. Code blocks in Space Mono 13–14px on Paper fill with a hairline border. No green, no Roboto Mono.
- Wordmark in the document header (logo-ink.svg, monochrome, 16–20px tall, hairline rule below).
- British spelling throughout.
- Zero hedging language (`might`, `could`, `perhaps`, `seems`) outside explicit `Honesty about current state:` or `TODO —` markers.
- Em-dashes used as precision punctuation, not as comma substitutes.
- Section order follows §7: why-it-matters → landscape → critical few → important rest → supporting → discipline → climax callout → summary reference → status → one-paragraph summary.
- **Every diagram, graph, schema, and plot renders as a visual** (§10) — Mermaid by default, JPEG fallback, monochrome with TSS-red focal accent. Zero ASCII art, zero raw `dot` / `plantuml` / `d2`, zero `[diagram: …]` placeholders. Editable source (`.mmd`, `.py`) checked in alongside.
- Closing summary paragraph names the categories, the critical items, and the discipline in one sweep.

## Files in this skill

- `reference/integrations_map_anatomy.md` — annotated walk-through of `05_Integrations_Map`, mapping every section onto the §7 reasoning flow. Read this when the abstract spec isn't enough and you need a concrete worked example.
- `reference/diagram_style.md` — the canonical diagram style, with the two-leg corridor as the reference exemplar. Read this when §10 needs more detail than the SKILL.md summary.

## When to use other skills alongside

- **`vector-guest-brand`** — required co-skill. Provides the `colors_and_type.css` stylesheet (with base64-embedded Space Grotesk / Space Mono), the wordmark SVGs, the full token sheet, and the design discipline (one luminous moment per view, hue-as-atmosphere, hairlines over shadows).
- **`docx`** — required for `.docx` output. Use the `docx-js` route; pass the §8 token table verbatim into the docx-js style configuration. Callouts and code blocks need explicit `Table` constructions — Markdown blockquotes and fenced code won't reproduce the brand.
- **`vectorguest-vault`** — for research before drafting. Andre's project context lives in the Obsidian vault; consult it first for anything that depends on prior decisions, meeting outcomes, or existing definitions.
