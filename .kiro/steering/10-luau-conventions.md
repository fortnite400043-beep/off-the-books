---
inclusion: fileMatch
fileMatchPattern: "**/*.{luau,lua,json,toml}"
---

# Luau and Tooling Conventions

`docs/ARCHITECTURE.md` is the detailed authority once it exists. These are the baseline rules it must follow.

## Toolchain

| Tool | Role |
|---|---|
| Rokit | Pins tool versions (`rokit.toml`) |
| Rojo | Syncs the filesystem to Studio (`default.project.json`) |
| Wally | Packages (`wally.toml`) |
| Lune | Tests and tooling scripts run outside Studio |
| Fusion | All UI |
| ProfileStore | Player data persistence with session locking |
| StyLua | Formatting |
| Selene | Linting |

Pin exact versions and verify the current stable releases when setting up. Don't guess version numbers.

## Code rules

- Every file starts with `--!strict`, and all public APIs are typed.
- **Data-driven content:** businesses, employees, traits, laws, upgrades, items, and so on are defined in shared definition modules. Systems read those definitions. Adding a new business should mean adding data plus its unique module, never editing core systems.
- **Logic separate from Roblox:** economy math, raid resolution, evidence scoring, elections, and similar calculations live in pure modules with no Instance or service access, so Lune can test them.
- **Server-authoritative:** clients send *intents*. The server validates every remote call (type, range, ownership, rate limit, and permission), then acts.
- **Single entry points:** one server bootstrap and one client bootstrap load services and controllers in a defined order. There are no stray Scripts.
- Use one networking layer, with no ad-hoc RemoteEvents scattered around.
- **Save data:** keep a versioned schema with migrations from day one. Every save format change gets a migration.
- **Analytics:** every meaningful player action goes through a single analytics module.
- Avoid deprecated APIs (for example, use `task.wait`, not `wait`).
- Naming: PascalCase for modules, types, and services; camelCase for locals and functions; UPPER_SNAKE for constants.

## Tests

- Run Lune tests for all pure logic before committing: `lune run tests`, or whatever ARCHITECTURE.md defines.
- Every economy formula and state machine gets tests, including edge cases.

## UI

- Use Fusion components only. Build a shared UI kit (theme tokens, typography, buttons, panels, lists).
- Every screen must work on touch, mouse and keyboard, and gamepad. Account for mobile safe areas and minimum touch target sizes.
- The visual language is 2000s devices: a slider phone that upgrades through models, a chunky laptop, and pixel-LED signage.
