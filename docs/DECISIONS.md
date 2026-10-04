# Decision Log

This is the authoritative record of design decisions. It overrides all other docs. If a decision changes, update the entry, add "(superseded YYYY-MM-DD)" to the old text, and record the new version.

**Status key**
- ✅ **Confirmed:** the user explicitly stated or approved it.
- 🟡 **Accepted proposal:** Kiro proposed it and the user agreed or didn't object. It's safe to build on, but mention it if it becomes significant.

Undecided items live in `OPEN_QUESTIONS.md`.

The source for everything below is the original design conversation, held before 2026-10-04.

---

## 1. Identity and scope

- ✅ **Title:** *Off the Books*
- ✅ **Setting:** the capital city **New Studsworth**, in the **Free Republic of Studmark**, in the **2000s**.
- ✅ **Art style:** standard Roblox style; not realistic and not very cartoony.
- ✅ **Audience:** ages 12–25. A deep game where players must be engaged and smart to succeed. Not a simple linear progression.
- ✅ **Platforms:** PC, mobile, and console, all fully supported from day one.
- ✅ **Team:** a solo human director. Kiro creates the code, UI kit, models, animations, and docs. Sound assets and niche items are sourced by the user.
- ✅ **Tech:** Rojo, Lune, Fusion, Blender, plus Rokit, Wally, ProfileStore, strict Luau, StyLua, and Selene. The user develops on **Windows** and already has Studio and Rojo installed.
- ✅ **Analytics** from the start.
- ✅ **Automated tests** with Lune.
- ✅ The prototype must be the permanent skeleton: it gets added to, never redone.

## 2. Servers, map, and plots

- ✅ Multiplayer: many players compete in one server-city.
- 🟡 About **20 players per server**.
- 🟡 **Performance architecture:**
  - Business simulation is calculated as numbers on the server.
  - Ambient NPCs (customers, staff) are drawn on each player's device only.
  - Raid NPCs are real server-side characters, with capped numbers per raid.
  - Building interiors load on demand.
  - The map uses StreamingEnabled.
