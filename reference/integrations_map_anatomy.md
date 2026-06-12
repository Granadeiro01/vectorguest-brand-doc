# `05_Integrations_Map` — annotated anatomy

A worked example of the Vector Guest knowledge-base style applied end-to-end. Use this as a concrete reference when the abstract spec in `SKILL.md` isn't enough. Every label below maps to a rule in `SKILL.md §1–11`.

Drive id: `16FSTT0bRNUB6k_8gjTCm3q4MI-S82TpD9FubxWBpVkw`
Drive title: `05_Integrations_Map`

> **Note on the historical version.** The version of `05_Integrations_Map` currently in Drive was authored in the previous TSS template (Arial, `#c0303a` callout stripe, black-on-white). The reasoning flow, heading patterns, and inline-bold-label vocabulary documented below are the canon and carry forward unchanged. The *visual aesthetics* (fonts, colours, callout treatment) have since been refactored onto the Vector Guest brand system — Space Grotesk / Space Mono, Linen / Paper / Ink / Ash, spectral gradient as the one luminous moment. Where this walk-through references a visual detail, the brand-refactored equivalent is given in parentheses.

## Opening block (§1)

```
[Mono kicker, Space Mono uppercase 11px Ash, tracking 0.16em]
    VECTOR GUEST · KNOWLEDGE BASE · INTEGRATIONS

[Title, Space Grotesk 700, display-size, Ink]
    Integrations Map

[Subtitle, Space Grotesk italic, 18–20pt, Ash]
    Every external system Harold OS talks to, what data flows, and which agent
    owns each connection. The plumbing of the platform.

[Opening callout — Paper #FAFAF8 fill, hairline border]
    SCOPE OF THIS DOCUMENT
    This document gives you the shape of Harold OS's external integrations at a
    level a senior contributor needs. For exhaustive per-integration detail —
    webhook payloads, exact endpoints, OAuth flows, error handling — see the
    canonical tss-integrations.md in the source-of-truth set.
```

The mono kicker replaces the old breadcrumb pattern (`TSS Knowledge Base · Integrations Map`) and any double-printed title that survived from the Google Docs export. The brand is sharp infra-grade: one mono label, one display title, one italic subtitle, one callout — then the doc starts.

## Reasoning flow (§7) — section by section

### H1: `Why integrations are a first-class concern`  → maps to §7.1 (Why this matters)

Two prose paragraphs. First names the architectural stance (Harold OS is system of record, replaces the PMS, integrates only with genuine infrastructure). Second names the questions every integration carries (ownership, failure detection, fallback) and tees up the rest of the doc.

### H1: `The six integration categories`  → maps to §7.2 (Landscape)

Opens with one sentence. Then a three-column table `Category | Purpose | Examples` covering all six categories. Table header in Space Mono uppercase Ash, body in Space Grotesk Ink, hairlines between rows only — no header fill, no zebra striping. Closes with a short paragraph defining what "owning agent" means.

### H1: `The critical integrations`  → maps to §7.3 (Critical few, H2 per item)

Four H2 sub-sections, each `Name — role`:

- `Channex — the channel manager`
- `Stripe — card payments`
- `Ponto — bank account access`
- `Anthropic Claude API — reasoning substrate`

Each H2 set in Space Grotesk 600, 20–22pt, Ink, with the em-dash structural and not decorative. Each follows the canonical inline-bold-label order: `Owning agent:` → `What it does:` → `What flows:` → `Why it matters:` → `Why we chose it:`.

### H1: `The important rest`  → maps to §7.4 (Important rest, H3 per item)

H3 per item: `Salto — locks`, `PriceLabs — comp-set pricing`, `AirDNA — market data`, `SendGrid — transactional email`, `WhatsApp Business API — guest messaging`, `Aircall — voice`, `Trustpilot — reviews`, `PredictHQ — event intelligence`. Each gets paragraph-length treatment, not the full label vocabulary.

### H1: `Supporting integrations`  → maps to §7.5 (Bullets)

A bullet list of low-criticality integrations (analytics, finance ops, internal tooling). One line per item. This is the only place bullets are welcome in the doc.

### H1: `Internal capabilities that look like integrations but aren't`  → maps to §7.6

Forestalls a common confusion: the rule engine, the semantic layer, and the orchestration loop *look* like integrations to outsiders but are first-party. Two or three short paragraphs.

### H1: `Operational discipline`  → maps to §7.7

Health monitoring, graceful degradation, retry/idempotency strategy. Three or four H3 sub-sections.

### Climax callout: `DESIGN FOR FAILURE`  → maps to §7.8 (the one luminous moment)

Sits immediately after the discipline H1, before the summary reference. **This is the doc's single permitted instance of the spectral gradient** — a 2px gradient hairline along the callout's top edge, banner in Space Mono uppercase Ink, body in Space Grotesk Ink. One paragraph stating the invariant: every integration is built assuming the upstream system will fail; the question is always "what does Harold OS do when it does", not "how do we prevent failure".

### H1: `Summary reference`  → maps to §7.9 (Reference table)

One table: `Integration | Primary agent | Criticality | What fails if it breaks`. Every integration in the doc appears as one row, in the same order they were introduced.

### H1: `What's built vs what's planned`  → maps to §7.10 (Status)

Two bullet lists side by side: shipped, planned. Honest about gaps.

### H1: `Summary`  → maps to §7.11 (One-paragraph close)

One paragraph naming the six categories, the four critical integrations, the discipline (design-for-failure, webhook-as-truth, idempotency, health monitoring), and pointing to the canonical source-of-truth set for deeper detail.

## Diagrams (§10)

`05_Integrations_Map` itself does not contain a diagram. When new docs in this canon do — payment-stack flows, state machines, system topologies — the rules in `SKILL.md §10` and `reference/diagram_style.md` apply: Mermaid by default, JPEG fallback, monochrome with TSS-red focal accent. **Diagrams are the deliberate exception to the spectral palette** — that is a feature of the system, not an inconsistency.

## Things to copy verbatim into new docs

- The opening callout's reference to a "canonical source-of-truth set" / "canonical tss-X.md" — every doc in the canon points at a deeper sibling for exhaustive detail. New docs should do the same, naming whichever sibling is the deeper layer.
- The `Owning agent:` opening label inside every entity H2. Even when the entity isn't an integration, the equivalent label is the right opener: `Owning team:`, `Owning function:`, `Accountable role:`.
- The closing summary's "X categories, Y critical items, Z disciplines" sweep.

## Things to never do

- Don't add a breadcrumb line above the title. The mono kicker is the orienting element; that is the entire opening layer.
- Don't replace the em-dash in `Name — role` with a colon or hyphen.
- Don't bullet content that belongs in a table.
- Don't use `**` bold for emphasis inside body prose — bold is reserved for the inline labels (`Why it matters:`) and the mono uppercase banners in callouts.
- Don't hedge. Replace "we might" / "we could" with either "we will" or an explicit `Honesty about current state:` paragraph.
- Don't use Arial, Calibri, Cambria, Roboto Mono, or Helvetica. Space Grotesk and Space Mono only.
- Don't make a code block via Markdown fencing — every code block is a single-cell panel with Paper fill and a hairline border.
- Don't reach for the spectral gradient outside the single climax callout.
- Don't reach for TSS red outside the diagram layer (§10).
