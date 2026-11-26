# Changelog

## 2.0.0 (2026-11-26)

- **New `Misc` Tab & Built-in Combat Timer (`/fw misc`):**
  - Added a standalone **Combat Timer** under the new top-level **Misc** tab (next to **Global Style**).
  - Added **Anchor Frame To** chooser so the Combat Timer can sit on screen or attach directly to any unit frame (**Player**, **Target**, **Focus**, **Pet**, **TargetTarget**, **Boss 1**) with anchor point and X/Y offset sliders.
  - Includes **Reset on Boss**, **Hide Out of Combat**, **Keep Time on Leave Combat**, custom **Prefix / Suffix** brackets, **Custom** or **Class Color**, and font/size/outline/shadow controls.
- **Profiles Tab — Import / Export & Per-Spec Dungeon/Raid Situations (`/fw profiles`):**
  - Added one-click **Profile Import & Export** with **Overwrite Current** and **Create New Profile** options.
  - Added **Per-Spec Profile Situations**: each specialization has its own tickable situation overrides for **Dungeon**, **Raid Normal/HC 25M**, **Raid Mythic**, and **Raid 40 Man**.
- **Totems & Aura Countdown Colors:**
  - Fixed Totems countdown text blinking yellow when leaving combat or updating active totems.
  - Buff, Debuff, and Totem countdown numbers smoothly shift from green to yellow (at 50% time remaining) and red (under 3 seconds) in both Retail and WoW Forever.
- **Blizzard-Style Options Window (`/fw`):**
  - Clean 5-tab layout (**Unit Frames**, **Colors**, **Profiles**, **Global Style**, **Misc**) + **Edit Mode** button.
  - 23 modular widgets organized under **BARS**, **AURAS**, **TEXTS**, and **ICONS & MISC** with live preview.
