# vectorguest-brand-doc

A Claude skill that produces Vector Guest / TSS / Harold OS knowledge-base documents in the canonical house style — strategy memos, architecture docs, integrations maps, payment-stack writeups, build plans, operating models, market & competition docs, vision docs, READMEs, role specs.

The skill defines **the document layer**: anatomy, heading hierarchy, recurring sub-section labels, table conventions, callout discipline, prose voice, reasoning flow, and diagram rendering. **Aesthetics inherit from the `vector-guest-brand` skill** — Space Grotesk / Space Mono typography, Linen / Paper / Ink / Ash palette, spectral gradient as the one luminous moment per view. **Diagrams stay in Andre's monochrome + TSS-red language** — that is the deliberate exception, because the diagram canon is already settled.

## What the skill covers

- **Document anatomy** — mono-uppercase kicker line, Space Grotesk display title, italic Ash subtitle, opening callout on Paper fill with a hairline border.
- **Heading hierarchy** — Space Grotesk 600 at four sizes; H2 always `Name — role` with an em-dash.
- **Inline-bold sub-section vocabulary** — `Owning agent:`, `What it does:`, `What flows:`, `Why it matters:`, `Why we chose it:` in fixed order.
- **Tables** — hairlines between rows only, mono-uppercase Ash header text, no fills, no zebra striping.
- **Callouts** — Paper `#FAFAF8` fill, hairline border, mono-uppercase Ink banner. One climax callout per doc carries a 2px spectral-gradient hairline along the top edge as the single luminous moment.
- **Prose voice** — direct, declarative, zero hedging, British spelling, em-dashes as precision punctuation.
- **Reasoning flow** — why-it-matters → landscape table → critical few → important rest → discipline → climax callout → summary reference → status → one-paragraph close.
- **Formatting tokens** — full token table inherited from `vector-guest-brand`; Space Grotesk / Space Mono throughout, Ink `#18171A` on Linen `#F0EDE6`, hairlines in Rule `#C8C4BC`.
- **Diagrams and plots** — Mermaid by default for anything Mermaid can express; rendered JPEG (≥1600px, Space Grotesk, monochrome + TSS-red focal accent) as fallback. Diagrams keep their own colour language and do not adopt the spectral palette. The two-leg corridor state machine is the reference exemplar (see `reference/diagram_style.md`). No ASCII art, no raw `dot` / `plantuml` / `d2`, no `[diagram: …]` placeholders.

## Install

Drop `vectorguest-brand-doc.skill` onto Cowork (or any Claude client that supports skill bundles). The skill triggers automatically on Vector Guest / VectorGuest / TSS / Harold OS document requests, or on phrases like "in my usual format" or "like the integrations map". The companion `vector-guest-brand` skill should be installed alongside — it ships the fonts, logo SVGs, and the design-token sheet this skill depends on.

## Files

- `SKILL.md` — the skill itself (frontmatter + body).
- `reference/integrations_map_anatomy.md` — annotated walk-through of `05_Integrations_Map`, mapping every section onto the reasoning-flow skeleton.
- `reference/diagram_style.md` — the canonical diagram language, with the two-leg corridor as the reference exemplar.
- `vectorguest-brand-doc.skill` — packaged bundle, ready to install.
