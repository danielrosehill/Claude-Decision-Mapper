# Example: Time Zone Display

A DIY multi-timezone wall clock + dashboard, replacing a previous attempt that used multiple standalone WiFi-NTP LCDs (which drifted out of sync visibly).

**Live project repo:** `~/repos/github/my-repos/Time-Zone-Display-0526`
**Status:** in progress — decision space narrowed but not yet locked.

## Turn-by-turn log

| # | Topic | Shift |
|---|-------|-------|
| [01](turns/01-initial-brief.md) | Initial brief: timezones, display size, ESP32 vs Pi question | Spec drafted |
| [02](turns/02-orange-pi-and-architecture.md) | RPis unavailable; Orange Pis instead; min spec; standalone vs server architectures | Compute narrowed to Orange Pi; architecture chosen (server + thin clients) |
| [03](turns/03-integrated-units-esp32-revisit.md) | "Pi on the back is ugly" — integrated options? ESP32 cleaner? | Mounting options enumerated; ESP32 reassessed honestly; tablet floated as cleanest |
| [04](turns/04-veto-tablets.md) | Android tablets vetoed (unreliable for kiosk use) | Decision space collapsed to Pi-class SBC + 3 mounting paths |
| [05](turns/05-panel-pc-costs-and-thermals.md) | Panel PC costings + reflashability; monitor-sandwich thermals | Cost benchmarks set (~$115–185 DIY vs ~$150–500 preassembled); sandwich thermals confirmed viable with vented enclosure + standoff + heatsink |
| [06](turns/06-wireframe-times-and-penpot.md) | UTC-anchored time table for wireframe; Penpot MCP rebuild of the design | Wireframe v1 produced — hero row (Jerusalem + UTC), 3×2 grid west→east, footer dashboard |
| [07](turns/07-reliability-slim-vesa.md) | Display selection: 24/7 reliability, slim, VESA; price tiers | Shadow-box eliminated; display tiers mapped; branded portable (~$180–250) is the sweet spot, Mimo Vue HDX-1080C the officially-24/7 stretch; Pi-side hardening logged as separate axis (eMMC, RO rootfs, watchdog) |
| [08](turns/08-initial-vs-ideal-build.md) | Initial vs ideal build tiers | Two-tier roadmap: v1 = bench-build (existing monitor + Pi, glued); v2 = purpose-built kiosk panel (integrated SBC or LAN-served signage). Branded-portable demoted to v2 fallback; "smart monitor / all-in-one PC" category vetoed |
| [09](turns/09-budget-breakdown.md) | Budget breakdown across tiers | Four costed options: A ~$30–45 bench, B ~$290–380 sandwich, C ~$420–820 integrated, D ~$320–620 LAN-served. A→B path recommended; LAN-dependency tradeoff surfaced for D |
| [10](turns/10-panel-pc-products.md) | Specific panel-PC products with internal SBCs | Search-term reframing ("panel PC" → "Android wall tablet"/"meeting room tablet"); Chipsee Pi CM4/CM5 panel PC (~$350) identified as Tier-2 front-runner; Tier-C cost floor revised down; turn-04 tablet veto narrowed (consumer-only, not purpose-built signage tablets) |
| [11](turns/11-veto-android-and-locked-signage.md) | Veto Android and locked-appliance signage | Android-default panel PCs vetoed across all sub-tiers; Tizen/webOS/Q-Line/BrightSign vetoed (option D effectively removed). Surviving Tier-2 list: Pi CM4/CM5 panel PCs + Rockchip panel PCs with vendor Debian. Chipsee Pi CM4/CM5 10.1" reinforced as front-runner |
| [12](turns/12-display-size-vs-form-factor.md) | Display size vs integrated form factor | Use case = home-office glance from ~2 m. Sizing rule (text height ≈ distance ÷ 200) pushes toward 15.6"+. Integrated Pi-CM panel-PC market caps at 15.6"; 21"+ requires falling back to Tier B (monitor + Pi sandwich). Front-runner promoted from 10.1" → 15.6" Chipsee CS15600RA4156P; Tier B reactivated as size-driven fallback |
| [13](turns/13-self-build-spec-locked.md) | Self-build spec locked at 15.6" | Tier C (integrated panel PC) demoted to price reference; Tier B+ (deliberate sandwich w/ 3D-printed PETG case, Pi CM5 32GB eMMC, active 40mm Noctua, ~$355–405) promoted to primary path. eMMC requirement (decision 002) finally satisfied via CM5 over Pi 5. Cost beats integrated by ~$200 |
| [14](turns/14-bare-panel-not-portable-monitor.md) | Bare panel + driver board, not portable monitor | Display layer corrected: bare 15.6" eDP laptop panel + matched HDMI-to-eDP controller board, not assembled portable monitor. Eliminates double-enclosing. Single 12V brick + internal buck (no more dual USB-C PD). Enclosure upgraded to laser-cut Al front + PETG rear. Cost drops to ~$264–334. Keyword vocab logged for sourcing |

## Current state of the spec

See [`../../../Time-Zone-Display-0526/planning/01-spec-and-decisions.md`](../../../Time-Zone-Display-0526/planning/01-spec-and-decisions.md) (lives in the project repo, not this one).

Outstanding decisions:
- Mounting path: HMI panel-PC vs monitor-sandwich vs shadow-box frame
- API selections (weather, AQI source)
- Layout: portrait vs landscape
