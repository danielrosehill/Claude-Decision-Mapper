# Turn 09 — Budget Breakdown

## User

Give me a budget breakdown for a few options for the implementation.

## Assistant

Four options costed (USD, ex-VAT/shipping):

| Option | Description | Total |
|---|---|---|
| **A** — Bench build | Existing monitor + Pi + PSU/cable/tape/zip ties | **~$30–45** |
| **B** — Branded portable + Pi sandwich | Lenovo M14 / Asus MB16 / Dell C1422H + Pi 4 or Orange Pi 3 LTS + VESA mount + case | **~$290–380** (stretch: Mimo Vue HDX-1080C ~$550–600) |
| **C** — Integrated kiosk panel | Industrial panel-PC, ARM, 10–15", 24/7-rated, fanless, VESA. Single enclosure | **~$420–820** |
| **D** — LAN-served signage | Commercial signage display (Philips/LG/Samsung) + existing LAN host renders | **~$320–620** |

**Recommendation:** A → B path. Spend ~$40 on A this week to validate software in situ; jump to B (~$300) once validated. C/D only if aesthetics or fleet management justify the premium.

Trade-off flagged: D shifts dependency to LAN host availability — Pi-as-kiosk survives a brief network blip, LAN-served goes blank.

Saved as `planning/budget-options.md`.

## Notes

- **Decision space expanded from 2 (Tier 1 / Tier 2) to 4 concrete price tiers.** Tier 2 split into C (integrated SBC) and D (LAN-served), making the variants from turn 08 costable.
- **A→B established as the recommended path.** Skip-to-C only justified by aesthetics; D only justified by signage-fleet use cases that don't exist here.
- **New tradeoff surfaced:** LAN-served (D) is cheaper hardware on the wall but introduces network-dependency failure mode. Pi-local (B/C) tolerates short network outages.
- **Mimo Vue HDX-1080C** confirmed as the "officially 24/7-rated" stretch within tier B at +$200 over the branded-portable baseline.
- Cheap-China-Android sub-variant within C ($150–250) noted but flagged as firmware lottery.
