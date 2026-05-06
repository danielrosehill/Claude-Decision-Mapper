# Turn 01 — Initial Brief

## User

I'd like to create a timezone clock and plan out the project from a DIY perspective. I've found that off-the-shelf assembled timezone clocks are really expensive. I previously bought a few standalone LCD displays, each a WiFi NTP, and discovered that getting the seconds to sync is impossible — they wind up out of sync, which looks terrible.

Learning from that, I want to create one display with the following times:
- Local: Israel time
- East: China
- West: Central Europe (Paris)
- Cork, Ireland (currently UTC+1)
- UTC
- US: Eastern, Central, Pacific

For components I'm envisioning roughly a 30×20 cm display — a generously sized LCD panel — showing the timezones, plus a footer dashboard with: temperature, AQI, Hebrew date, secular date, and a couple of prayer times.

My question: does it make most sense to drive this with an ESP32 or a Raspberry Pi? I have a spare 40×30 cm monitor that's HDMI-only I could use. I also have a number of 7-inch screens but they feel too small.

## Assistant

(Response was interrupted by the user at the next turn — only the opening recommendation was delivered.)

> **Recommendation: Raspberry Pi, not ESP32**
>
> For your feature set (9 timezones + weather + AQI + Hebrew date + zmanim/prayer times), Pi wins clearly. Reasons:
>
> **Pi (Pi 4 / Pi 5 / even Pi Zero 2 W)**
> - HDMI out → drives your existing 40×30 monit[interrupted]

## Notes

- **Spec drafted.** 9 timezones identified, dashboard scope set, candidate hardware listed.
- **Hard constraint surfaced from prior failure:** seconds must tick in lockstep across all rows. This carries forward as a non-negotiable.
- **Open question raised:** ESP32 vs Pi.
