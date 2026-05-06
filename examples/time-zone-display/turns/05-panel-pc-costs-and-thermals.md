# Turn 05 — Panel PC Costs & Sandwich Thermals

## User

Give me approximate costings for panel PCs and whether they typically ship with a preinstalled base OS or can be flashed with say RPi OS. Objective is to compare the cost of preassembled vs assembly. The other question with the portable HDMI monitor approach: it can be glued onto the back of a screen pretty easily, but what about thermals and cooling? Can basic heatsink cooling work even when the PC is horizontally mounted (board lying parallel to the back of the monitor within a little plastic assembly)?

## Assistant

### Panel PC costings (Linux-capable only)

| Class | Examples | Size | Price | Ships with |
|---|---|---|---|---|
| Pi-CM4 integrated | Seeed reTerminal | 5" 1280×720 | ~$195 | Raspberry Pi OS — fully reflashable |
| Pi-CM4 integrated, larger | Seeed reTerminal DM | 10.1" 1280×800 | ~$400–500 | Raspberry Pi OS — reflashable |
| Industrial Chinese RK panel PC | Generic RK3566/RK3568 | 7"–10.1" up to 1920×1200 | ~$120–250 | Usually Android; some Debian/Ubuntu. Reflashable via RKDevTool. Quality lottery. |
| RK3588 panel PC | Firefly, Mekotronics, Radxa-based | 10.1"–15.6" | ~$300–500 | Android 12 or Debian; reflashable. |
| x86 panel PC | LattePanda-based, POS-style | 10"–13" | ~$250–500 | Windows or none; flash anything. Hotter. |
| Used POS terminals | eBay surplus | 10"–15" | ~$50–150 | Windows POS — wipe and install Debian. Sleeper option. |

**Monitor-sandwich (path 2) cost stack for comparison:**
- Orange Pi Zero 2 / 3 LTS: ~$30–50
- 10.1" portable HDMI monitor (1920×1200 IPS): ~$70–110
- Frame + cabling + heatsink: ~$15–25
- **Total: ~$115–185** — cheaper than preassembled by $50–250.

**Reflashability:** all are reflashable. Pi-CM4 panels trivial (SD). RK panels need RKDevTool via USB-C in maskrom mode. None are locked.

**Buying-assembled benchmarks:**
- reTerminal DM at ~$450 — zero fabrication, Pi ecosystem
- Industrial RK3566 at ~$150–250 — sweet spot if Linux support pans out

### Thermals (monitor sandwich)

Passive cooling works fine even with the board parallel to the monitor back, **provided the enclosure isn't sealed.**

- **Orientation is not the issue.** Convection works in any orientation at this scale; heatsinks don't need gravity.
- **The real risk is heat soak from the monitor itself.** LCD backlights radiate heat backward through the rear panel — steady-state ~30–40°C. Bonding the Pi flush to that surface starts the SoC at +40°C ambient before any load.

**Mitigations (do all four):**
1. 10–15 mm standoff gap between Pi and monitor back — don't glue flush
2. Vent slots at top *and* bottom of the plastic enclosure (chimney effect)
3. Aluminum finned heatsink on the SoC (5–10 mm, ~$2)
4. Pick a cool SoC — Allwinner H3/H5/H6 and RK3328 stay under 70°C passively under Chromium load. **Avoid RK3588** in a sealed sandwich.

Optional: 30 mm 5 V fan (~$3) for RK3566+ or extra headroom. Powered off Pi's 5 V rail; inaudible at low RPM.

**Practical baseline:** OPi Zero 2 (H616) running Chromium kiosk at ~30% CPU idles ~55°C in a 25°C room with vented enclosure + heatsink. Comfortable margin to the 85°C throttle point.

## Notes

- **Cost comparison surfaced:** preassembled premium is $50–250 over a self-assembled monitor-sandwich.
- **Benchmark established:** reTerminal DM (~$450) is the "no fabrication, just buy" reference.
- **Thermal concern resolved:** sandwich approach is viable with vented enclosure, 10–15 mm standoff, heatsink, and SoC choice. Eliminates a previously unstated risk for path 2.
- **Constraint emerging:** SoC selection now matters for path 2 (avoid RK3588 unless adding a fan).
