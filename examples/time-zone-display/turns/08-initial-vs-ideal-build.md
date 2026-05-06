# Turn 08 — Initial vs Ideal Build Tiers

## User

Question about the final build. In terms of a starting/initial build and a more ideal version. The basic version can include just the monitor I have and an Orange Pi — getting it attached can just be glued on the back or something. In the more idealized build we're looking at a monitor specifically purpose-built for this, rather than buying a monitor and finding a way to add an SBC. Most ideally: an LCD monitor intended for use as a kiosk display, with an SBC built in or at least something that exposes Debian, intended for this purpose — *not* an all-in-one computer (the old "smart monitor with OS + USB ports" category is a different use case). Either the display is served locally from the SBC's memory, or it serves a digital display over the LAN. Either way it functions persistently as a kiosk display, VESA-mounted on the back.

## Assistant

Captured as decision 003 in the project repo. Two-tier roadmap:

**Tier 1 — Initial build (use what's here)**
- Existing monitor + Orange Pi
- Mounting: glue / VHB / zip-tie to the back
- Goal: prove the software stack end-to-end (kiosk Chromium, NTP, watchdog, read-only rootfs)
- Compromises on depth/aesthetics/VESA neatness explicitly accepted

**Tier 2 — Ideal build (purpose-built kiosk hardware)**
Two acceptable variants:
1. **All-in-one kiosk display with embedded SBC** — single VESA-mountable enclosure, panel + ARM/x86 SBC exposing Debian, renders dashboard locally
2. **Networked signage display** — VESA panel pulling dashboard from a LAN host (browser-based signage player or thin client at a local URL)

**Explicitly NOT wanted:** the older "smart monitor / all-in-one PC" category (Windows-on-a-stick + general-purpose desktop OS). Wrong category — that's an interactive workstation, not always-on kiosk.

Required Tier-2 properties: 24/7 rated, VESA 75/100, slim, Debian-exposed compute, either local rendering or LAN-served.

## Notes

- **New decision axis: build phasing.** v1 = ship-with-bench-hardware; v2 = purchase purpose-built. Software stack carries forward unchanged.
- **Decision 002's "branded portable monitor" tier demoted** from primary target to Tier-2 *fallback*. The preferred Tier-2 path is now an integrated kiosk panel or LAN-served signage, not portable-monitor-plus-Pi sandwich.
- **"Smart monitor / all-in-one PC" category explicitly vetoed** as a Tier-2 candidate — it's an adjacent product class but the wrong use case (interactive desktop, not signage).
- **Tier 1 is disposable** — corollary: don't over-invest in mounting/cabling for v1.
- Outstanding: which Tier-2 variant (integrated SBC vs LAN-served) is preferred. Unresolved.
