# Turn 10 — Specific Panel-PC Products with Internal SBCs

## User

Can you give me some specific products for panel PCs that have internal SBCs? I can't find any on AliExpress, just to get a sense for form factor and price. I'm seeing a lot of i7-based builds that seem overkill for signage.

## Assistant

The "i7 panel PC" results on AliExpress are **industrial HMI** (factory automation, legacy Windows). Wrong category. The right search terms are **"Android tablet PoE wall mount"** or **"meeting room tablet"** — that's where the ARM-SoC + VESA + always-on category actually lives.

**Tier C-low: Android wall tablets, Rockchip (~$200–400)**
- RAYPODO 10.1" PoE wall tablet (RK3566, 1280×800, Android 11, free VESA bracket) — ~$230 on Amazon
- Geekland GK-TVR-POE-DS (RK3399, 350 nits, signage-targeted) — ~$280
- Shining SH1059LX / SH101KJ-T (RK3576S, VESA 75) — ~$250–350
- Mimo Adapt-IQV 10.1" — ~$400–500

**Tier C-mid: Industrial Rockchip panel PCs (~$400–700)**
- Chipsee PPC-RK3576-101 (RK3576 octa, 480 nits, IP-rated front)
- Chipsee PPC-A55-101S (RK3568, IP65)
- Geniatech TPC-K3 (RK3568, 10–32" range)
- Vantron VT-PPC series (RK3566/RK3568)
- Most ship Android by default; vendor Linux/Debian images on request (Chipsee publishes Debian builds)

**Tier C-high: Raspberry Pi CM4/CM5 panel PCs (~$300–500)** — *the sweet spot for this use case*
- Chipsee CS10600RA4101P (Pi CM4, 10.1") — ~$330–400
- Chipsee Pi CM5 panel PC (7" / 10.1") — ~$350–450
- Literally "Pi in a panel" sold as one SKU. Full Raspberry Pi OS, VESA, no sandwich.

**Top pick for the spec:** Chipsee CM4/CM5 10.1" panel PC, ~$350.

Offered to fold this into the budget doc as a Tier-C product list.

## Assistant Sources (preserved for trail)

- chipsee.com/product-category/ipc/arm-rockchip/
- chipsee.com/product-category/ipc/arm-raspberry-pi/
- cnx-software.com — Chipsee 15.6" panel PC review
- linuxgizmos.com — Pi CM4 panel PCs
- amazon.com — RAYPODO 10.1" PoE
- geekland.co — GK-TVR-POE-DS
- mimomonitors.com — Adapt-IQV 10.1"
- shiningltd.com — SH101KJ-T

## Notes

- **Search-term reframing was the load-bearing shift.** "Panel PC" → "Android wall tablet" / "meeting room tablet" / "PoE signage tablet" unlocks the actual product category. The i7 results were a category mismatch, not a market gap.
- **New preferred Tier-2 candidate identified: Chipsee Pi CM4/CM5 panel PC (~$350).** Beats the previously-assumed "$400–820 industrial integrated" range from turn 09 and keeps Debian-native (Pi OS) without a vendor port. This collapses the gap between B (Pi sandwich) and C (integrated) — for ~$50 more than B you get the integrated form factor.
- **Tier C cost floor revised down** from ~$420 (turn 09) to ~$230 (RAYPODO Android wall tablet) at the cheap end, ~$330 (Chipsee CM4) for Linux-native.
- **Android-as-host re-entered the conversation** via the wall-tablet category, in tension with turn 04's earlier veto of tablets. Distinction: turn 04 vetoed *consumer* Android tablets (battery, sleep, crash); turn 10 candidates are *purpose-built wall-mounted* Android devices designed for always-on signage. Veto narrowed, not lifted.
- Decision space: Tier 2 now has a clear front-runner (Chipsee CM4/CM5 panel PC) rather than an open category.
- Outstanding: confirm 10.1" is the right size (vs 7" or larger); confirm portrait/landscape; lock SKU.
