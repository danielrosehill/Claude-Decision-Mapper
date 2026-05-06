# Turn 07 — Reliability, Slim, VESA

## User

Ideally we want something running 24/7. Nice light/viewing settings are fine but for something going up in a kitchen, the main thing is **reliability** — not best viewing experience. Reliability is the top criterion. Second criterion: **VESA mount** (will be wall-mounted). Landscape vs portrait TBD when wireframes are finished.

## Assistant

### Constraint hierarchy now

1. 24/7 reliability — top
2. Slim form factor (kitchen wall)
3. VESA mount — required
4. Panel quality — secondary

### Reliability hardening (applies to all paths)

- **eMMC over SD card.** SD cards are the #1 failure mode in always-on Pi kiosks (Chromium cache + log writes wear them out in months). Industrial panel PCs and reTerminal ship eMMC; bare OPi typically doesn't unless you pick the right SKU (e.g. Orange Pi 3 LTS).
- **Read-only root filesystem.** Overlayfs on Armbian. Eliminates SD wear and survives power loss without corruption. Standard kiosk deployment pattern.
- **Solid PSU.** Cheap USB chargers cause most "random 3am reboot" bugs. Use a real 5V/3A supply with a proper connector, not the freebie in the box.
- **Hardware watchdog.** `systemd-watchdog` against the SoC's hardware timer. If Chromium hangs or kernel locks, board reboots itself. Trivially configured.
- **systemd `Restart=always`** on the Chromium kiosk unit, with network-online dependency.
- **Thermal headroom.** Already addressed in turn 05; more important under 24/7. Sustained 70°C fine; 80°C+ ages capacitors fast.
- **Capacitor quality.** Cheap industrial RK panel PCs sometimes die at 6–18 months. Read user reports before buying. reTerminal-class better track record.

### Path table (revised)

| Path | Slim | VESA | Reliability outlook |
|---|---|---|---|
| Industrial RK3566 panel PC | Yes (~25–40 mm) | 75/100 VESA usual | Lottery on caps; eMMC standard |
| Seeed reTerminal DM | Medium (~35 mm) | 75 VESA | Good track record; eMMC |
| Slim monitor-sandwich (portable HDMI + flat-mount OPi 3 LTS) | ~25–30 mm | 75 VESA via monitor | Strong if eMMC + read-only rootfs |
| ~~Shadow-box frame~~ | **No — eliminated** | — | — |

### Updated lean

Slim monitor-sandwich with **eMMC-variant Orange Pi** flat-mounted in a 3D-printed VESA-compatible case, ~25–30 mm depth, ~$150. Reliability hardening (read-only rootfs + watchdog + good PSU) is trivial.

Industrial RK3566 panel PC is the "buy preassembled" alternative if vendor QC concerns can be addressed via reviews.

## Notes

- **Constraint set tightened.** Reliability promoted to top; viewing experience demoted.
- **One option eliminated** (shadow-box frame — too thick for slim kitchen mount).
- **New hardware preference surfaced:** eMMC > SD card. This filters Orange Pi SKUs.
- **Reliability hardening pattern documented** — applies regardless of mounting path.
- **Outstanding:** orientation (waiting on wireframe), final mounting path (panel PC vs sandwich).