- 🟡 **Districts:** Copperfield (suburbs, starter area), The Rust Yards (industrial), Gilded Row (downtown), Saltmouth Docks (late game), and Vault Hill (government district; players can't build there). Future districts: Ashtown (Old Studsworth ruins) and Embassy Row.
- 🟡 About 60–80 city plots, split into size classes.
- ✅ **Players own buildings, not plot locations.** Each building has a size class: **Small, Medium, Large, Extra Large, or Gigantic**. Owned buildings load into a free plot of matching size and district when the player joins.
- ✅ Every player has a **base plot**. Unowned city plots appear as closed-off buildings for sale and/or construction sites. Buying one triggers a construction phase.

## 3. Economy

- ✅ **Dynamic, player-driven economy for each server.** For example, a player-owned logistics business lowers prices server-wide.
- ✅ **Government staffing modifier, per server:** more government players online makes it harder for criminals to avoid getting caught.
- ✅ **Currencies:** **Studs (S$)** are clean money. **Cash** is dirty, untraceable money. Laundering converts Cash into Studs. Names stay Roblox-friendly to avoid moderation problems.
- ✅ **Offline earnings:** 10% base rate. Game passes increase it (the cap is an open question). Heat slowly decreases while offline.
- ✅ Everything saves permanently. There are per-session events, sales, and deals.
- ✅ **Finance systems:** loans, credit score, taxes, insurance, real estate rental income. **Investing in other players' companies is not allowed.**
- ✅ **Endgame private bank:** players can lend to other players with interest. 🟡 Abuse limits: loan size tied to the borrower's level, real penalties for not repaying, NPC debt collectors.
- ✅ **Money sinks** in the mid-to-late game, including luxury status purchases.
- ✅ **Server events:** recessions, crackdowns, shortages, holidays, storms, and similar. Frequency is still open.
- ✅ **Player-to-player supply contracts**, for example a warehouse supplying a supermarket at a negotiated rate.
- ✅ **Two sets of books:** businesses keep accounting records that can be "cooked" to hide laundering. The IRS investigates them.

## 4. Businesses

- ✅ **Two core frameworks:** one for legit businesses and one for illegal operations. Each business type also has its own unique module on top of its core.
- ✅ Reputation, reviews, marketing, and price competition between nearby businesses.
- ✅ Each business can be played at two levels: macro management, or a single NPC manager running it while the player focuses on expansion and planning.
- ✅ **Tier unlocks** require a combination of player level, reputation, licenses, and prerequisite businesses.
- ✅ **Licenses and permits** apply to *some* businesses, not all. The Forgery Bureau sells fakes.
- ✅ **No drugs and no gambling.** Illegal product types: stolen cars and parts, counterfeit and bootleg goods, smuggled electronics, sanctioned goods, forged papers, counterfeit Studs, and street racing (without betting).
- ✅ **Turf:** gangs gain district control and turf bonuses.
- 🟡 **Business roster:**

**Legit businesses**

| Tier | Businesses |
|---|---|
| T1 | Car Wash (S, starter), Laundromat (S), Food Truck (S, mobile) |
| T2 | Convenience Store (S), Mechanic Shop (M), Diner (M), Pawn Shop (S) |
| T3 | Supermarket (L), Logistics Warehouse (L), Taxi Company (M), Construction Company (L) |
| T4 | Nightclub (L), Car Dealership (L), Hotel (XL), Security Firm (M), Real Estate Agency (M) |
| T5 | Radio Station / Media Co. (L), Shipping Terminal (G), Gold Refinery (G), Private Bank (XL), Corporate HQ (G) |

**Illegal operations** (each needs a front business)

| Tier | Operation | Front |
|---|---|---|
| T1 | Back-Room Fence | Car Wash or Pawn Shop |
| T2 | Chop Shop | Mechanic |
| T2 | Bootleg Goods Workshop | Laundromat or Convenience Store |
| T3 | Forgery Bureau | Real Estate or Pawn Shop |
| T3 | Smuggling Ring | Logistics Warehouse |
| T4 | Counterfeit Studs Press | Nightclub or Hotel |
| T4 | Street Racing Ring | Car Dealership |
| T5 | Embargo Running | Shipping Terminal |
| T5 | Unlicensed Gold Tunnel | Gold Refinery |

## 5. Employees, gangs, and corporate

- ✅ **Employees are unique, named individuals.** Stats: skill, wage, morale, loyalty, and stress, plus traits.
- ✅ Pay affects how fast employees level up and how likely they are to snitch.
- ✅ **Benefits:** health insurance packages protect employees from harm in raids and from workplace injuries.
- ✅ **Death is permanent.** 🟡 It costs a compensation payment and lowers morale.
- ✅ **No poaching** of other players' employees.
- ✅ Strikes and walkouts happen when pay or morale is low.
- ✅ Employees can be trained and promoted, for example from cashier to manager.
- ✅ **Gang members** are a separate system that uses the same stat ideas, plus unique traits.
- ✅ **Corporate structure:** CEO (the player), COO, CFO, HR Director, Security Chief, and General Managers. Corporate staff and HR investigate problems for you. Corporate staff **cannot betray you, but can make mistakes**. The structure scales up like every other part of a business.

## 6. Raids

- ✅ Rival raids are NPC against NPC, commanded by players. **Owners and attackers only give orders; they never fight in person during raids.**
- ✅ Players can only raid **online** players in their server, within a level range. Offline players are safe.
- ✅ Players can raid **AI businesses**, which covers low-population and solo servers.
- ✅ **A level-based shield** protects new players.
- ✅ If someone leaves in the middle of a raid, it automatically counts as a failed raid (see OPEN_QUESTIONS for whether this applies to defenders too).
- ✅ **What each type of raid can do:**
  - **Rival criminals** can only hit illegal operations. They can steal inventory, make staff quit, and shut the business down for repairs if the damage is severe. **Rivals can never raid legit (civilian) businesses**, but they can tip off the authorities.
  - **Police and detectives** hit illegal operations. The result is a shutdown and lost stock.
  - **The IRS is the only agency that can act against legit businesses**, including fronts. The result is a shutdown, lost stock, and frozen accounts.
- ✅ **Planning phase** before each raid: buy intel, choose an entry point, pick a squad, and choose equipment.
- ✅ **Orders** can go to the whole squad or to individual units.
- ✅ **Defense:** defenders place guards and traps in their building layout. Options include guards, cameras, reinforced doors, alarms, panic rooms, and bribing **NPC** police.
- ✅ Raids are **visible in the world**.
- ✅ **Limits:** one raid at a time per player, with cooldowns.
- ✅ **Attacker risks:** injured or dead gang members, heat, and revenge attacks.

## 7. Government careers

- ✅ **A separate life.** While on duty, a player can't manage their businesses; those businesses run as if the player were offline. There's no cooldown on switching. Government players **cannot sneak into or access players' bases**.
- ✅ **Government pay is XP**, which unlocks levels, cosmetics, vehicles, and titles.
- ✅ **Branches and agency names:**

| Branch | Parody name |
|---|---|
| Police | City Police (needs renaming for New Studsworth; see OPEN_QUESTIONS) |
| Detectives | Criminal Investigations Bureau (CIB) |
| IRS | Department of Revenue & Taxation (DRT), "the Taxmen" |
| FBI | Federal Bureau of Enforcement (FBE) |
| CIA (staff only) | Central Oversight Directorate, also called the High Directorate |

- ✅ **Ladder:** Police → Detective → IRS. Federal unlocks after all three are maxed out. Federal agents are more authoritative and **can bypass regular laws**.
- ✅ **The Directorate role** is staff only. It is both a moderation tool and the highest in-world authority (comparable to safety inspectors on a construction site).
- ✅ **Unlocking is hard**, with in-game requirements, so new players can't jump in and grief. The IRS requires a tax code exam minigame. Senior positions require promotion exam minigames.
- 🟡 The tax code changes every season, so exam answers can't simply be passed around.
- ✅ **Senior ranks** can issue bonuses, create timed special missions with bonus rewards, and lead multiplayer raids. They do **not** assign cases to juniors or approve warrants.
- ✅ **No corruption:** government players can't take bribes.
- ✅ **No limit** on how many government players can investigate one target.
- ✅ When no criminal players are online, government players work NPC criminal cases.
- 🟡 **Case loop:** leads come in → investigation minigames → evidence score → an NPC judge issues a warrant → raid or seizure → automated trial (evidence against an NPC lawyer the defendant can hire) → outcome.
- ✅ **Light roleplay** overall, with trials automated from evidence. The **government side has the heaviest roleplay**.
- ✅ **Punishment for convicted players combines** fines and asset seizure, jail time in **Rustgate Penitentiary** (a real map location where the player can still use their phone), and a temporary lock on the business.
- ✅ Government careers have their own tutorial (🟡 called "the Academy").

## 8. Politics and elections

- ✅ **Offices:** the Mayor (city-wide) and district Commissioners. 🟡 Commissioners pass laws for their district. The Mayor passes city-wide laws, can override Commissioners, and gets a salary, an office, and bodyguards.
- ✅ **Running for office** requires meeting thresholds (level, heat, and others). Qualified players join a queue and appear on the next ballot.
- ✅ **Elections happen only when a seat becomes vacant.** There's an entry window, then a voting period. 🟡 Proposed lengths: 3-minute entry window, 4-minute voting period. A sole candidate wins automatically.
- ✅ An official holds office in that server until they leave, resign, or are assassinated.
- ✅ **While a seat is vacant,** current laws stay in effect and no new laws can be passed.
- ✅ Officials can run businesses, but a crime conviction while in office is punished much more harshly.
- ✅ **Laws come from a preset list.** Commissioners can have 2 active laws and the Mayor 3. Laws last 20–30 minutes, with a cooldown before passing another. The **High Directorate can veto any law** and enact its own preset laws or temporary acts.
- ✅ **Everyone can vote.**
- ✅ **Campaigns:** candidates offer Studs-funded rewards to voters, capped per voter. **Robux buys campaign cosmetics only** (posters, billboards, rally stages, outfits, convoy skins, jingles). Bribing voters adds heat.
- ✅ **Campaign promises** come from a preset list and are tracked automatically. Broken promises lower approval.
- ✅ **City treasury** is funded by taxes. The Mayor spends it on preset projects (police funding, road repairs, propaganda). **Embezzlement is possible**, and it's a potential IRS case.
- ✅ **Approval rating** for each official.

## 9. Assassination and combat

- ✅ **Assassinations are done in person by players**, possibly with NPC help, as a planned operation with a visible attack.
- ✅ **Eligibility** depends on approval rating and how the official's laws affect you. It's allowed when approval is **below about 30%**.
- ✅ A **global cooldown, per server, per official** limits attempts.
- ✅ The official has NPC bodyguards, is **unarmed, and can try to flee**. Police players can respond live.
- ✅ **A killed official** respawns normally and loses their office. That is the only consequence for them.
- ✅ **Penalties:** a failed attempt gets a mild penalty. A successful one gets a harsher penalty, within reason, but **only if real government players intervene**. If none do, the assassin gets away with it.
- ✅ **Guns:** illegal for citizens. Only government players own them legally. **Assassins buy black market weapons**, and simply carrying one is a crime.
- ✅ **Combat** uses simple Roblox-style tools, mostly guns. It's built as a **general combat framework** (weapons, health, damage, server-side hit validation), because more PvP is planned later.

## 10. Crews

- ✅ **4–6 members.** Crews can own businesses together and share a treasury.
- ✅ **Ranks:** Founder, Co-Founder, high ranks, mid ranks, low ranks. Low ranks have no access to funds. Mid ranks can request funds. High ranks can allocate funds within a limit.
- ✅ Players must reach a certain level before receiving crew funds, and lower levels can receive only limited amounts.

## 11. Player, progression, and characters

- ✅ **Gameplay is mostly macro management:** a phone for quick actions, a laptop or office for deep management, plus actions that require being there in person.
- ✅ **Progression tracks:** player level, separate levels for each business, and reputation (street and corporate).
- ✅ **Winning means power:** owning the most businesses and the best upgrades. For government players, it means rank.
- ✅ **Multiple character saves per account.** Extra save slots and backgrounds are sold as game passes.
- 🟡 **Shared between characters:** cosmetics, game passes, and titles. **Separate per character:** money, businesses, levels, and reputation. Characters on one account can never transfer anything to each other.
- 🟡 **Starting backgrounds**, balanced, each with a bonus and a drawback:
  - **Inheritor:** inherits an upgraded car wash, plus a debt. Mentor: "Mags" Delgado.
  - **Ex-Con:** has street reputation and a fence contact, but starts with heat. Mentor: Benny Two-Locks.
  - **Defector:** has corporate reputation, but street contacts are wary. Mentor: Mr. Pell.
  - **Local:** cheaper, more loyal staff, but less starting cash. Mentor: Auntie Rosa.
- ✅ **In-depth tutorial,** inspired by Schedule 1. 🟡 Takes about 30–45 minutes. It can be skipped on later characters, except for the opening specific to the new background.
- ✅ The tutorial is the only scripted story. Lore after that comes through game updates, lore drops, and events.
- ✅ **Office and home progression,** also purchasable: start somewhere rundown and work up to a penthouse or mansion.
- ✅ **Day length:** about 20 real minutes per in-game day. Payroll and restocking run on cycles. Day and night affect businesses: the nightclub earns at night, and illegal operations are safer at night.

## 12. Vehicles

- ✅ GTA-style vehicles, plus taxis and fast travel as alternatives.
- 🟡 Players store owned cars in a garage and call them with the phone. Only one can be active at a time. Insurance restores destroyed cars. Ties into the Mechanic and the Dealership. NPC traffic is drawn on each player's device.

## 13. Monetization

- ✅ **Direct Robux pricing.** No premium currency.
- ✅ **Gifting only.** No player-to-player trading.
- ✅ **Approved product types:** offline earnings boost, extra manager slots, instant construction, a starter pack, crew-wide perks, a VIP subscription, extra character and background slots, a purchasable office or home, and campaign cosmetics.
- 🟡 Cosmetics are the main earner: business decor, signage, uniforms, hidden-room themes, vehicle wraps, outfits, and phone models. Also private servers and Premium Payouts.
- ✅ **No in-game advantage can be bought,** including in elections.

## 14. Lore

- ✅ **Backstory: "The Great Default."** Old Studsworth's private banks secretly lent out foreign gold deposits and lost them. Invasion nearly followed. The military seized power. New Studsworth was built beside the ruins of the old city.
- ✅ **Geopolitics:** Studmark is a small, neutral country between two warring superpowers:
  - **The People's Collective of Krovask:** communist-style.
  - **The Ventrex Corporate Federation:** a country run as a corporation.

  Studmark must keep both happy to avoid invasion.
- ✅ **Studmark is free in name only.** It's easily embargoed and controlled from outside. Its politicians are corrupt and greedy. Laws rarely last more than a couple of months, and leaders are replaced constantly. It's a **highly bureaucratic military government**.
- ✅ Studmark hosts **the world's largest central bank** (🟡 the Studmark Grand Reserve, in the Deep Vault) and sits on gold and silver deposits under the city.
- 🟡 **Power structure:** the High Directorate (military council, the real power) → a figurehead President who keeps getting replaced → the Ministries → the Mayor → district Commissioners. The national rulers sit above the city. This structure needs more depth.
- ✅ **Tone:** a friendly-looking surface with dark details underneath. Propaganda, slogans, and a state news channel. 🟡 Mascot: Goldie the Vault Owl. 🟡 Slogans include *"Neutral. Grateful. Compliant."*
- ✅ **NPC citizens** have a mix of attitudes: deluded, loyal, brainwashed, fearful, or resentful. 🟡 These attitudes affect snitching and how willing NPCs are to talk to detectives.
- 🟡 **Geography:** a gold-rich river valley that opens onto a bay. Krovask lies to the north (mountains), Ventrex to the east, the sea to the south (the smuggling route), and the Old Studsworth ruins to the west. This needs more depth.
- ✅ **NPC crime families** serve as AI raid targets. 🟡 There are three, one each for the Docks, the Rust Yards, and Gilded Row.
- ✅ **NPC corporations** exist mostly in the background.
- ✅ Other factions (news network, unions, an underground movement, a law firm) will be added eventually. Players can build some standing with NPC factions.
- ✅ **Story through updates:** the war storyline advances with game updates. Ashtown holds mysteries for future lore drops. Contracts for the superpowers are a "perhaps."
- ✅ **Weather is seasonal**, controlled by major game updates.
- ✅ **Parody brands** are wanted. Players can name their companies, with text filtering.
- ✅ **Lore is delivered through** a mix of radio news reacting to player events, a newspaper app, billboards, NPC dialogue, collectibles, and item descriptions.
- 🟡 **Radio stations:**
  - Studs FM 98.7: 2000s pop and pop-punk
  - Rust Radio: rock and nu-metal
  - Gilded 104: R&B and lounge
  - Club Frequency: 2000s electronic
  - Block Beats: 2000s hip-hop instrumentals
  - The Reserve Report: state news
  - Office Jazz: smooth jazz
- 🟡 **District palettes:**
  - Copperfield: warm brick and orange lights
  - Rust Yards: gray and rust, with fog
  - Gilded Row: gold, black, and neon
  - Saltmouth Docks: teal and navy, with rain
  - Vault Hill: white marble, flags, and cameras
- 🟡 **2000s devices:** a phone that upgrades from flip to slider to early smartphone, a chunky laptop, CRT TVs, pagers for criminal contacts.

## 15. Prototype scope

- ✅ A playable prototype with the complete skeleton in place, so later scaling never requires rewrites.
- 🟡 **Contents:**
  - One district
  - Base plot plus 3 city plots
  - Car Wash, Convenience Store, and Chop Shop
  - Full employee system
  - Laundering and heat
  - AI raid targets
  - Police as the only government branch
