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

## Current state of the spec

See [`../../../Time-Zone-Display-0526/planning/01-spec-and-decisions.md`](../../../Time-Zone-Display-0526/planning/01-spec-and-decisions.md) (lives in the project repo, not this one).

Outstanding decisions:
- Mounting path: HMI panel-PC vs monitor-sandwich vs shadow-box frame
- API selections (weather, AQI source)
- Layout: portrait vs landscape
