<div align="center">

<img src="https://raw.githubusercontent.com/xxxstar123/Framework-Unitframes/main/media/Framework-icon-512.png" alt="Framework Unitframes Crest" width="128">

# Framework Unitframes

**Standalone, combat-safe unit frames for Player, Target, TargetTarget, Focus, Pet and Boss 1–5 — with native Blizzard aura containers, per-spec situation profiles, and a zero-overhead C-side Combat Timer.**

For every class and specialization · Retail (12.x) and WoW Forever (1.60.x) · *Inspired by CUF*

[![Download on CurseForge](https://img.shields.io/badge/download-CurseForge-F16436?logo=curseforge&logoColor=white)](https://www.curseforge.com/wow/addons/framework-unitframes)
[![Download on Wago](https://img.shields.io/badge/download-Wago.io-c1272d?logo=wago&logoColor=white)](https://addons.wago.io/addons/framework-unitframes)
[![Discord](https://img.shields.io/badge/Discord-join-5865F2?logo=discord&logoColor=white)](https://discord.gg/j3TH89X9wZ)
[![Donate with PayPal](https://img.shields.io/badge/donate-PayPal-00457C?logo=paypal&logoColor=white)](https://www.paypal.com/donate/?business=mywowace%40proton.me&no_recurring=0&item_name=Support+Framework+Unitframes&currency_code=USD)

![Framework Unitframes Complete Combat HUD](https://raw.githubusercontent.com/xxxstar123/Framework-Unitframes/main/media/diagrams/01-hero-hud.png)

</div>

---

## Why Framework Unitframes?

- **100% Standalone.** Requires no external unit-frame or raid-frame addon. All textures, fonts, dispel detectors, glow engines, and aura containers are self-contained inside `Framework`.
- **Combat-Safe Native Aura & Totem Engine (Midnight 12.x & Forever 1.60.x).** Traditional Lua aura scanners fail or taint when `UnitAura` and `GetTotemInfo` return secret values in combat. Framework binds directly to Blizzard's native `AuraContainer` and `C_DurationUtil.CreateDurationTextBinding()`, so your Buffs, Debuffs, Dispels, Totems, and duration threshold colors keep updating in the middle of boss fights with **zero Lua `OnUpdate` overhead**.
- **23 Modular Widgets per Unit.** Every bar, absorb overlay, text tag, aura lane, portrait, and status icon can be enabled, styled, anchored, or copied across units independently.
- **Per-Spec Profiles + 4 Tickable Situation Overrides.** Each specialization of your class chooses its own default profile plus individual on/off situation overrides for **Dungeon (5-Man / M+)**, **Raid Normal/Heroic (25M)**, **Raid Mythic (20M)**, and **Raid 40 Man**.
- **Built-in Native Combat Timer (`/fw misc`).** An ExwindTools-style elapsed fight timer driven by Blizzard's C-side `DurationTextBinding` + `CreateNumericRuleFormatter` (`div=60`, `mod=60`) — anchor it to the screen or directly to any unit frame (`Player`, `Target`, `Focus`, `Pet`, `TargetTarget`, `Boss 1`).
- **Blizzard-Native Options Window (`/fw`).** Clean 600px tabbed interface (`Unit Frames`, `Colors`, `Profiles`, `Global Style`, `Misc`) built with game-native Blizzard frames, gold headers, inset cards, sliders, and searchable dropdowns.
- **Pixel-Perfect at Any UI Scale.** Every border, bar, icon edge, and gap snaps to whole physical screen pixels.
- **Seamless First-Run Migration & Clique Support.** All 15 unit buttons register automatically with `ClickCastFrames` (Clique and native click-cast bindings). On first login, Framework can automatically import your existing unit-frame layouts if present.

---

## Architecture & Visual Tour

### 1. Anatomy of a Framework Unit Frame (23 Modular Widgets)

Every unit frame is composed of four modular widget groups — **Bars**, **Auras**, **Texts**, and **Icons & Misc** — all configurable with live preview in `/fw`:

![Anatomy of a Framework Unit Frame](https://raw.githubusercontent.com/xxxstar123/Framework-Unitframes/main/media/diagrams/02-unitframe-anatomy.png)

| Category | Widgets Included | Highlights |
| :--- | :--- | :--- |
| **Bars (8)** | `Health Bar`, `Power Bar`, `Alt Power Bar`, `Cast Bar`, `Class Bar`, `Shield Bar`, `Heal Prediction`, `Heal Absorb` | Class / Reaction / Custom / Threshold gradient colors, loss backdrops, striped shield overlays, overabsorb glow, detachable Cast Bar & Power Bar with empower stage pips and latency zone. |
| **Auras (4)** | `Buffs`, `Debuffs`, `Dispels`, `Totems` | Dual-lane native `AuraContainer` engine, one-click curated Blacklist presets (*My Defensives*, *Big Defensives*, *External Defensives*, *Utility*), Maximum Duration slider, Clock or Vertical cooldown swipe, Dispel border & highlight. |
| **Texts (5)** | `Name Text`, `Health Text`, `Power Text`, `Level Text`, `Custom Text` | Flexible format tags (`[name]`, `[hp:short]`, `[hp:pct]`, `[shield]`, `[classification]`, `[raidgroup]`), Cyrillic transliteration option, full font/outline/shadow control. |
| **Icons & Misc (6+)** | `Portrait`, `Raid Icon`, `Role Icon`, `Leader Icon`, `Combat Icon`, `Ready Check`, `Resting Icon`, `Faction Icon`, `Pet Happiness` (Forever), `Highlight` | 2D / 3D / Class Icon portraits with Square or Circle mask + ring, 9 Role Icon styles, animated 42-frame Resting flipbook, PvP/Honor Faction crests, and Forever Hunter Pet Happiness faces. |

---

### 2. Native Combat-Safe Aura Engine & Duration Threshold Colors

Out of combat, Framework compiles your aura filters, curated presets, maximum duration cap, and sort order. In combat, Blizzard's C++ `AuraContainer` and `DurationTextBinding` take over seamlessly — formatting remaining time and evaluating your **50% Yellow Warning** and **< 3.0s Red Urgent** color curves in native code without touching secret values in Lua.

![Native Aura Engine & Duration Threshold Colors](https://raw.githubusercontent.com/xxxstar123/Framework-Unitframes/main/media/diagrams/03-combat-safe-auras.png)

---

### 3. Per-Spec Profile Situations, Import / Export & Native Combat Timer

Open `/fw profiles` to assign a profile to each specialization of your class, tick any of the **4 instance situations** (*Dungeon*, *Raid Normal/HC 25M*, *Raid Mythic*, *Raid 40 Man*) to auto-switch when entering instances, or share compressed `!FW:<ver>:PROFILE:<name>!` strings with **Overwrite Current** or **Create New Profile**.

Open `/fw misc` (the **Misc** tab right next to **Global Style**) to configure the standalone **Combat Timer**, including **Anchor Frame To** (*Screen Center*, *Player*, *Target*, *Focus*, *Pet*, *TargetTarget*, *Boss 1*), *Reset on Boss* (`ENCOUNTER_START`), *Hide Out of Combat*, and *Keep Time on Leave Combat*.

![Per-Spec Profile Situations & Native Combat Timer](https://raw.githubusercontent.com/xxxstar123/Framework-Unitframes/main/media/diagrams/04-profiles-and-combat-timer.png)

---

### 4. Edit Mode (`/fw edit`), Snap Grid & Show / Hide Fader Rules

Press **Edit Mode** in the top-right header of `/fw` (or type `/fw edit`) to unlock all unit frames and detached widgets:

- **Color-Coded Selection Overlays:** **Blue** boxes for Unit Frames (`Player`, `Target`, `TargetTarget`, `Focus`, `Pet`, `Boss 1–5`) and **Gold** boxes for detached widgets (`Cast Bar`, `Power Bar`, `Class Bar`).
- **Pixel-Accurate Positioning:** Drag with grid snap lines, or click any frame to open its coordinates popup and nudge **1px** with the **Arrow Keys** (**Shift + Arrow** for **10px**).
- **13 Fader Rules & 8 Visibility Rules per Unit:** Exclusive *Show* / *Hide* ticks per condition (*In Combat*, *Has Target*, *Player Damaged*, *Casting*, *Dungeon*, *Raid*, *Arena*, *Battleground*, *Resting*, *Mounted*, *Vehicle*, *Solo*, *Group*) plus **Mouse Hover Override** and custom macro driver strings.

![Edit Mode Overlay, Snap Grid & Show / Hide Rules](https://raw.githubusercontent.com/xxxstar123/Framework-Unitframes/main/media/diagrams/05-editmode-and-rules.png)

---

## Slash Commands

| Command | Action |
| :--- | :--- |
| `/fw` or `/framework` | Open or close the Framework Unitframes options window |
| `/fw edit` or `/fw editmode` | Toggle interactive Edit Mode (drag frames, grid snap, arrow-key nudge) |
| `/fw profiles` | Open directly to the **Profiles** tab (Spec profiles, Situations, Import/Export, Backups) |
| `/fw appearance` | Open directly to the **Global Style** tab (Bar textures, Fonts, Cooldown style, Duration colors) |
| `/fw colors` | Open directly to the **Colors** tab (Health, Power, Cast Bar, Shield, Aura & Dispel palettes) |
| `/fw misc` | Open directly to the **Misc** tab (Standalone Combat Timer & Unitframe Anchor chooser) |
| `/fw test` | Toggle test/preview mode on unit frames |
| `/fw tags` | Show the custom text tag reference tooltip |
| `/fw restore automatic\|manual` | Restore the latest automatic or manual database backup |

---

## Installation

1. Download **Framework Unitframes** from [CurseForge](https://www.curseforge.com/wow/addons/framework-unitframes) or [Wago Addons](https://addons.wago.io/addons/framework-unitframes).
2. If installing manually, extract the `Framework` folder into:
   - **Retail:** `World of Warcraft\_retail_\Interface\AddOns\Framework`
   - **WoW Forever:** `World of Warcraft\_forever_\Interface\AddOns\Framework`
3. Type `/fw` in-game to open the options window, or `/fw edit` to position your frames.

---

## Feedback, Bug Reports & Support

- **Discord:** [Join the community Discord](https://discord.gg/j3TH89X9wZ)
- **Bug Reports:** [Open a Bug Report](https://github.com/xxxstar123/Framework-Unitframes/issues/new?template=bug_report.yml)
- **Feature Requests:** [Suggest a Feature](https://github.com/xxxstar123/Framework-Unitframes/issues/new?template=feature_request.yml)
- **Support the Project:** Framework Unitframes is free. If you enjoy using it, you can [support development via PayPal](https://www.paypal.com/donate/?business=mywowace%40proton.me&no_recurring=0&item_name=Support+Framework+Unitframes&currency_code=USD).

---

## License

Copyright (c) 2026 **xxxstar123**. All rights reserved — free to download and use in World of Warcraft; no redistribution, modification, or AI use of the code without written permission (see [LICENSE](LICENSE) and [AGENTS.md](AGENTS.md)). Inspired by CUF.

*World of Warcraft is a trademark of Blizzard Entertainment, Inc. Framework Unitframes is not affiliated with or endorsed by Blizzard Entertainment.*
