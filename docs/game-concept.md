# Tidebreak — Game Concept

> Working title. Mobile 5v5 MOBA · iOS / Android · Free-to-play · Built in Unity · Concept v0.2

Companion documents:
- [Art direction & visual development plan](art-direction.md): how the game looks, and the visual work we finish before production code starts.

## 1. The pitch

**A full-depth 5v5 MOBA that fits in a 12-minute bus ride, on a map that changes under your feet.**

Tidebreak is fought on a coastline where the sea rises and falls on a fixed rhythm. Everyone knows *when* the tide will rise. Nobody knows *which way the river will run* until it does. When the water turns, one side of the map suddenly becomes a fast highway for ganks and the other becomes a slog. Teams prepare for both outcomes, then race to exploit the one they get.

Around that hook we fix the things mobile MOBA players complain about most: matches that drag on, games decided by one AFK player, pre-game grind that buys stat advantages, positions nobody wants to play, and toxic chat.

## 2. Where the market is, and the gap

| | Typical match | Strength | Common player complaint |
|---|---|---|---|
| Honor of Kings | ~15 min | Huge roster, polish, scale in China | Complexity for newcomers; regional focus outside China is still building |
| Mobile Legends | ~12–15 min | Fast, light, runs on low-end phones; dominant in SEA | Emblem/stat systems feel grindy; matchmaking and toxicity |
| Wild Rift | ~15–20 min | PC-grade depth, well-known IP | Long matches for mobile; slow hero unlocks; heavy device needs |
| Pokémon Unite | 10 min fixed | Approachable, strong IP | Shallower strategy; held-item progression felt pay-to-win at launch |

*(Figures are approximate and should be re-checked against current data before external use.)*

The gap: **nobody combines PC-level strategic depth with a reliably short match, zero paid stat power, and a map that keeps the mid-game unpredictable.** We can't win on IP or launch roster size, so we win on how the game *feels* to play every day.

## 3. Design pillars

1. **Twelve minutes, every minute matters.** Median match of 12–13 min, hard ceiling around 18. No dead farming windows.
2. **Skill is the only stat.** Nothing bought or ground outside a match changes combat numbers. No emblems, runes, or stat-bearing cosmetics.
3. **Know when, not which way.** The tide schedule is fixed and visible; the river's direction is revealed only at the moment it rises. Preparation and reaction both matter.
4. **Every position is a main character.** Support, Cliff lane and Jungle each have moments that decide games, and rewards that make people *want* to queue for them.
5. **A bad teammate shouldn't ruin your night.** AFK protection, bot takeover, comms built for cooperation, not arguing.
6. **Runs on the phone you already have.** A 3 GB RAM Android at stable 30 fps; 60/120 fps on mid-range and flagship.

## 4. The map

5v5, three lanes, a jungle split into four quadrants, a river cutting diagonally across the middle, two bases.

### Lanes are named by landmark, not "top" and "bottom"

Like other mobile MOBAs, the red team's camera is rotated 180° so both teams see their own base in the bottom-left. That means "top" for one team is "bottom" on the other team's screen. To keep communication unambiguous, lanes and river directions are named by landmark:

| Lane | Look | Usual occupants |
|---|---|---|
| **Cliff lane** | Sea cliffs, gull rookeries, wind-bent pines | Solo laner |
| **Causeway** (mid) | A half-sunken stone road between the two cities | Mid laner |
| **Mangrove lane** | Roots, boardwalks, tidepools | Carry + Support |

The **river** runs from the Cliff end to the Mangrove end, crossing the Causeway in the center.

## 5. The tide

### When: fixed and visible

| Time | Tide event | Water state |
|---|---|---|
| 0:00 | Match start | **Low tide** — shallow, still river |
| 4:00 | **First rise** | High tide — current direction revealed |
| 6:00 | Fall | Low tide — Shrines surface |
| 8:00 | **Second rise** | High tide — direction revealed again |
| 10:00 | **The Surge** | Permanent high tide; direction revealed |
| 12:00, 14:00, … | **Churn** | Still high tide, direction re-rolled every 2 min |

The tide clock sits beside the match timer, a 15-second warning plays before each rise, and a haptic pulse fires at 5 seconds. Everyone can plan around *when*.

