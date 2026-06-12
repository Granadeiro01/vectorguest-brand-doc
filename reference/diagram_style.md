# Diagram style — the canonical Vector Guest exemplar

This is the reference for every diagram, graph, plot, and schema in a Vector Guest knowledge-base document. **It is the deliberate exception to the spectral-gradient brand system** — diagrams use a different accent (TSS red) because that is the language Andre's diagram canon was built in, and consistency inside the diagram layer matters more than colour-system unification with the body.

If you are unsure how a diagram should look, default to the two-leg corridor exemplar below.

## Reference exemplar — the two-leg corridor

A state-machine diagram with two horizontal lanes:

- **MONEY LEG** (top lane): `expected` → `received` (with `received` as the focal node — outlined in TSS red, not filled).
- **OBLIGATION LEG** (bottom lane): `open` → `part_allocated` → `allocated` → `settled`.
- **Allocation bridge**: a red `#c0303a` dashed curved arrow from `open` (bottom lane) to `received` (top lane), labelled `Allocation` in italic red.
- **Transfer + Payout** edge from `allocated` to `settled`, labelled in small italic black.
- **Lane labels** `MONEY LEG` / `OBLIGATION LEG` set in Space Mono uppercase Ash (`#8A8792`), small.
- **Caption** beneath the diagram: italic Space Grotesk 14px Ash — *"The two-leg corridor — the money leg resolves identity for free at received; the red Allocation bridge is where the work moved."*

That diagram is the canon. Every other diagram in the knowledge base should read as if it came from the same hand.

## The rules (taken from `SKILL.md §10`, expanded)

### Geometry

- **Nodes**: rectangles with sharp corners (or 2–4px radius at most). Stroke 1.5px solid black `#000000`. Fill white or transparent — **never coloured**.
- **One focal node per diagram**: same shape and size as the others, but stroke is TSS red `#c0303a` at 1.5px. This is the box the eye should land on first.
- **Edges**: solid black 1px arrows, with a small filled triangular arrowhead.
- **One focal edge per diagram** (optional, when there's a relationship that carries the point): drawn as a TSS red `#c0303a` dashed curve, same arrowhead style. Use sparingly — most diagrams have a focal node but no focal edge; some have both.
- **Lanes / groupings** (when needed): a thin Ash `#8A8792` hairline above or below the lane, with a Space Mono uppercase Ash label at the far left.
- **No coloured fills inside nodes. No gradients. No shadows. No emoji. No icons.** The diagram is the typography and the geometry — nothing else.

### Typography inside the diagram

- **Node text**: black, sans-serif. In Mermaid use the default font; in rendered JPEGs use Space Grotesk (Arial as fallback if the toolchain can't embed Space Grotesk). 14px or so — match body size.
- **Edge labels**: italic, smaller (12px), black for ordinary edges, TSS red for the focal edge label.
- **Lane / region labels**: Space Mono uppercase, Ash, 11px, tracking `0.16em` — the same `.vg-label` treatment used everywhere else in the doc.

### Caption

Every diagram has a caption directly beneath it:

- Space Grotesk italic 14px, Ash `#8A8792`, centred.
- Format: one sentence stating *what the diagram is about and where the eye should land*. The two-leg corridor caption is canonical: it names the structure ("two-leg corridor") and the move ("the red Allocation bridge is where the work moved").
- The caption is part of the diagram, not a body paragraph. It carries the meaning that the visual carries silently.

### Layout in the doc

- Centred, full-width up to the body column (no wider than 720px in HTML, full content-width in docx).
- 12–16px space above (after the body paragraph that introduces it) and 8px space between the diagram and its caption.
- If the diagram needs visual containment, sit it between two hairlines (Rule `#C8C4BC`). Otherwise no border around the figure.

## Mermaid template for the two-leg corridor

```mermaid
flowchart LR
    %% MONEY LEG
    subgraph money["MONEY LEG"]
        direction LR
        expected[expected]
        received[received]
        expected --> received
    end

    %% OBLIGATION LEG
    subgraph obligation["OBLIGATION LEG"]
        direction LR
        open[open]
        part_allocated[part_allocated]
        allocated[allocated]
        settled[settled]
        open --> part_allocated --> allocated -->|Transfer + Payout| settled
    end

    %% Allocation bridge — focal edge
    open -. Allocation .-> received

    %% Styling
    classDef default fill:#FFFFFF,stroke:#000000,stroke-width:1.5px,color:#000000;
    classDef focal fill:#FFFFFF,stroke:#c0303a,stroke-width:1.5px,color:#000000;
    class received focal;
    linkStyle 5 stroke:#c0303a,stroke-dasharray:4 3,color:#c0303a;
```

Notes on the Mermaid:

- The `classDef focal` redefines the focal node so `received` gets the red stroke.
- `linkStyle 5` targets the Allocation edge (the 6th edge in declaration order, zero-indexed). Adjust the index if edges are reordered.
- When rendering to JPEG via `mmdc`, pass `-t neutral -b transparent --width 1600` so the output sits cleanly on Linen or Paper backgrounds.

## When to use Mermaid vs. JPEG

- **Mermaid**: flowcharts, sequence diagrams, state machines, class diagrams, ER diagrams, Gantt, timelines, mindmaps, simple journey maps, pie charts.
- **JPEG**: architecture diagrams with custom layout, multi-layer system maps Mermaid mangles, real-data charts (matplotlib / plotly / d3), anything with bespoke positioning. Render at ≥1600px wide, Space Grotesk (or Arial) labels, monochrome with TSS-red focal accent.

In both cases the rules above apply — black geometry, one red focal element, italic Ash caption.

## What's not acceptable (mirrored from §10)

- ASCII art.
- Bullet-list "flows".
- Markdown tables pretending to be diagrams.
- Plain-text diagrams stuffed into callouts.
- Raw `dot`, `plantuml`, `d2` source pasted as a code block with no rendering.
- Screenshots of whiteboards or paper sketches.
- Diagrams using the spectral gradient instead of TSS red. **The diagram layer is the explicit exception** — it does not adopt the spectral palette.
- A diagram without a caption.
