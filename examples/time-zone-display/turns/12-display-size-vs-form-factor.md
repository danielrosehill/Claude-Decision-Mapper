# Turn 12 — Display Size vs Integrated Form Factor

## User

In terms of recommended display size — this is supposed to be high-visibility. Home office, glance to see next meeting and time in different places I'm working with. Currently the monitors I'm using are 21". 21" feels generous for this much information, especially with a news ticker. What's your assessment?

## Assistant

21" instinct is anchored on what your eyes are already calibrated to and is reasonable for the wireframe density. But it pushes off the surviving Tier-2 shortlist.

**Sizing-vs-distance table (rule: smallest text height ≈ viewing distance ÷ 200):**

| Size | Comfortable glance distance | Density fit |
|---|---|---|
| 7" | ~0.5 m | Cramped |
| 10.1" | ~0.8–1.0 m | Tight, ticker + grid fight |
| 13.3" | ~1.5 m | Good |
| 15.6" | ~2.0 m | Generous — best balance |
| 21–24" | ~2.5–3 m | Very generous; matches existing instinct |

**Tension:** the Pi-CM panel-PC market caps at ~15.6" (Chipsee CS15600RA4156P, ~$550–650). Above that, the integrated category disappears — 21"+ is a different product class (signage / monitor + separate SBC). HMI panel PCs were designed for arm's-length factory use, which is why 7–15.6" covers the market.

**Three coherent paths:**

1. **15.6" Chipsee Pi CM4 panel PC** (~$550–650). Top of integrated category. Glance-readable from ~2 m. Stays inside turn-11 list.
2. **13.3" Pi CM4 panel PC** (~$400–500). Fine if dashboard sits closer (above monitors, not across room).
3. **21–22" external monitor + Pi sandwich (Tier B)** (~$300–400). The only way to get 21" — sacrifices integrated form for size match.

**Recommendation:** start at 15.6" integrated. Information-sparse wireframe should glance-read at 2 m. If too tight after install, fall back to Tier B (21" + Pi sandwich) — 15.6" panel resellable.

## Notes

- **Forced tradeoff surfaced:** 21" desired vs Tier-2 (turn 11) capped at 15.6". Cannot have both.
- **New constraint:** smallest-text-height ≈ viewing-distance ÷ 200 — gives an objective sizing floor.
- **15.6" Chipsee CS15600RA4156P promoted** to top recommendation. Previously the 10.1" was the front-runner; bumped up because the home-office glance use case demands it.
- **Tier B (branded portable + Pi sandwich) re-enters** as the only path to 21"+. Previously demoted to fallback in turn 08; now reactivated as the size-driven escape hatch.
- **Decision rule established:** try integrated 15.6" first; treat Tier B as fallback if 15.6" reads too small after install. Hardware resellable, so low cost of being wrong.
- Outstanding: confirm viewing distance in actual office; mock dashboard at target size before ordering.
