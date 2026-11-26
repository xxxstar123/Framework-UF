# Changelog

## 2.0.0 (2026-11-26)

### Highlights
- **Top-Level `Misc` Tab & Native Combat Timer (`/fw misc`):**
  - Added an ExwindTools-style standalone **Combat Timer** powered by Blizzard's native C-side `C_DurationUtil.CreateDuration()` + `DurationTextBinding` + `CreateNumericRuleFormatter` (`div=60`, `mod=60`, `ElapsedDuration`) with zero Lua `OnUpdate` overhead in combat.
  - Added **Anchor Frame To** chooser allowing the Combat Timer to anchor to `Screen Center (UIParent)`, `Player`, `Target`, `Focus`, `Pet`, `TargetTarget`, or `Boss 1`, with full 9-point anchor, relative point, and X/Y offset sliders.
  - Includes `Reset on Boss` (`ENCOUNTER_START`), `Hide Out of Combat`, `Keep Time on Leave Combat`, custom `Prefix (Left)` / `Suffix (Right)`, `Custom` or `Class Color`, and full font/outline/size/shadow controls.
- **Profiles Tab — Import / Export & Per-Spec Profile Situations (`/fw profiles`):**
  - Added compressed **Profile Import & Export** (`!FW:<ver>:PROFILE:<name>!<payload>`) with **Overwrite Current** and **Create New** import modes.
  - Added **Per-Spec Profile Situations**: each specialization has its own situation overrides for **Dungeon**, **Raid Normal/HC 25M**, **Raid Mythic**, and **Raid 40 Man**, each with an individual on/off checkbox.
- **Totems & Aura Duration Text Colors:**
  - Fixed Totems duration text blinking yellow when transitioning between secret combat durations and readable out-of-combat cooldowns.
  - Added full support for `SetBreakpoints` + `SetTextFormat` on `DurationTextBinding` so duration color curves (green -> 50% yellow -> <3s red) bind reliably in combat on both Retail (12.x) and WoW Forever (1.60.x).
- **Refined 600px Blizzard-Native Options Window (`/fw`):**
  - Unified 5-tab top bar (`Unit Frames`, `Colors`, `Profiles`, `Global Style`, `Misc`) + `Edit Mode` button.
  - Categorized 23 unit-frame widgets under `BARS`, `AURAS`, `TEXTS`, and `ICONS & MISC` with collapsible drawer cards and live preview.
