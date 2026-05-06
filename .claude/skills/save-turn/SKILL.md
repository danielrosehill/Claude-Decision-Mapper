---
name: save-turn
description: Append a numbered turn file to the active decision-mapping example, capturing the user prompt + assistant response + a Notes block on what shifted (constraint added, option eliminated, decision narrowed). Use when the user says "save this turn", "log this", or after any turn that materially refines the spec or decision space. SKIP design/wireframe turns — those are irrelevant to decision mapping.
---

# save-turn

Captures one back-and-forth in the decision-mapping log so the iterative spec-refinement process is preserved as a durable artifact.

## When to use

Trigger on:
- Explicit user request: "save this turn", "log this", "add to the repo", etc.
- After any turn that **shifts the decision space**: constraint added/removed, option eliminated, criterion reranked, vetoed approach, surfaced tradeoff, locked sub-decision.

## When NOT to use (exceptions)

**Skip design / wireframe turns entirely.** Visual layout, Penpot edits, color/typography choices, mockup iterations — none of these belong in the turn log. They're execution detail, not decision-mapping substrate.

If the turn is purely about producing or revising a wireframe, do nothing for the turn log. The wireframe lives in Penpot (use the `mcp__jungle-personal__penpot__*` tools — high-level overview, execute_code, export_shape, etc.); reference it from the project repo if needed but do not log it as a "turn" here.

If a turn mixes spec refinement *and* design work, log only the spec-refinement portion.

## Where to write

```
examples/<project-slug>/turns/NN-<short-slug>.md
```

`NN` is the next zero-padded sequence number. Check `examples/<project-slug>/turns/` for the highest existing number.

Also update `examples/<project-slug>/README.md` — append one row to the turn-by-turn table.

## Turn file structure

```markdown
# Turn NN — <Short Title>

## User

<Lightly cleaned prompt — voice-input artifacts removed, no semantic changes. Preserve the user's framing and emphasis.>

## Assistant

<Condensed response — keep the substantive content (recommendations, tables, tradeoffs). Drop banter, drop repeated context, drop tool-call narration.>

## Notes

- **What shifted in this turn** — one bullet per shift. Concrete, specific.
- Constraint added / option vetoed / criterion reranked / decision narrowed.
- Outstanding questions raised.
```

The **Notes** block is the load-bearing part — it's what a future agent reasoning over the log will read first. Be specific:

- Bad: "Discussed mounting options."
- Good: "Shadow-box frame eliminated (too deep for slim kitchen mount). Decision space: 4 → 3 paths."

## Index update

Append a row to `examples/<project-slug>/README.md`:

```
| [NN](turns/NN-<slug>.md) | <topic> | <shift summary> |
```

## Penpot MCP note

For any design / wireframe work in any decision-mapping example, use the Penpot MCP server (`mcp__jungle-personal__penpot__*`) — `high_level_overview`, `execute_code`, `export_shape`, `penpot_api_info`. Do **not** log those interactions as turns here.

## Commit

After writing the turn + updating README, commit with message `Turn NN: <short title>` and push.
