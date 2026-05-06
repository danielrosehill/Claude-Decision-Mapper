# Turn 06 — Wireframe Times + Penpot Build

## User (combined)

1. Give me a set of times for a wireframe I'm building — 00:00 UTC in the target timezones.
2. Let's add Penpot MCP to this repo, or if you already have it connected, update my design.

## Assistant

### Times at 00:00 UTC (today is 2026-05-06, summer / DST)

| Zone | Summer (now) | Winter |
|---|---|---|
| Jerusalem (IDT/IST) | **03:00** | 02:00 |
| Shanghai (CST, no DST) | **08:00** | 08:00 |
| Paris (CEST/CET) | **02:00** | 01:00 |
| Cork (IST/GMT) | **01:00** | 00:00 |
| **UTC** | **00:00** | 00:00 |
| New York (EDT/EST) | **20:00 prev day** | 19:00 prev day |
| Chicago (CDT/CST) | **19:00 prev day** | 18:00 prev day |
| Los Angeles (PDT/PST) | **17:00 prev day** | 16:00 prev day |

Recommendation: mock the summer column — it's the common case and exposes the −1d edge case for US zones, which the layout must handle (small date stamp or "−1d" indicator).

### Penpot wireframe build

Confirmed already-connected via `mcp__jungle-personal__penpot__*`. Existing design had a 1271×715 grey canvas with scattered placeholder rectangles — cleared all but the background and rebuilt.

**Layout (1271×715, dark theme):**
- Header strip (40h): "TIME ZONE DISPLAY" + date
- Hero row (160h, 2 cards): **Jerusalem (Local)** with cyan accent bar, **UTC (Reference)**. 88px clock numerals.
- Grid (3×2 tiles, 154h each, 56px clock numerals):
  - Row 1: Cork · Paris · Shanghai
  - Row 2: Los Angeles · Chicago · New York (each marked "−1d")
- Footer dashboard (96h, 4 cells): Temperature, Air Quality, Hebrew Date, Zmanim — placeholders with realistic values

Palette: bg `#0F172A`, tiles `#1E293B`, primary text `#F1F5F9`, muted `#94A3B8`, accent `#38BDF8`. Source Sans Pro (300 for clock numerals, 400 body, 700 labels).

Geographic ordering (west→east in the grid) was chosen over alphabetic to match how a viewer's eye scans a world clock.

### Hiccups

- Penpot MCP tunnel went down twice mid-session (Cloudflare 502 → 1033). Recovered after backoff.
- Source Sans Pro doesn't support weight 600; corrected labels to weight 700.

## Notes

- **Wireframe v1 produced.** First concrete artifact for the design layer.
- **Layout principles surfaced:**
  - Local zone gets visual hierarchy (hero + accent bar)
  - UTC paired with local as second hero — it's the reference, deserves equal weight
  - Cross-day zones (US) need explicit −1d marker
  - Footer is functional, not decorative — same tile pattern, smaller scale
- **Outstanding:** real data wiring, layout responsiveness for portrait, font choice review (Source Sans Pro is fine but Inter / IBM Plex Sans worth testing for the clock numerals).
