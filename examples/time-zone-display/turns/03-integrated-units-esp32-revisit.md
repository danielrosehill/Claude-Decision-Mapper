# Turn 03 — Integrated Units & ESP32 Revisit

## User

Gotcha. So the "Pi on the back" part is where I find it gets ugly. Is there anything (or way to build) an integrated display + Pi unit? And if I didn't have Pis free, would ESP32 not be a cleaner fit? Please save the spec and responses in the repo so we document our decision-making process.

## Assistant

### Integrated display + compute options

**1. All-in-one boards (cleanest)** — SBC bonded to the panel, no "Pi on the back" silhouette:
- Seeed reTerminal (RK3399 + 5" IPS), CrowPanel / Elecrow HMI boards
- LattePanda / Khadas Mind-style x86 mini PCs behind a 10–13" portable monitor with a custom 3D-printed frame
- **Used Android tablet in kiosk mode** with Fully Kiosk Browser — cheapest integrated answer (~$50). Genuinely the lowest-effort, best-looking option for a clock dashboard.

### ESP32 — honest reassessment

For the *full* spec (9 timezones + weather + AQI + Hebrew date + zmanim, ~30×20 cm display), ESP32 is **not** cleaner:
- Display drive: ESP32 can do small SPI/parallel TFTs (≤4–7") via LVGL. Driving a 10"+ HDMI panel needs an HDMI controller board + an SBC — back to Pi-class.
- No browser. UI in LVGL/C or MicroPython — no HTML/CSS, no easy fonts, no flexbox. 9 rows of typography that look *good* is real work.
- APIs: HTTPS + JSON parse all hand-rolled. Hebcal/zmanim parsing on ESP32 = pain.
- Where ESP32 *does* win: small dedicated 3.5–7" TFT or e-paper clock with 2–3 zones and minimal extras. If scope shrinks to "just the 9 clocks on a 7-inch display, no dashboard," ESP32-S3 + a 7" RGB panel (Waveshare ESP32-S3 7", Makerfabs Matouch 7", LilyGo T-RGB) is genuinely clean.

**Conclusion:** ESP32 is cleaner *only* if scope shrinks. For the full spec, it's a downgrade.

### Ranking (at this turn)

1. Used Android tablet → Fully Kiosk → server URL
2. Integrated HMI board (CrowPanel/Elecrow 7–10")
3. Orange Pi + portable monitor in a 3D-printed/wood frame
4. ESP32 + 7" RGB panel — only with scope reduction

### Action taken

Saved planning doc: `Time-Zone-Display-0526/planning/01-spec-and-decisions.md`.

## Notes

- **Aesthetic constraint surfaced:** "Pi on the back" route is rejected for visual reasons.
- **ESP32 honestly compared and demoted** for the full spec.
- **Tablet introduced as the cleanest option** — but not yet accepted by user.
- **Decision artifact created** in the project repo.