### Which way: revealed at the rise

When the tide rises, the river starts flowing either **toward the Cliffs** or **toward the Mangroves**. Players find out which at the moment of the rise, not before.

**The rules (semi-random):**
- Each rise is a 50/50 roll between the two directions.
- **No three in a row:** the river can't flow the same way three rises running. After two of the same, the third is guaranteed to flip. This gives attentive teams a small, earned edge, and stops one side of the map from being dull for a whole match.
- The result is decided on the server at the reveal moment and sent to clients only then. It can't be found by data-mining, prediction, or modified clients.
- The map is symmetrical across the river, so neither direction favors the blue or red team. Live telemetry will watch for any imbalance (win rate by direction × side × position).

**What the direction changes:**

| | Downstream side (where the water flows to) | Upstream side (where it flows from) |
|---|---|---|
| River movement | +30% move speed moving with the current | −20% moving against it |
| Jungle access | Two **spillways** open: fast-water chutes from the river into both teams' jungles on that side | The river mouth deepens; two jungle entrances flood shut |
| Objectives | The **Leviathan** surfaces here (from 8:00) | — |
| Drifting loot | **Flotsam** caches wash down the river and beach here | — |
| Net effect | Fast, dangerous, high-traffic: ganks arrive from the river quickly | Slower and safer, but cut off from the fight |

### The Turn: the reveal moment

Every rise plays out as a three-second sequence called **the Turn**:

1. **Slack water (0–1 s):** the water level climbs and the river goes perfectly still. River movement is neutral.
2. **Churn (1–2.5 s):** whirlpools form along the river. Audio swells; neither direction is hinted.
3. **Commit (2.5–3 s):** a surge wave rolls from the upstream end toward the downstream end, the current snaps into place, and a direction arrow appears on the HUD and minimap.

Those three seconds are the most tense in the game. They're designed to be watched: a visible, audible "dice roll" that every player and every spectator sees at the same time.

### How it plays

- **Before the rise:** junglers hold central positions that can reach either side. Laners keep their waves in states that are safe whichever way the water goes. Supports ward *both* spillways or choose to gamble on one.
- **The first 20 seconds after the Turn:** the downstream side is the most gankable spot on the map. The team that reacts fastest wins it.
- **The upstream side:** the laners there get a short window of safety to push, recall, or take a tower.
- **Mind games:** after two rises the same way, both teams know the third will flip, and plan for it.

## 6. Objectives

| Objective | When | Reward | Notes |
|---|---|---|---|
| **Sunken Shrines** (×2, one per river half) | 3:00 in the Ebb, then every low tide | Capture by standing in the circle (5 s; contesting pauses it). Grants a team-wide **Tide Blessing**, stacking to 3: choose one of two each capture. | Short, readable fights that any team composition can contest. |
| **Leviathan** | Surfaces at the downstream river mouth 30 s after the 8:00 rise; respawns at the next rise or churn after it dies | The killing team's minions are carried by a **tidal wave** down one chosen lane for 60 s, hitting towers hard. | Location changes with the current, so even the big objective is part of the reveal. The reward must be spent, not banked. |
| **Flotsam caches** | Every high tide | Drift down the current and wash up downstream; break one for gold and a short speed boost. | Pulls junglers and supports into the river right after the Turn. |
| **Crown Tide** | Replaces the 14:00 churn | The base gates open, the **Heart** (nexus) stops regenerating, and the team holding more Shrine Blessings gets a 20 s empowered push. | A designed finale that caps match length. |

### Comeback without coin flips

- **Bounties** on kill streaks and on teams ahead in gold, paid mostly as *experience* (catches you up in levels) rather than gold.
- Shrines are capture objectives, not damage races, so the team that's behind can contest with good positioning.
- The random current direction gives the losing team regular openings to catch a split enemy out of position.

## 7. Positions and classes

Tidebreak separates **what a hero is** (their class) from **where they play** (their position).

### Positions: what you queue for

