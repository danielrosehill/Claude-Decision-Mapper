# Turn 17 — Open-Frame Industrial Monitors

## User

For off-the-shelf monitors at this size or smaller, with VESA mount — is there such a thing as a finished display actually built or intended to be run in kiosk mode?

## Assistant

Yes. Real product category, niche enough that normal monitor searches miss it. Two sub-categories:

**1. Open-frame industrial monitors** — bare-bones finished display, controller + panel + minimal bezel + VESA, HDMI in, DC barrel jack, designed for embedding in kiosks/machines/signage. 24/7 rated.

| Brand | Sizes | 15.6" price | Notes |
|---|---|---|---|
| Beetronics (NL) | 7"–17" | ~$350 | Clean, well-regarded, optional touch |
| Faytech (DE/CN) | 7"–24" | ~$300 | Cheaper, IP65 front options |
| Iiyama ProLite TF | 10.1", 15.6" | ~$400 | Touch-first, rugged |
| Lilliput | 7"–17" | ~$200–300 | Cheaper, in-vehicle/embedded heritage |
| AOpen DT | 10", 15" | ~$500 | Signage-grade, 24/7 |

**2. Kiosk touchscreen monitors** — same form factor with capacitive touch, retail/POS oriented:

| Brand | Models | Sizes | Price |
|---|---|---|---|
| Elo TouchSystems | 1002L, 1502L | 10.1", 15.6" | $300–600 |
| Mimo Monitors | Vue HDX-1080C | 10.1" | $450–550 |
| GVision | K-series | 10"–22" | $300–700 |

**Not in this category:** sub-15" consumer monitors with VESA (don't exist), Samsung/LG/Philips small signage (locked to Tizen/Android/webOS — vetoed turn 11), 15–17" "regular" monitors (tiny market, mostly POS spares).

**Comparison vs. earlier tiers:**

| Approach | Cost | 24/7 rated | Look | Hassle |
|---|---|---|---|---|
| Portable monitor + Pi case + VHB | ~$280 | Not officially | OK | Low |
| **Open-frame industrial + Pi case + VHB** | **~$400** | **Yes** | **Best** | **Lowest** |
| Tier-C integrated panel PC | ~$650 | Yes | Best | None (if delivered) |

Open-frame industrial is the honest sweet spot — ~$120 over portable monitor for actual 24/7 rating, cleaner aesthetics (no kickstand / USB-C bulge), HDMI + DC barrel jack instead of USB-C PD dance.

**Pick:** Beetronics 15.6" (~$350). Faytech as cheaper alternative. Elo 1502L (~$550) for "definitely won't fail in 5 years," accepting paying for unused touch.

## Notes

- **New product category surfaced late: open-frame industrial monitors.** Closest off-the-shelf match to the original "finished kiosk display" intent. Should have appeared earlier in the discovery process — the "panel PC" / "portable monitor" / "bare panel" search frames missed it.
- **Front-runner promoted: Beetronics 15.6" open-frame (~$350) + Pi-in-aluminium-case-on-back.** Total ~$400 for a 24/7-rated build with off-the-shelf parts. Replaces the prior portable-monitor pick (Lenovo M15 / Asus MB16ACE) for the v2 build.
- **Decision rule clarified:** when the use case is *kiosk*, search the kiosk product channel (Beetronics, Faytech, Iiyama TF, Lilliput, Elo) — not the consumer-monitor or laptop-display channels. Different distribution, different pricing, different ratings.
- **Cost shape changes:** ~$400 total now beats Tier-C integrated ($550–650) on price *and* matches it on 24/7 rating. Tier-C's only remaining advantage is "single-enclosure" which is a small aesthetic gap given a clean aluminium Pi case + VHB-mounted on a flat industrial-monitor back.
- **Vendor list captured for future reference:** Beetronics, Faytech, Iiyama ProLite TF, Lilliput, AOpen DT, Elo, Mimo, GVision. Reusable substrate for any "small kiosk display" sourcing.
- Tier-C (Chipsee Pi CM4/CM5 panel PC) is now demoted to "buy if you specifically want single-enclosure aesthetic and don't mind +$250."
