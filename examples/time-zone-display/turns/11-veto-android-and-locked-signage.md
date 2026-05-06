# Turn 11 — Veto Android and Locked-Appliance Signage

## User

Let's limit the list to useful information. I definitely want to avoid Android. Raspberry Pi is good, as is Debian. I definitely don't like the Samsung commercial display ones, although I know they're popular. So we can narrow our ideal options to flash-it-yourself basic Linux/Debian or Raspberry Pi, which should narrow down the potential options significantly.

## Assistant

Confirmed. Two vetoes applied to Tier 2:

- **Android-default panel PCs vetoed.** Eliminates: RAYPODO, Geekland GK-TVR-POE-DS, Shining SH101KJ-T, Mimo Adapt-IQV, Geniatech TPC-K3 (Android default), Vantron Android SKUs, all cheap AliExpress Android wall tablets.
- **Locked-appliance signage displays vetoed.** Eliminates: Samsung Tizen Signage, LG webOS Signage, Philips Q-Line, BrightSign. Option D (LAN-served signage) from turn 09 effectively removed unless the receiving end is a generic Pi/Linux device.

Surviving Tier-2 candidates:

| Product | Compute | OS | Price |
|---|---|---|---|
| Chipsee CS10600RA4101P (Pi CM4 panel PC, 10.1") | Pi CM4 | Pi OS | ~$330–400 |
| Chipsee CM5 panel PC (7" / 10.1") | Pi CM5 | Pi OS | ~$350–450 |
| EDATEC Pi CM4 panel PCs | Pi CM4 | Pi OS | ~$300–400 |
| Waveshare Pi CM4 industrial panels | Pi CM4 | Pi OS | ~$250–350 |
| Chipsee Rockchip panel PCs ordered with their Debian image | RK3568/RK3576 | Debian (vendor) | ~$450–600 |

Front-runner unchanged: **Chipsee Pi CM4/CM5 10.1" panel PC**. Pi-native, vendor-supported Pi OS, single VESA enclosure.

## Notes

- **Two hard vetoes added to Tier 2:** Android (across all sub-tiers) and locked-appliance signage OSes (Tizen/webOS/Q-Line/BrightSign).
- **Decision space significantly collapsed.** Tier C-low (Android wall tablets) eliminated entirely. Tier D (LAN-served via commercial signage) eliminated. Surviving paths: Pi CM4/CM5 panel PCs, or Rockchip panel PCs sold with vendor Debian.
- **Tier-2 candidate list reduced from ~12 products to ~5.** Pi-CM family is the dominant cluster.
- **Implicit OS preference now explicit:** Pi OS or Debian, flashable, vendor-supported BSP. Not Android-with-kiosk-launcher, not appliance OS pointed at a URL.
- Front-runner (Chipsee Pi CM4/CM5 10.1") survives both vetoes — prior selection is reinforced, not displaced.
- Outstanding: lock SKU, decide CM4 vs CM5, decide 7" vs 10.1".
