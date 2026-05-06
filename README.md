# Claude-Decision-Mapper

A repository for mapping and codifying an iterative spec-refinement process used with Claude (and applicable to other LLM-driven planning conversations).

## The pattern

Across a wide range of projects — software builds, hardware purchases (printers, monitors, etc.), home-lab decisions — Daniel has found that the highest-quality outcomes come from the same loop:

1. **Define a draft spec** — state goals, constraints, available resources, and rough preferences.
2. **Receive correction / framing** — Claude responds with what's possible, what isn't, and where the tradeoffs sit.
3. **Narrow the decision space** — vetoes, new constraints discovered along the way, allocations that change.
4. **Repeat 2–3** until the decision space collapses to one or two viable paths.
5. **Lock the spec** — the final agreed-upon document becomes the bedrock / source of truth for the build (or purchase, or migration).

Each turn refines either the *problem* (what is actually wanted) or the *constraint set* (what is actually available / acceptable). The value is in capturing both halves — not just the final decision.

## Purpose of this repo

This repo is **not** a plugin yet — it's the explanation and reference material that a future plugin/agent will be built against. Specifically:

- Capture real conversation turns from live decision-making sessions
- Preserve them in a structured, numbered form so the back-and-forth structure is legible
- Use them as ground-truth examples for designing an agent that helps drive this loop deliberately (prompting for missing constraints, surfacing premature decisions, marking when the decision space has actually narrowed, etc.)

## Structure

```
examples/
  <project-name>/
    README.md           — what was being decided, final outcome (when reached)
    turns/
      01-<title>.md     — turn 1: user prompt + assistant response
      02-<title>.md
      ...
    artifacts/          — final spec, planning docs, etc. (linked from outside if too large)
```

Each turn file contains:
- The **user prompt** (lightly cleaned for readability — voice-input artifacts removed, no semantic changes)
- The **assistant response**
- Optional **notes** on what shifted in this turn (constraint added, option vetoed, decision narrowed)

## Current examples

- [`examples/time-zone-display/`](examples/time-zone-display/) — DIY multi-timezone wall clock with dashboard. In progress.
