# 📦 OFFMETA Compatibility Bundle — `qb-multicharacter` + `illenium-appearance`

This repo is a **ready-to-drop bundle** containing two resources that were adjusted to work nicely together:

- 🧍 **`qb-multicharacter`** (QBCore) — **patched** so the *character selection preview* correctly applies outfits/appearance using **illenium-appearance**
- 👕 **`illenium-appearance`** — **patched** to optionally spawn a **shop NPC + 3D text prompt** at clothing/barber/tattoo/surgeon stores (zone mode)

> ✅ Goal: make the setup cleaner, avoid “wrong clothes” on multichar preview, and provide a more immersive shop experience.

---

## ✨ What was changed

### ✅ `qb-multicharacter` (illenium-appearance preview fix)
- 🎭 Applies saved appearance to the **preview ped** using:
  - `exports['illenium-appearance']:setPedAppearance(...)`
- 🧠 Fixes model handling so it works whether the stored model is:
  - a **number hash** *or* a **string model name**
- 🧼 Small safety/cleanup around ped initialization

➡️ Full notes: [`qb-multicharacter/OFFMETA_CHANGES.md`](qb-multicharacter/OFFMETA_CHANGES.md)

### ✅ `illenium-appearance` (shop NPC + 3D text prompt)
- 🧍 Spawns shop peds only when **UseTarget = false** (zone mode)
- 🏷️ Draws **3D title + hint text** over the NPC (configurable per shop type)
- 🚀 Includes performance guards (spawn distance / draw distance)

➡️ Full notes: [`illenium-appearance/OFFMETA_CHANGES.md`](illenium-appearance/OFFMETA_CHANGES.md)

---

## 📥 Installation

1) Copy both folders into your server resources:
- `illenium-appearance`
- `qb-multicharacter`

2) Ensure the start order in `server.cfg` (important because `qb-multicharacter` uses exports from `illenium-appearance`):

```cfg
ensure illenium-appearance
ensure qb-multicharacter
```

3) If you want the **shop NPC + 3D text** feature:
- In `illenium-appearance/shared/config.lua`:
  - set `Config.UseTarget = false`
  - keep `Config.ShopPed3D.enabled = true` (already enabled in this bundle)

---

## ⚙️ Notes & Tips

- If you use **qb-target** for shops, keep `Config.UseTarget = true` and the 3D NPC/text feature will **not** run (by design).
- The shop ped + text is configurable per shop type under `Config.ShopPed3D.types`.

---

## 🙏 Credits

- **`qb-multicharacter`**: QBCore Framework contributors (GPL-3.0)
- **`illenium-appearance`**: iLLeniumStudios / snakewiz (MIT)
- Compatibility & immersion improvements packaged by **OFFMETA**

---

## 🪪 Licensing

This repository is an **aggregate/bundle**:
- `qb-multicharacter` remains under **GPL-3.0** (see `qb-multicharacter/LICENSE`)
- `illenium-appearance` remains under **MIT** (see `illenium-appearance/LICENSE`)

No license terms are changed by this bundle.
