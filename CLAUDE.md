# CLAUDE.md — Claude-Decision-Mapper

## What this repo is

A library of real **decision-mapping conversations**: numbered turn-by-turn logs that capture how a spec gets iteratively refined through dialogue with Claude. The pattern (draft spec → correction/framing → narrow → repeat → lock) is described in the root `README.md`.

This repo is **not a plugin yet**. It's the substrate — real examples — that a future agent will reason over.

## Working in this repo

When the user is mid-conversation on a decision-mapping project (their own, elsewhere) and asks you to "save this turn", "log it", or similar:

- Use the **`save-turn` skill** in `.claude/skills/save-turn/SKILL.md`.
- The skill explains: file location, structure, Notes-block conventions, README index update, commit message.

## What counts as a turn

Log a turn when the conversation **shifts the decision space**: a constraint added or removed, an option vetoed or eliminated, a criterion reranked, a tradeoff surfaced, a sub-decision locked.

## Exception — do NOT log design/wireframe turns

Wireframing, layout, typography, color, Penpot edits, mockup iterations — **skip entirely**. They are execution detail, not decision-mapping substrate. The wireframe lives in Penpot; this repo is for the *reasoning* trail, not the *visual* trail.

If a turn mixes spec refinement and design work, log only the spec-refinement portion.

## Penpot MCP

For any design / wireframe work in a decision-mapping example, use the **Penpot MCP server**: `mcp__jungle-personal__penpot__*` (`high_level_overview`, `execute_code`, `export_shape`, `penpot_api_info`). Those interactions are **not** logged as turns here.

## Repo layout

```
examples/
  <project-slug>/
    README.md           — turn index + outstanding decisions
    turns/
      NN-<slug>.md      — one file per logged turn
    artifacts/          — optional supplementary material
.claude/
  skills/
    save-turn/SKILL.md  — the turn-saving skill
```

## Commit convention

`Turn NN: <short title>` for each new turn. Push immediately.