| Position | Where | Job |
|---|---|---|
| **Cliff** | Cliff lane, solo | Hold a lane alone, split-push, teleport into fights |
| **Jungle** | The four jungle quadrants and the river | Farm camps, gank, control objectives, and react first to every Turn |
| **Mid** | Causeway | Roam to both sides; first to any river fight |
| **Carry** | Mangrove lane | Scale into the main damage dealer |
| **Support** | Mangrove lane, then everywhere | Vision, protection, and starting fights |

Ranked uses role queue across these five positions.

### Classes: what a kit does

| Class | Kit identity |
|---|---|
| **Vanguard** (tank) | Starts fights and protects; every Vanguard has a big moment ultimate that changes terrain or moves multiple enemies |
| **Striker** (fighter / assassin) | Dives and duels; clear windows in and out; every dash has a visible tell |
| **Arcanist** (mage) | Zones and bursts; many kits interact with water |
| **Marksman** | Sustained ranged damage; few self-defence tools |
| **Warden** (support) | Enables, saves, and controls vision |

A class is not a position. A Vanguard might play Cliff, Jungle, or Support. A Striker might play Jungle, Cliff, or Mid.

### Designed for the jungle, without a jungler class

"Jungler" is a position, not a class. But some heroes are deliberately designed to be great at it. These **jungle-natural** heroes come from several classes and share some of these traits:

