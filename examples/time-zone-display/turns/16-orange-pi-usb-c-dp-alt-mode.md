# Turn 16 — Orange Pi USB-C DP Alt Mode Support

## User

What support, if any, is available on the Orange Pi for Type-C connectivity for monitors?

## Assistant

Mixed by board. Available on RK3588 family, absent on older Allwinner / RISC-V boards, and **not present on Raspberry Pi 5 / CM5 at all**.

| Board | SoC | DP Alt Mode |
|---|---|---|
| Orange Pi 5 / 5B / 5 Plus / 5 Pro / 5 Max / 5 Ultra | RK3588(S) | Yes — DP 1.4 |
| Orange Pi 4 / 4 LTS | RK3399 | Yes — DP 1.2 |
| Orange Pi 3 / 3 LTS | Allwinner H6 | No — power input only |
| Orange Pi Zero 2/3 | Allwinner H616/H618 | No |
| Orange Pi RV / RV2 | RISC-V | No (typically) |
| **Raspberry Pi 5 / CM5** | BCM2712 | **No** — USB-C is power-input only; display via micro-HDMI |

**Why it doesn't help here even when present:**

1. **Power direction conflict** — Pi USB-C is both power input and DP output. Monitor would need to feed PD back through a second port; pairing with Orange Pi's negotiation is unreliable.
2. **Driver maturity gaps** — RK3588 USB-C/DP works on vendor BSPs (Joshua Riek Ubuntu-Rockchip, Armbian); flakey elsewhere. Symptoms: works at boot, drops on resume, EDID misread, wrong resolution.
3. **Resolution/refresh quirks** — random portable monitors sometimes negotiate at 30 Hz or fail to wake.

**Recommendation:** ignore DP Alt Mode for this build. Use **HDMI for display + USB-C for power, separately**. HDMI is bulletproof on every Orange Pi 5-family board; USB-C-as-power-only is bulletproof. Two short cables behind a wall-mounted monitor are invisible — the "single cable" elegance only matters for portable laptops.

DP Alt Mode would pay off only if a USB-C touchscreen with display+touch over one cable were ever needed. Not in scope.

## Notes

- **Capability mapped, then deliberately not used.** Orange Pi 5-family DP Alt Mode is real; project does not depend on it.
- **Display interface locked: HDMI from Pi.** Same path on Pi CM5 (micro-HDMI) and Orange Pi 5-family (HDMI 2.0/2.1). Decision-portable across SBC choice.
- **One-cable USB-C-to-monitor topology rejected** for kiosk reliability reasons (PD negotiation fragility, driver-state gaps). Two-cable HDMI + USB-C-power topology is the locked path.
- **New comparative datapoint:** this is a feature where Orange Pi 5-family beats Pi 5/CM5 (which has no DP Alt Mode at all). Doesn't shift the SBC choice because the project doesn't need the feature, but worth noting if future projects do.
- **No change to the build spec** — the previous "HDMI for video, USB-C for power" approach was already correct; this turn confirms it against the alternative rather than adding new components.
