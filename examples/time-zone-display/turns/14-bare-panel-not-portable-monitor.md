# Turn 14 — Bare Panel + Driver Board, Not Portable Monitor

## User

That's not the V2 spec we agreed. Starting with an orderable display monitor and then building around it doesn't make sense — especially with 3D printing on top of that, that's a worse approach. More logical to just buy the component for the screen. Example: a 15.6" laptop LCD replacement panel listing on AliExpress, eDP 30-pin, $37.70. Revise the build spec. What are the keywords for finding a monitor that isn't standalone and will work with this project?

## Assistant

Right call — the portable-monitor + 3D-shell-around-shell idea was double-enclosing. Cleaner DIY path is **bare laptop LCD panel + matched HDMI-to-eDP controller board + Pi**, all inside one purpose-built enclosure. Cyberdeck / arcade-cabinet builder pattern.

**Keyword vocabulary:**

*Panel:*
- "laptop LCD replacement screen" / "laptop LCD matrix"
- "bare LCD panel" / "LCD module"
- "eDP panel 15.6" / "LVDS panel 15.6"
- Or panel model number directly (e.g. `B156HAN02.1`, `N156HCA-EAA`)

*Interface:* eDP 30-pin (modern 2014+ panels) or LVDS 40-pin (older / cheaper). For 15.6" 1080p both are common; eDP preferred.

*Driver board:*
- "LCD controller board" / "LCD driver board"
- "HDMI to eDP" / "HDMI to LVDS" (matching panel interface)
- Common chipsets: RTD2660, RTD2270, M.NT68676, T.V56.031
- **Critical: buy panel + board as a matched kit from one seller** so the controller's EEPROM is pre-flashed for the panel model

*Kits / vendors:* "DIY monitor kit 15.6", "Raspberry Pi LCD kit", Waveshare matched kits.

**Structural changes to the spec:**

1. **Cost drops sharply.** Bare 15.6" eDP panel ~$40–65 + matched controller ~$18–28 = ~$60–95 vs. $180–230 for a portable monitor with kickstand and shell.
2. **Enclosure becomes the only shell.** No double-enclosing. Recommended: laser-cut aluminium front frame + 3D-printed PETG rear cover (cyberdeck standard). VESA 75/100 integral to rear.
3. **Power consolidates onto a single 12 V brick.** Driver board takes 12 V direct; Pi gets 5 V via internal buck converter. One mains cable, one barrel jack on the unit. (Previously two USB-C bricks were needed because portable monitors took USB-C PD.)

**Revised BOM (~$264–334 total):**

| Item | Spec | Price |
|---|---|---|
| 15.6" eDP IPS panel | AUO B156HAN02.1 / Innolux N156HCA-EAA | $40–65 |
| HDMI→eDP controller board (matched) | RTD2660 / M.NT68676 family | $18–28 |
| Pi CM5 4GB/32GB WiFi | Official | $75 |
| Waveshare CM5-IO-BASE-A | | $15 |
| 12V/5A brick + buck to 5V | Pololu D24V25F5 or LM2596 | $23 |
| Noctua NF-A4x10 5V + heatsink | GPIO PWM at 60°C | $20 |
| Enclosure: laser-cut Al + PETG rear | Custom, VESA 75+100 | $50–80 |
| Cabling, jacks, hardware | | $23 |
| **Total** | | **~$264–334** |

Saving vs. previous portable-monitor v2: ~$70–90. Saving vs. integrated Chipsee panel PC: ~$280–320.

Saved as `planning/build-spec-v2.md` (overwrites prior version).

## Notes

- **Major spec correction.** Display layer changes from "buy assembled portable monitor" → "buy bare laptop panel + matched controller board". Eliminates double-enclosing.
- **Form factor wins:** total depth target now < 30 mm (vs. ~40+ mm with a portable monitor inside another shell).
- **Power topology changes** as a side-effect: portable monitors required USB-C PD, forcing two-brick design. Bare panel + 12 V driver board enables single-12V-brick + internal buck-to-5V — cleaner, cheaper, single mains cable. Decision-mapping shift: previously deferred to "v3 polish", now achievable in v2 because the constraint that forced it (USB-C PD on the monitor) is gone.
- **Enclosure approach upgraded** from "all 3D-printed PETG" to "laser-cut aluminium front + 3D-printed PETG rear" — possible because there's no rival shell to fight, and aluminium gives finished-product look.
- **New constraint surfaced:** controller board EEPROM must match panel model — adds a "buy as matched kit" sourcing rule. Mismatch = manual EEPROM flashing via USB programmer.
- **eDP 30-pin established as preferred panel interface.** LVDS 40-pin acceptable as cheaper alternative. MIPI-DSI ruled out (size cap ≤10").
- **Outstanding sub-decisions narrowed:** lock specific panel SKU first, then order matching kit; CM5 supply check; enclosure CAD pending panel in hand; bench thermal test before committing to fan cutout.
- **Cost target now ~$264–334** for full v2 build — under the original Tier B band of $290–380 from turn 09 *despite* the active cooling and custom enclosure.
