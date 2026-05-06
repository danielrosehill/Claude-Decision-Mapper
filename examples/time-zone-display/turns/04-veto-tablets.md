# Turn 04 — Veto: Tablets

## User

My only veto is actually Android tablets — I've found they are not very reliable for this use-case. So our decision space is now Pi.

## Assistant

Updated the planning doc to remove tablets from consideration and re-ranked the remaining options.

### Vetoed: Android tablets

Reason given: prior experience — unreliable for kiosk-style always-on use cases (background-task killing, OS updates breaking kiosk apps, battery degradation when permanently plugged in).

### Decision space now (Pi-class SBC only)

Ranked cleanest → most DIY:

1. **Linux-capable HMI panel-PC** (e.g. Seeed reTerminal RK3399, or RK3566/RK3588 panel-PCs). Single slab, ~$80–200. Caveat: most "HMI" boards in the 7–10" range are ESP32-based (LVGL only) — must specifically pick a Linux-capable SoC variant.
2. **Portable HDMI monitor + Orange Pi sandwiched behind**, hidden by a 3D-printed or wood frame extending the bezel depth. Cable management inside the frame; one power lead exits at the bottom.
3. **Bare LCD panel + LVDS/eDP→HDMI driver board (~$25) inside a deep shadow-box picture frame**, Orange Pi mounted to the back of the frame interior. Best-looking finished result; highest fabrication effort. The frame *is* the bezel.

### Recommendation

Shadow-box frame for the headline display if "looks like art" is wanted. Monitor-sandwich as the pragmatic fallback (and lets the spare 40×30 cm monitor get reused).

## Notes

- **Veto applied.** Decision space collapsed: 4 options → 3.
- **All remaining paths are Pi-based.** ESP32 also implicitly off the table (full spec retained).
- **Outstanding decisions:** mounting path, API selections, layout orientation.
