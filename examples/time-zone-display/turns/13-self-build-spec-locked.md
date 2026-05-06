# Turn 13 — Self-Build Spec Locked at 15.6"

## User

Let's go with 15.6". The panel PC market is very small / niche — easier to find the components: display, SBC, PSU, case (with VESA on the back). Give me the full spec for the updated build, and handle cooling safely given the Pi is contained.

## Assistant

Locked 15.6". Strategy pivot: away from "buy integrated panel PC" (Tier C, niche market) back to "self-assembled sandwich done properly" (Tier B+, deliberate enclosure rather than glue).

**Topology:** 15.6" portable monitor + Raspberry Pi CM5 + dual-output PSU + 3D-printed PETG enclosure with VESA 75/100, mounted as one unit.

**Component summary:**

| Component | Pick | Price |
|---|---|---|
| 15.6" portable monitor | Lenovo ThinkVision M15 or Asus ZenScreen MB16ACE | $180–230 |
| Compute | Pi CM5 4GB/32GB WiFi + IO board | $95 |
| PSU (v2 simple) | Two PSUs: Pi 27W USB-C + monitor's bundled | $12 |
| Cooling | Noctua NF-A4x10 5V (GPIO PWM, on at 60°C) + aluminium heatsink | $20 |
| Enclosure | 3D-printed PETG, custom, VESA 75+100 | $20 (filament) |
| Cabling, standoffs, clips | Short right-angle USB-C, M3/M4 kit | $28 |
| **Total** | | **~$355–405** |

**Key spec decisions:**

- **CM5 over Pi 5** because eMMC variant exists (32 GB onboard), satisfying decision 002's reliability requirement without microSD or NVMe HAT.
- **Two-PSU approach** for simplicity (one mains plug for Pi, one for monitor) — single-brick DC-DC variant deferred to v3 polish pass.
- **Active cooling required** — Pi CM5 hits 85°C thermal throttle under sustained Chromium load; 40mm Noctua at GPIO PWM (only spins above 60°C) keeps it at ~55–65°C silently.
- **3D-printed PETG enclosure**, not PLA — PLA softens at the temperatures the Pi side will reach; PETG holds at 70°C+.
- **Vented design with ≥8mm Pi-to-wall standoff gap** for convection even with fan off.

**Cost vs Tier-C reference:** Chipsee 15.6" Pi CM4 panel PC ~$550–650. Self-build saves ~$200, gets newer CM5 silicon, and allows better panel choice.

Saved as `planning/build-spec-v2.md` in the project repo.

## Notes

- **Strategic pivot:** Tier C (integrated panel PC, Chipsee CS15600RA4156P) demoted to *price reference*, not target. Reason: market is too niche, and a deliberate self-build at the same size point is cheaper and more flexible. Decision 003's "Tier 2 = integrated panel PC" assumption effectively superseded.
- **Tier B (sandwich) re-promoted to primary path** but with a major upgrade: custom 3D-printed enclosure + Pi CM5 + active cooling, vs the original "glue Pi to back of monitor" framing. The form factor gap between Tier B and Tier C closes considerably.
- **Compute SKU locked: Pi CM5 4GB/32GB-eMMC**, with Pi 5 + NVMe Base as fallback if CM5 supply is bad.
- **eMMC requirement (decision 002) finally satisfied** by switching from Pi 5 (microSD/NVMe only) to Pi CM5 (eMMC native). Closes a decision-002 follow-up.
- **Enclosure material spec locked: PETG, not PLA** — temperature-driven choice based on Pi thermals.
- **Cooling strategy locked:** active 40mm fan on GPIO PWM threshold, with passive convection as graceful-degradation path if fan dies.
- **PSU strategy: two separate PSUs for v2**, single-brick DC-DC explicitly deferred (v3 polish, not a v2 blocker).
- **Cost target: ~$355–405** for full v2 build. Sits inside the original Tier-B band ($290–380) from turn 09 with a small premium for active cooling + custom enclosure.
- Outstanding: CM5 availability check in IL; portrait vs landscape (still open from earlier turns); enclosure CAD work pending monitor purchase; bench thermal test before fan-vs-convection commit.
