# Turn 15 — Sourcing Keywords for Panel + Controller Kit

## User

Specific search keyword to find the HDMI + controller board pair?

## Assistant

Ranked search strings, kit-oriented first.

**Best — matched-kit searches (panel + board together):**
```
15.6 LCD panel HDMI driver board kit
15.6 inch 1920x1080 eDP panel with controller board
laptop screen to HDMI kit 15.6
DIY monitor kit 15.6 1080p
N156HCA HDMI driver board kit
B156HAN HDMI controller board kit
```
Searching by panel model number = highest precision.

**Second-best — controller alone, pair via order note:**
```
M.NT68676 controller board
RTD2660 LCD controller HDMI
universal LCD driver board eDP 30 pin
HDMI to eDP controller 1080p
```
Sellers of `M.NT68676.2A` / `RTD2660H` will pre-flash the EEPROM on request.

**Premium escape hatch:**
```
Waveshare 15.6 IPS HDMI display
```
~2× AliExpress price but ships ready-to-plug, controller pre-flashed, often with frame + VESA.

**Six match points to verify between panel + board:** resolution, interface (eDP/LVDS), pin count, backlight type, frame rate, panel model in the board's compatibility list.

**Magic phrase to send the seller:**
> "I have panel model `<exact part number>`. Can you flash the controller board for this panel before shipping?"

**Recommended workflow:**
1. Pick panel: search `15.6 IPS eDP 30 pin laptop screen 1080p`, choose model (e.g. `B156HAN02.1`)
2. Search `<panel model> HDMI driver board kit` for matched listings
3. Fallback: search `M.NT68676 HDMI VGA DVI 15.6`, message seller with panel model

## Notes

- **Sourcing process locked:** panel-first → matched-kit search → controller-only fallback. Removes the EEPROM-flash risk that was flagged in turn 14.
- **Common controller chipsets named** for future reference: M.NT68676, RTD2660, RTD2270, T.V56.031. Same chipset = same firmware family, same EEPROM-flash workflow.
- **Six-point compatibility checklist** captured: resolution / interface / pin count / backlight type / frame rate / panel-listed-in-compat. Reusable for any future LCD-panel sourcing.
- **Waveshare flagged as the +$40–60 painless option** if AliExpress kit hunt is frustrating. Worth the premium if the build is otherwise stalled on sourcing.
- No decision-space shift this turn — this is execution detail attached to turn 14's sourcing rule. Logged because the keyword vocabulary itself is reusable substrate.
