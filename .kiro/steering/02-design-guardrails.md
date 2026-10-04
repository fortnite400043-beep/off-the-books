---
inclusion: always
---

# Design Guardrails

Check every design and implementation choice against these rules.

## Design pillars

1. **Smart beats grindy.** Success comes from planning, management, and reading the economy, not from clicking.
2. **Dirty money needs clean fronts.** Illegal operations earn faster, but laundering requires legit businesses. Both sides must stay necessary to each other.
3. **Macro management with physical presence.** Most control happens through the phone and laptop UI, but key actions (deals, inspections, assassinations, office life) happen in the world.
4. **A living, player-driven server economy.** Players' businesses, government staffing, elections, and laws all change the city each session.
5. **Friendly on the surface, dark underneath.** The tone mixes parody with seriousness: a bureaucratic, authoritarian state whose cheerful propaganda hides something darker.

## Monetization: no pay-to-win

- **Sell:** cosmetics (the main earner), capped convenience, extra character and background slots, a VIP subscription, private servers, crew perks, and campaign cosmetics.
- **Never sell:** in-game money (Studs or Cash), exclusive income sources, or anything that wins elections, raids, or competition.
- Convenience must be **capped** and **earnable or matched by free players**. The offline earnings boost has a hard cap; see DECISIONS.md.
- Price directly in Robux. There is no premium currency.
- Players can gift purchases to each other. There is no player-to-player trading.
- Design timers to be fair first. Never inflate a timer just to sell a skip.

## Roblox policy (verify against current Roblox guidelines when in doubt)

- **No illegal drugs** in any form. Contraband is limited to stolen cars and parts, counterfeit and bootleg goods, smuggled electronics, sanctioned goods, forged papers, and counterfeit Studs.
- **No gambling** of any kind, including simulated gambling and betting on street races.
- **Violence:** death is allowed, Roblox style, with **no blood or gore**.
- **All player-entered text** (company names, campaign messages, chat-like inputs) must go through Roblox's `TextService` filtering.
- Paid random items, if they're ever added, must show their odds.
- Real-world brands, agencies, and countries must never appear. Use the parody names from LORE.md.

## Fairness and anti-abuse

- Money must never be able to flow between alt accounts or between a player's own characters. Every money-transfer path (crews, loans, contracts, elections) needs level gates, caps, and server-side checks.
- New players are protected by a level-based shield and level-range matchmaking.
- The server is authoritative for everything. Never trust the client.
