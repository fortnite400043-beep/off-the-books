---
inclusion: always
---

# Project Context: Off the Books

**Off the Books** is a competitive multiplayer Roblox business-management game. Players share a server-city, **New Studsworth** (capital of the Free Republic of Studmark), and build empires of legit businesses and hidden illegal operations. Separate government careers (police, detectives, revenue agents, federal agents) and elected political offices act as counterweights.

- **Audience:** ages 12–25. Deep, strategic, macro-level management, not a simple tycoon.
- **Setting:** the 2000s. Standard Roblox art style: neither realistic nor very cartoony.
- **Platforms:** PC, mobile, and console, all fully supported from day one.
- **Team:** one human director (the user) plus Kiro. Kiro produces the code, UI, Blender-scripted models and animations, and docs. The user sources audio.

## Source of truth

Read these before doing design or implementation work. They override anything you remember or assume.

| File | Purpose |
|---|---|
| `docs/DECISIONS.md` | Every confirmed design decision. **Highest authority.** |
| `docs/OPEN_QUESTIONS.md` | Undecided items. Never resolve these yourself; ask the user. |
| `docs/SESSION_LOG.md` | Handoff log between sessions. Read the latest entry first. |
| `docs/GDD.md` | Game design document (system-level design) |
| `docs/LORE.md` | Lore bible: world, factions, characters, districts, brands |
| `docs/ECONOMY.md` | Numbers, formulas, and balancing |
| `docs/ARCHITECTURE.md` | Code skeleton, module layout, data schemas |
| `docs/ROADMAP.md` | Build order from prototype to launch |
| `docs/systems/*.md` | Detailed per-system specs |

Some of these files may not exist yet. Check `docs/SESSION_LOG.md` for current progress.

## Core principle

**The prototype is the permanent skeleton.** Everything built must be extended later, never rewritten. Favor data-driven definitions, clear module boundaries, and stable interfaces over quick hacks.
