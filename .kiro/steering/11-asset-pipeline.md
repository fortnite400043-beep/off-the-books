---
inclusion: fileMatch
fileMatchPattern: "{blender,assets}/**"
---

# Asset Pipeline (Blender)

- Assets are generated with **Blender Python scripts** kept in `blender/`. Scripts are the source of truth, so any asset can be regenerated.
- Style: standard Roblox look with low to medium poly counts, clean flat or simple materials, and 2000s-era design.
- Follow Roblox import limits (mesh triangle limits, texture sizes) and check them against current Roblox docs.
- Export FBX in Roblox's scale and orientation. Name exported files after their in-game IDs from the definition modules.
- Character animations target Roblox's R15 rig.
- Kiro can't see renders unless it renders a preview headlessly or the user sends screenshots. Get visual sign-off before mass-producing assets.
- Audio is sourced by the user. Use only audio with clear rights, such as the Creator Store licensed library.
