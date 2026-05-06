# Turn 07 — Display: Reliability, Slim, VESA

## User

Ideally we want something running 24/7. Nice light/viewing settings are fine but for something going up in a kitchen, the main thing is **reliability** — not best viewing experience. Reliability is the top criterion. Second criterion: **VESA mount** (will be wall-mounted). Landscape vs portrait TBD when wireframes are finished. Targeting display recommendations and price approximations.

## Assistant

### Constraint hierarchy

1. 24/7 reliability — top
2. Slim form factor (kitchen wall)
3. VESA mount — required
4. Panel viewing quality — secondary

### What "24/7 reliable" means for an LCD

- **Backlight rated lifetime.** Cheap portables: 20–30k hr. Signage-grade: 50–70k hr. 24/7 = 8,760 hr/yr — a 30k-hr panel hits half-brightness in ~3.5 yr; 50k-hr in ~5.5 yr.
- **No auto-power-off / no "no signal" nag overlays.** Consumer monitors often sleep after idle or flash error overlays; signage/kiosk monitors don't.
- **Capacitor quality** on the driver board — branded monitors have published reliability data, no-name doesn't.
- **Burn-in is a non-issue on IPS LCD** (OLED problem only). Don't pay to "solve" it.
- **Brightness uniformity over time.** Cheap edge-lit panels develop visible gradients within a year of always-on.

### Display tier table (10–15" landscape, VESA, slim)

| Tier | Examples | Price | Rated 24/7? | Notes |
|---|---|---|---|---|
| Cheap portable HDMI | No-name AliExpress / Amazon 13.3" | $70–110 | No | Lottery; 8–12 mm; VESA 75 hit-or-miss |
| Branded portable | Lenovo ThinkVision M14, Asus ZenScreen MB16, Dell C1422H, AOC | $180–300 | Not officially, realistic 3–5 yr | Real QC; VESA 75 standard; ~10–15 mm |
| Small office / photo-frame | ViewSonic VA1655, Philips 162B9, Iiyama ProLite 13–15" | $130–220 | "Light commercial" / 16×7 | 30–40 mm; conservative power |
| Industrial / signage | Mimo Vue HDX-1080C, ELO 1002L, AOpen DT 10/15, Philips Q-Line | $300–700 | **Yes — 24/7 rated** | 15–25 mm; VESA 75/100; best longevity |
| Repurposed used monitor | Off-lease Dell/HP with VESA | $40–90 | No | Cheap & solid but ~50 mm + ugly bezels |

### Recommendation

**Branded portable monitor at ~$180–250** is the practical sweet spot — slim, VESA 75, real QC, ~5 yr expected at 24/7. Specific candidates worth checking: **Lenovo ThinkVision M14**, **Asus ZenScreen MB16**, **Dell C1422H**.

**Step up to Mimo Vue HDX-1080C (~$450)** if officially-warrantied 24/7 matters — overbuilt for a kitchen clock but lifetime peace of mind.

**Avoid no-name AliExpress portables** for always-on duty — the $50 saved isn't worth the failure-rate uplift.

### Pi-side reliability (separate axis, still required)

Whichever display is picked, the Pi side also needs hardening for 24/7:

- **eMMC over SD card** (filters Orange Pi SKUs to those with eMMC, e.g. Orange Pi 3 LTS)
- **Read-only root filesystem** (overlayfs on Armbian)
- **Hardware watchdog** via `systemd-watchdog`
- **Solid 5V/3A PSU** (not the bundled freebie)
- **systemd `Restart=always`** on the Chromium kiosk unit, with `After=network-online.target`

### Path table after this turn

| Path | Display depth | VESA | 24/7 outlook |
|---|---|---|---|
| Industrial RK3566 panel PC (display + compute integrated) | ~25–40 mm | 75/100 typical | eMMC standard; cap QC is the lottery |
| Seeed reTerminal DM (display + compute integrated) | ~35 mm | 75 | Good track record; CM4 + eMMC |
| Slim sandwich: branded portable monitor + flat-mount eMMC OPi behind | ~25–30 mm total | 75 via monitor | Strong if monitor + Pi both hardened |
| ~~Shadow-box frame~~ | **Eliminated** | — | Too thick for slim kitchen mount |

## Notes

- **Display selection landscape mapped** with realistic 24/7 expectations and prices.
- **Cheap no-name portables demoted** despite price overlap with branded portables — wrong tier for always-on.
- **Shadow-box frame eliminated** (too deep for kitchen wall).
- **Two-axis reliability framing established:** display QC is independent of Pi-side hardening; both must be solved.
- **eMMC > SD** locked as a constraint on Pi SKU selection.
- **Outstanding:** orientation (waiting on wireframe), final integrated-vs-sandwich pick, specific monitor model.
