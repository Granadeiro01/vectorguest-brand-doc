# vectorguest-brand-doc

A Claude skill that captures the VectorGuest / TSS / Harold OS knowledge-base house style and reproduces it for every new document — strategy memos, architecture docs, integrations maps, payment-stack writeups, build plans, operating models, market & competition docs, vision docs, READMEs, role specs.

The canonical example the skill mimics is `05_Integrations_Map`. New documents come out indistinguishable from it in structure, formatting, and reasoning flow.

## What the skill covers

- **Document anatomy** — twice-printed title, italic grey subtitle, opening callout with a TSS-red top stripe.
- **Heading hierarchy** — H2 is always `Name — role` with an em-dash.
- **Inline-bold sub-section vocabulary** — `Owning agent:`, `What it does:`, `What flows:`, `Why it matters:`, `Why we chose it:` in fixed order.
- **Tables as the grouping device** — categorical content is always a table, never a bullet list.
- **Callout boxes** — single-cell tables with `#fafafa` fill and a 0.75pt `#c0303a` top border. ALL-CAPS banner heading inside.
- **Prose voice** — direct, declarative, zero hedging, British spelling, em-dashes as precision punctuation.
- **Reasoning flow** — why-it-matters → landscape table → critical few → important rest → discipline → invariant callout → summary reference → status → one-paragraph close.
- **Formatting specifics** — Arial throughout, Roboto Mono for code, 1.15 line spacing, US Letter with 1.0-inch margins.

## Install

Drop `vectorguest-brand-doc.skill` onto Cowork (or any Claude client that supports skill bundles). The skill triggers automatically on VectorGuest / TSS / Harold OS document requests, or on phrases like "in my usual format" or "like the integrations map".

## Files

- `SKILL.md` — the skill itself (frontmatter + body).
- `reference/integrations_map_anatomy.md` — annotated walk-through of `05_Integrations_Map`, mapping every section onto the reasoning-flow skeleton.
- `vectorguest-brand-doc.skill` — packaged bundle, ready to install.