- **Efficient clearing:** area damage, sustain, or abilities that reset on monster kills.
- **Terrain mobility:** crossing walls, reefs, or water faster than other heroes.
- **A gank tool:** crowd control or burst that lands from fog of war.
- **Tide reaction:** something in the kit that rewards responding quickly to the Turn (for example, a speed burst toward the downstream side right after it's revealed). These traits reward *reacting* to the reveal; none of them lets a player know the direction early.

Any hero *can* jungle. Jungle-naturals just do it noticeably better, the way some heroes are clearly better solo laners.

**In draft**, each hero shows its **natural positions** (one or two, designed for) and **viable positions** (works with the right build). This guides newer players without forbidding experiments.

**Launch target:** at least 6 jungle-natural heroes spread across at least 3 classes, so junglers have a real choice of playstyle (tank jungler, assassin jungler, mage jungler).

### Jungle systems

- **Tidehook:** a jungle relic (the "smite" equivalent). It deals heavy true damage to monsters, secures objectives, and lets you hook onto river debris to cross water. Taking lane minion gold while holding it is heavily penalized, so it's a natural fit only in the Jungle position. After 20 camp clears it evolves into one of two forms the player chooses:
  - **Riptide Hook** (ganking): hooking a champion slows them and reveals them briefly.
  - **Anchor Hook** (control): bonus damage to the Leviathan and a shield while standing in a Shrine.
- **Camps:** four camps per quadrant, with clear first-clear routes reaching the river at ~1:30.
- **Tidepool camps:** small camps along the river banks that exist only at **low tide**. They give bonus gold and a short vision sweep of the river, so junglers fight over the river even before the first rise.
- **Flotsam** (see objectives) gives junglers and supports a reason to collide right after each Turn.
- **Early-game rhythm:** first clear → Shrine at 3:00 → first Turn at 4:00. The first Turn is the jungler's defining decision of the early game.

## 8. Heroes

### Kits: 4 abilities + 2 Attunements

Every hero has a passive, two abilities, and an ultimate. At level 4 and level 8, each player picks one of two **Attunements**: upgrades that change *how* an ability works, not just its numbers. This replaces runes and emblems. Customization happens inside the match, where it responds to the actual game, and it can't be bought.

### Sample launch heroes

**Isra Coil** — *Striker* · Natural: **Jungle** · Viable: Mid
- Passive: *Current Rider.* Gains double the river's speed bonus. For 4 s after each Turn, gains bonus move speed in the direction of the current anywhere on the map.
- 1: *Slipstream.* Dash. Recasts on hitting a champion; resets on killing a monster.
- 2: *Coil.* Spins, damaging nearby enemies and becoming briefly untargetable.
- Ult: *Rogue Wave.* Marks an enemy, then crashes down on them after 1.5 s (telegraphed to the target).
- *Why she junglers well:* clears with resets, gets to the downstream side first after every Turn.

**Grothmaw, the Reef Hulk** — *Vanguard* · Natural: **Jungle** · Viable: Cliff, Support
- Passive: *Coral Hide.* Killing monsters grows a stacking armor shell that shatters for damage when Grothmaw is crowd-controlled.
- 1: *Burrow.* Tunnels through a reef wall or short stretch of terrain; enemies above the exit point are knocked up.
- 2: *Slam.* Ground pound that slows and clears camps quickly.
- Ult: *Tidal Charge.* Charges in a line, carrying enemies with him. Travels twice as far when charging downstream.
- *Why he junglers well:* terrain mobility, a gank tool from fog, and a reward for reading the current fast. A tank jungler who sets up fights instead of finishing them.

**Maren, the Undertow** — *Vanguard* · Natural: **Support**, **Cliff**
- Passive: *Riptide.* Standing in river water builds a stacking shield.
- 1: *Anchor Toss.* Throws an anchor; hit an enemy to pull yourself to them.
- 2: *Breakwater.* Raises a short wall of water that blocks projectiles.
- Ult: *Drown the Shore.* Floods a large circle for 4 s; enemies inside are slowed and pulled toward the center.
- Attunement 4: Breakwater becomes a *moving* wall *or* Anchor Toss pulls the enemy to you instead.

**Kesh Varo, the Lantern** — *Warden* · Natural: **Support**
- Passive: *Guiding Light.* Allies who move along Kesh's lantern trail gain move speed.
- 1: *Beacon.* Places a lantern that reveals an area and heals allies standing in it.
- 2: *Tether.* Links to an ally; the next lethal damage they take within 3 s is redirected to Kesh as a shield.
- Ult: *Lighthouse.* Kesh becomes a stationary tower of light for 5 s: reveals the whole river and shoots beams at enemies in range.
- Attunement 8: Lighthouse can be cast on an ally *or* Tether can link two allies to each other.

**Vael Ashdown** — *Arcanist* · Natural: **Mid** · Viable: Jungle
- Steam mage: abilities do more damage to targets standing in water, and evaporate flooded terrain to create cover. Strongest at high tide, weakest at low tide. A tide-dependent jungler pick for teams that plan to fight in the river.

**Dorrin & Pip** — *Marksman* · Natural: **Carry**
- A crossbow ranger and a crab who carries the bolts. Pip can be sent to a spot to act as a forward ward and second firing point. Teaches positioning through a cute, readable kit.

### Roster plan

- Launch: **30 heroes**, with at least 6 natural picks for each position. Attunements put effective variety closer to 60 playstyles.
- Post-launch: one new hero every ~4 weeks, plus one **rework** per season.
- Free rotation of 10 heroes weekly, always covering every position. Every hero is earnable through play (target: a casual player earns a new hero every ~5–7 days).

## 9. Items

- **Five slots + boots.** About 60 items at launch.
- **Recommended build** auto-adjusts mid-match to enemy composition. One-tap buy from the HUD without opening the shop.
- **Relics:** one active-item slot (dash, shield, cleanse, etc.), swappable in the shop. The **Tidehook** is the jungle relic.
- Gold from Shrines is shared, so Supports don't fall behind.

## 10. Controls & feel

- **Twin-stick by default**, with smart-cast, quick-cast, and precision (drag-to-aim) per ability.
- **Target priority toggle** (lowest HP / closest / heroes only), always visible as one button.
- **Last-hit and tower-hit buttons** for players who want them; auto-targeting for players who don't.
- **Camera nudge:** drag the minimap edge with your free thumb to peek without losing your hero.
- **Tide awareness:** haptic pulse 5 s before a rise; another, stronger pulse when the direction commits. The arrow appears on the minimap where your eyes already are.
- **Left-handed and custom layouts**, full HUD scale and opacity control.

## 11. Social health

| Problem | Our answer |
|---|---|
| Toxic chat | No free-text all-chat. Team free-text is **off by default** (opt in per game). A **contextual ping wheel** handles most communication, including tide calls: "Turn in 15", "Current to Cliffs, collapse", "Upstream: push now". |
| AFK / disconnects | After 45 s of inactivity, a **bot takes over** at near-player skill. Reconnect target under 5 s. The AFK player loses rank points; the other four lose **none** if they lose. |
| Early forfeit fights | Surrender unlocks at 8:00, needs 4/5. |
| Position conflict | Role queue across five positions. Players who queue for the least-requested position get a **Fill Bonus** (extra rank points on a win, cosmetic currency). |
| Smurfing / boosting | Phone-number or platform account binding for Ranked; fast-track MMR for new accounts with high performance. |
| Reporting that feels pointless | Reporters are told when action was taken on a player they reported. |

Post-match **Shout-outs** (one tap to commend a teammate for a save, a call, or carrying) feed a visible honor level and seasonal rewards.

## 12. Modes

| Mode | Players | Length | Purpose |
|---|---|---|---|
| **Ranked** | 5v5, role queue | ~12–14 min | The core competitive game |
| **Quick Play** | 5v5, preferred positions | ~12–14 min | Same game, no rank |
| **Skirmish** | 3v3: solo lane, jungle, mid-sized river | ~7 min | Commute mode; also the best place to learn the jungle and the Turn |
| **Breakwater** | 5v5, single bridge, random heroes | ~10 min | Chaotic team-fight mode, rotates in on weekends |
| **Co-op vs AI** | 1–5 players | ~12 min | Onboarding and practice |

Onboarding: a 15-minute playable tutorial, then guided bot matches that each introduce one system (lanes and jungle, the tide and the Turn, Shrines, items, Attunements, the Leviathan). Ranked unlocks at level 10 with 10 heroes owned.

## 13. Progression

- **Account level** unlocks modes and gives early heroes; it never affects combat.
- **Hero Mastery:** cosmetic tiers per hero (borders, emotes, titles), plus regional leaderboards per hero.
- **Ranked:** three-month seasons, separate MMR per position, rank protection on the first loss after promotion.
- **Clubs:** guilds with shared weekly goals and club-vs-club weekend events.

## 14. Monetization

A strict line: **pay for looks and convenience, never for power.**

- **Skins** (main revenue): from recolors to premium **Tide-reactive** skins whose visuals shift between low tide, high tide, and the Turn. Every skin passes a readability check (see the art direction document).
- **Tide Pass:** seasonal battle pass with a free track (including 2 heroes) and a premium track that pays for itself in currency if completed.
- **Heroes:** buyable with premium currency for players who don't want to wait; always earnable for free.
- **No loot boxes for heroes or items.** Any randomized cosmetic bundles show exact odds, include a pity guarantee, and are disabled where restricted.
- **Regional pricing** tuned for Southeast Asia, Latin America, and India.

## 15. Esports & community

- In-client **spectator mode** with delay, broadcaster HUD, and replays from day one. The Turn gets a dedicated broadcast moment: a split-screen showing both teams' reactions.
- **Grassroots first:** automated in-client weekend tournaments before any pro league; a regional pro circuit after year one.
- **Creator program:** custom lobbies, replay export, and automatically generated highlight clips (the Turn and the plays right after it are natural clip moments).

## 16. Technology: Unity

The game is built in **Unity**, which is proven at scale for mobile MOBAs and gives us broad device coverage, mature mobile tooling, and a large hiring pool.

| Area | Choice |
|---|---|
| Engine version | Latest **Unity 6 LTS** at production start, upgraded only between seasons |
| Rendering | **Universal Render Pipeline (URP)** with per-device quality tiers. Details in the art direction document |
| Scripting backend | IL2CPP on both platforms |
| Simulation | A **deterministic game simulation written in plain C#** with fixed-point math, kept separate from Unity's `MonoBehaviour` world. Unity is the presentation layer: it draws what the simulation says. This lets the same simulation run on headless dedicated servers, in replays, and in automated balance testing |
| Netcode | Server-authoritative at 30 Hz with client-side prediction for movement and casts. The server decides what each client can see (no map hacks) and holds the tide seed (no early knowledge of the current direction) |
| Content delivery | **Addressables** for skins, heroes, and high-resolution packs downloaded on demand |
| Latency | Playable up to 120 ms. Launch regions: Singapore, Manila, Jakarta, São Paulo, Mumbai, Frankfurt, Virginia, Tokyo |
| Devices | 30 fps stable on 3 GB RAM Android (2021+ budget chips); 60 fps mid-range; 120 fps flagships |
| Install size | Under 1 GB initial download |
| Match load | Under 10 s on mid-range |
| Anti-cheat | Server authority + client integrity checks + replay-based detection of input automation |
| Cross-play | iOS / Android shared queues from day one |

## 17. World

**Setting:** *The Strand*, an archipelago where the heartbeat of a sleeping sea-god moves the ocean. Two coastal city-states fight for the **Hearts**, sunken relics that let whoever holds them command the tide. Nobody, not even the cities' tide-priests, can predict which way the sea will run when it rises; legend says the god chooses.

Full visual direction, including the look of each zone, the water, characters, and the Turn, is in the [art direction document](art-direction.md).

## 18. Launch plan

| Phase | Timing (from greenlight) | Scope | Goal |
|---|---|---|---|
| **0. Visual development** | Months 0–4 | Art bible, camera and scale tests, hero silhouettes, water and Turn look-dev, a "beauty corner" visual target in Unity | Lock the look and its performance budget before production code |
| 1. Gameplay prototype | Months 3–8 | Graybox map, 8 heroes (including 2 jungle-naturals), tide and Turn, bots | Prove the random current makes matches better, not just different |
| 2. Closed alpha | Months 9–14 | 15 heroes, Ranked, items, production art for the map | Tune match length and balance with ~5k players |
| 3. Soft launch | Months 15–20 | 24 heroes; Philippines, Brazil, Malaysia | Retention and monetization validation |
| 4. Global launch | Months 20–26 | 30 heroes, Clubs, open tournaments | Scale |

Phases 0 and 1 overlap on purpose: gameplay prototyping uses throwaway code and graybox art, while the visual target is built in a separate Unity look-dev project. Production code starts once both pass their gates.

### Target metrics at soft launch

| Metric | Target |
|---|---|
| D1 / D7 / D30 retention | 45% / 22% / 10% |
| Median match length | 12–13 min |
| Ranked queue time (median, peak) | < 45 s |
| Games with an AFK-to-bot takeover | < 3% |
| Win-rate gap between current directions, per side | < 1 percentage point |
| Jungle position share of queue entries (without Fill Bonus) | ≥ 18% |
| Crash rate | < 0.5% of sessions |

## 19. Risks and how we handle them

| Risk | Mitigation |
|---|---|
| Network effects: players stay where their friends are | Target regions underserved by competitors' servers or pricing; referral and squad-up rewards; Skirmish as an easy entry point |
| Random direction feels unfair ("we lost because of the coin flip") | Both teams get the same information at the same moment; the map is symmetrical; the no-three-in-a-row rule limits streaks; telemetry tracks direction impact. If the gap exceeds target, we soften the speed modifiers before touching the randomness |
| The Turn becomes noise players ignore | Make the downstream advantage strong enough to matter and short enough to require reaction; test with and without the mechanic in prototype |
| Jungle is too hard for new players | Jungle-natural heroes are labelled in draft; Skirmish teaches it; recommended clear paths shown in the first 20 jungle games |
| Small launch roster | Attunements double effective variety; ~4-week hero cadence |
| Short matches feel shallow to veterans | Depth lives in tide timing, the Turn, Shrine choices, and Attunements, not farm time. Track veteran retention separately |
| Large IP competitors outspend us | Creator program, community tournaments from day one, and a signature moment (the Turn) that's easy to clip and share |

## 20. Open questions

1. Is 2 minutes the right churn interval during the Surge, or should it speed up?
2. Should the "no three in a row" rule be shown to players, or left for them to discover?
3. Should any rare effect (an item or ultimate) ever reveal the direction early, or is "nobody knows" sacred?
4. Do we allow team free-text chat in Ranked at all?
5. Should Skirmish (3v3) have its own ranked ladder?
6. Do we need a transmedia plan (animated shorts) to compete for attention with established franchises?

## Next steps

1. Start Phase 0: art bible, camera tests, and water/Turn look-dev (see the [art direction document](art-direction.md)).
2. In parallel, build the graybox gameplay prototype: map, tide, the Turn, 8 heroes, bots.
3. Write full kits for the first 15 heroes, with at least 4 jungle-naturals across 3 classes.
4. Draft the Attunement and item lists and simulate gold and XP curves to hit the 12–13 min target.
