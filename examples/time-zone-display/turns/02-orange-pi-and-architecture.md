# Turn 02 — Orange Pi & Architecture

## User

RPis are taken up — I forgot. But I have a couple of Orange Pis. What would the min spec be for this? Let's also plan a nice way to mount it, and consider two approaches if I wanted to have several displays: one provided on a local server with clients displaying, versus each running on the display itself.

## Assistant

### Min spec

For a fullscreen kiosk webpage (HTML/JS clock + a few API pulls every 10–15 min for weather/AQI/zmanim), almost nothing is needed:

- **CPU:** any quad-core ARM ≥1.0 GHz (Allwinner H3/H5/H6, RK3328, RK3566 — all fine)
- **RAM:** 512 MB works, 1 GB comfortable
- **GPU:** anything with Mali/VideoCore that can do 1080p HDMI
- **Storage:** 8 GB SD
- **OS:** Armbian (Debian) or Ubuntu server + minimal X/Wayland + Chromium kiosk, or DietPi

Realistically any Orange Pi Zero 2 / PC / Lite / 3 LTS / 5 — all overkill. Pick the one with HDMI out and best Armbian support. Time sync via chrony → sub-50ms drift, irrelevant since seconds render from a single JS clock anyway.

### The seconds-sync problem — solve it in software

Old setup failed because each LCD ran its own clock. Fix: **one JS `Date.now()` per page, all rows render from the same tick.** Even across multiple displays, if each browser syncs NTP every few minutes, drift between displays is <100 ms — visually identical.

### Two architectures

**A. Standalone (each display runs everything)** — self-contained Pi + panel, fetches its own APIs.
- Pros: zero infra, no SPOF, trivial to replicate
- Cons: N displays = N API keys; each does its own zmanim calc; updating means SSH to each
- Best if: 1–2 displays, set-and-forget

**B. Server + thin clients (recommended if ≥3 displays)** — central service caches data and serves the dashboard; Pis are dumb Chromium kiosks pointing at `http://server.lan/`. WebSocket can broadcast a sync tick so seconds align *exactly* across displays.
- Pros: one API key, one cache, edit-once-update-everywhere, exact cross-display sync, per-display URL params
- Cons: server must stay up — mitigate with client-side fallback to last cached state + local clock

**Recommendation: B, hosted on `ubuntuvm`** (already always-on per the LAN map).

### Mounting

For a 30×20 cm-ish display, three clean options:

1. **VESA panel + Pi on the back.** Buy a small portable HDMI monitor (most have 75×75 VESA). Velcro/3M-VHB the OPi to the back; some monitors power the Pi off USB-C. One HDMI cable, one power.
2. **Picture-frame build.** Bare LCD panel + LVDS/eDP→HDMI controller board (~$25 on AliExpress) inside a deep shadow-box frame. Looks like art; more work but nicest result.
3. **Waveshare/Elecrow HDMI display with built-in case.** 10.1"–11.6" IPS at 1920×1080, ~$80–120, comes ready to mount.

For 9 timezone rows + footer dashboard, **10–13" at 1920×1080 in landscape** is the sweet spot. The 40×30 cm spare is on the large side for a clock — fine if wall-mounted across a room; cramped on a desk.

### Suggested next step

Offered to scaffold the project structure (server/ client/ deploy/ planning/).

## Notes

- **Constraint added:** RPi unavailable → Orange Pi.
- **Architecture decided:** server + thin clients on `ubuntuvm`.
- **Sync problem solved (in principle):** single JS clock source, server-broadcast tick optional for exact cross-display alignment.
- **Three mounting candidates introduced** — not yet narrowed.
