# Tidebreak — Game Concept

> Working title. Mobile 5v5 MOBA · iOS / Android · Free-to-play · Concept v0.1

## 1. The pitch

**A full-depth 5v5 MOBA that fits in a 12-minute bus ride, on a map that changes under your feet.**

Tidebreak is fought on a coastline where the sea rises and falls on a fixed rhythm. Every tide reshapes the map: river paths flood or dry out, shortcuts open, and buried objectives come to the surface. Teams don't just farm until the next big monster; they plan around the next tide.

Around that hook we fix the things mobile MOBA players complain about most: matches that drag on, games decided by one AFK player, pre-game grind that buys stat advantages, roles nobody wants to play, and toxic chat.

## 2. Where the market is, and the gap

| | Typical match | Strength | Common player complaint |
|---|---|---|---|
| Honor of Kings | ~15 min | Huge roster, polish, scale in China | Complexity for newcomers; regional focus outside China is still building |
| Mobile Legends | ~12–15 min | Fast, light, runs on low-end phones; dominant in SEA | Emblem/stat systems feel grindy; matchmaking and toxicity |
| Wild Rift | ~15–20 min | PC-grade depth, well-known IP | Long matches for mobile; slow hero unlocks; heavy device needs |
| Pokémon Unite | 10 min fixed | Approachable, strong IP | Shallower strategy; held-item progression felt pay-to-win at launch |

The gap: **nobody combines PC-level strategic depth with a reliably short match, zero paid stat power, and a map that keeps the mid-game varied.** That is the slot Tidebreak goes for. We can't win on IP or on roster size at launch, so we win on how the game *feels* to play every day.

## 3. Design pillars

1. **Twelve minutes, every minute matters.** Median match of 12–13 min, hard ceiling around 18. No dead farming windows.
2. **Skill is the only stat.** Nothing bought or ground outside a match changes combat numbers. No emblems, runes, or stat-bearing cosmetics.
3. **The map is a player.** The tide cycle forces decisions on a clock everyone can see.
4. **Every role is a main character.** Support and tank get kits and rewards that make people *want* to queue for them.
5. **A bad teammate shouldn't ruin your night.** AFK protection, bot takeover, comms built for cooperation, not arguing.
6. **Runs on the phone you already have.** A 3 GB RAM Android at stable 30 fps; 60/120 fps on mid-range and flagship.

## 4. Core match structure

5v5, three lanes, a jungle, two bases. Familiar enough that MOBA veterans are productive in game one; the twist is the clock.

### The three acts

| Act | Time | What's happening | Win condition pressure |
|---|---|---|---|
| **I. Ebb** | 0:00–4:00 | Laning, first jungle clears. Tide is *low*: the river is shallow and walkable everywhere. | First **Shrine** (see below) surfaces at 3:00. |
| **II. Flow** | 4:00–10:00 | Tide alternates high/low every 2 minutes. Each shift opens or closes paths and surfaces an objective. | Shrines, the **Leviathan**, and first towers fall. |
| **III. Surge** | 10:00+ | The tide reaches a permanent high. The outer river floods, lanes compress toward the center, and the bases' **Tide Gates** open. | Base pressure; respawn timers grow fast; the **Crown Tide** event forces a decisive fight. |

### The tide

- **Low tide:** The river is shallow. Anyone can cross anywhere. **Sunken Shrines** are exposed and can be captured.
- **High tide:** The river becomes a current. Moving *with* the current grants +30% move speed; moving against it is slowed. Two jungle paths per side flood shut, and a **sandbar bridge** opens across mid. Ganks become predictable on one side and fast on the other.
- A tide clock sits on the HUD next to the match timer. A 15-second warning plays before each shift. Everyone always knows what's coming, so this is strategy, not randomness.

### Objectives

| Objective | When | Reward | Why it's different |
|---|---|---|---|
| **Sunken Shrine** (×2, one per river half) | Every low tide from 3:00 | Capture by standing in the circle (5 s, contested pauses it). Grants a team-wide **Tide Blessing** that stacks up to 3 (choose one of two each capture: e.g. +ability haste, or shields after dashes). | Short, readable fights that small teams can win. Choices create build-like team identity without pre-game grind. |
| **Leviathan** | 7:00, then every 3 min at high tide | Killing team's minions are carried by a **tidal wave** down one chosen lane, which hits towers hard for 60 s. | The reward is *pushing*, not raw stats, so it converts into an ending instead of a snowball. |
| **Crown Tide** | 14:00 if the game is still going | A wave sweeps both bases. The **Heart** (nexus) loses its regeneration and the team holding more Shrine Blessings gets a 20 s empowered push. | A designed finale that caps match length without a coin-flip sudden-death rule. |

### Comeback without coin flips

- **Bounties** on players with kill streaks and on teams ahead in gold, paid out mostly as *experience* (catches you up in levels) rather than gold.
- Shrines are capture objectives, not damage races, so the team that's behind can still contest with good positioning.
- The **Leviathan's** reward expires: you have to use it, you can't bank it.

## 5. Heroes

### Roles

| Role | Job | What we change |
|---|---|---|
| **Vanguard** (tank) | Start fights, protect | Every Vanguard has a "big moment" ultimate that changes terrain or displaces multiple enemies. |
| **Striker** (fighter / assassin) | Dive, duel | Clear windows in and out; strict counterplay rules (every dash has a visible tell). |
| **Arcanist** (mage) | Zone, burst | Many Arcanist kits interact with water and the tide. |
| **Marksman** | Sustained damage | Fewer self-peel tools; relies on team. |
| **Warden** (support) | Enable, save, vision | Wardens own the **vision economy** (see below) and earn the most from Shrine captures. Their saves appear on the end-of-match screen as highlights. |

There's no dedicated jungler role. The jungle is shared by whoever is roaming, usually the Striker or Vanguard. That keeps one of the hardest-to-learn roles from blocking new players.

### Kits: 4 abilities + 2 Attunements

Every hero has a passive, two abilities, and an ultimate. The depth comes from **Attunements**: at level 4 and level 8, each player picks one of two upgrades that change *how* an ability works (not just numbers).

This replaces runes and emblems. Customization happens **inside the match**, where it responds to the actual game, and it can't be bought.

### Sample launch heroes

**Maren, the Undertow** — *Vanguard*
- Passive: *Riptide.* Standing in river water builds a stacking shield.
- 1: *Anchor Toss.* Throws an anchor; hit an enemy to pull yourself to them.
- 2: *Breakwater.* Raises a short wall of water that blocks projectiles.
- Ult: *Drown the Shore.* Floods a large circle for 4 s; enemies inside are slowed and pulled toward the center.
- Attunement 4: Breakwater becomes a *moving* wall *or* Anchor Toss pulls the enemy to you instead.

**Kesh Varo, the Lantern** — *Warden*
- Passive: *Guiding Light.* Allies who move near Kesh's lantern trail gain move speed.
- 1: *Beacon.* Places a lantern that reveals an area and heals allies standing in it.
- 2: *Tether.* Links to an ally; the next lethal damage they take within 3 s is redirected to Kesh as a shield.
- Ult: *Lighthouse.* Kesh becomes a stationary tower of light for 5 s: reveals the whole river and shoots beams at enemies in range.
- Attunement 8: Lighthouse can be cast on an ally *or* Tether can link two allies to each other.

**Isra Coil** — *Striker*
- Passive: *Current Rider.* Gains double the tide speed bonus.
- 1: *Slipstream.* Dash. Recasts on hitting a champion.
- 2: *Coil.* Spins, damaging nearby enemies and becoming briefly untargetable.
- Ult: *Rogue Wave.* Marks an enemy, then crashes down on them after 1.5 s (telegraphed to the target).

**Vael Ashdown** — *Arcanist*
- Steam mage: abilities do more damage to targets standing in water, and evaporate flooded terrain to create cover. Strongest at high tide, weakest at low tide. Players time aggression to the tide.

**Dorrin & Pip** — *Marksman*
- A crossbow ranger and a crab who carries the bolts. Pip can be sent to a spot to act as a forward ward and second firing point. Teaches positioning through a cute, readable kit.

### Roster plan

- Launch: **30 heroes** (6 per role). Smaller than competitors, but each with Attunements, so effective variety is closer to 60 playstyles.
- Post-launch: 1 new hero every ~4 weeks, plus one **rework** per season.
- Free rotation of 10 heroes weekly; every hero earnable through play (target: a casual player earns a new hero every ~5–7 days).

## 6. Items

- **Five slots + boots.** Around 60 items at launch.
- **Recommended build** auto-adjusts mid-match to enemy composition (e.g. suggests anti-heal when the enemy team heals heavily). One-tap buy from the HUD without opening the shop.
- **Relics:** one active-item slot (dash, shield, cleanse, etc.) chosen in the shop, like a second summoner spell you can swap later.
- Gold from Shrines is shared, so Wardens don't fall behind.

## 7. Controls & feel

- **Twin-stick by default**, with smart-cast, quick-cast, and precision (drag-to-aim) per ability.
- **Target priority toggle** (lowest HP / closest / heroes only), always visible on the HUD as a single button.
- **Last-hit and tower-hit buttons** for players who want them; auto-targeting for players who don't.
- **Camera nudge:** drag the minimap edge with your free thumb to peek without losing your hero.
- **Tide awareness:** haptic pulse 15 s before a tide shift; the HUD clock fills like a wave.
- **Left-handed and custom layouts**, full HUD scale and opacity control.

## 8. Social health

| Problem | Our answer |
|---|---|
| Toxic chat | No free-text all-chat. Team free-text is **off by default** (opt in per game). A rich **contextual ping wheel** handles 90% of communication: "Shrine in 15", "Tide turning, fall back", "I have ult". |
| AFK / disconnects | After 45 s of inactivity, a **bot takes over** at near-player skill. Reconnect target under 5 s. The AFK player loses rank points; the other four lose **none** if they lose. |
| Early forfeit fights | Surrender vote unlocks at 8:00, needs 4/5. Matches are short enough that "just play it out" is reasonable. |
| Role conflict | Role queue in Ranked. Players who pick the least-requested role get a **Fill Bonus** (extra rank points on a win, cosmetic currency). |
| Smurfing / boosting | Phone-number or platform account binding for Ranked; fast-track MMR for new accounts with high performance. |
| Reporting that feels pointless | Report outcomes are sent to the reporter ("Action was taken on a player you reported"). |

Positive reinforcement: post-match **"Shout-outs"** (one tap to commend a teammate for a save, a call, or carrying), which feed a visible honor level and seasonal rewards.

## 9. Modes

| Mode | Players | Length | Purpose |
|---|---|---|---|
| **Ranked** | 5v5, role queue | ~12–14 min | The core competitive game |
| **Quick Play** | 5v5 | ~12–14 min | Same game, no rank, blind pick |
| **Skirmish** | 3v3, one lane + jungle | ~7 min | Commute mode; also the best place to learn a hero |
| **Breakwater** | 5v5, single bridge, random heroes | ~10 min | Chaotic team-fight mode, rotates in on weekends |
| **Co-op vs AI** | 1–5 players | ~12 min | Onboarding and practice |

Onboarding: a 15-minute playable tutorial, then 5 guided bot matches that each introduce one system (tide, Shrines, items, Attunements, Leviathan). Players unlock Ranked after level 10 and owning 10 heroes.

## 10. Progression

- **Account level** unlocks modes and gives early heroes; it does not affect combat.
- **Hero Mastery:** cosmetic tiers per hero (borders, emotes, title), plus a regional/national leaderboard per hero.
- **Ranked:** seasonal ladder, 3 months per season. Rank protection on the first loss after promotion. Separate MMR per role.
- **Clubs:** guilds with shared weekly goals and club-vs-club weekend events.

## 11. Monetization

A strict line: **pay for looks and convenience, never for power.**

- **Skins** (the main revenue): tiered from simple recolors to "Tide-reactive" premium skins whose visuals change between high and low tide. Effects never change hitboxes or readability; every skin passes a clarity check.
- **Tide Pass:** seasonal battle pass with a free track (includes 2 heroes) and a premium track. Premium pays for itself in currency if completed.
- **Heroes:** buyable with premium currency for players who don't want to wait, always earnable for free.
- **No loot boxes for heroes or items.** Any randomized cosmetic bundles show exact odds and include a pity guarantee, and are disabled in regions where they're restricted.
- **Regional pricing** tuned for Southeast Asia, Latin America, and India.

## 12. Esports & community

- In-client **spectator mode** with a delay, a broadcaster HUD, and replays from day one.
- **Grassroots first:** in-client open tournaments every weekend (bracketed, automatically scheduled) before any pro league.
- **Pro circuit** after year one, regional leagues feeding one world event.
- **Creator program:** custom lobbies, replay export, clip highlights generated from each match.
- Short matches make tournaments shorter too, which is good for viewers and broadcasters.

## 13. Technology

| Area | Target |
|---|---|
| Engine | Unity (broad device support, mature mobile tooling) with a custom deterministic simulation core in C# |
| Netcode | Server-authoritative simulation at 30 Hz, client-side prediction for movement and ability casts. The server decides what each client can see, so fog of war can't be broken by map hacks. |
| Latency | Playable up to 120 ms. Regional servers in Singapore, Manila, Jakarta, São Paulo, Mumbai, Frankfurt, Virginia, Tokyo at launch |
| Devices | 30 fps stable on 3 GB RAM Android (2021+ budget chips); 60 fps mid-range; 120 fps flagships |
| Install size | Under 1 GB initial, with high-resolution assets downloaded optionally |
| Match load time | Under 10 s on mid-range |
| Anti-cheat | Server authority + client integrity checks + replay-based detection of input automation |
| Cross-play | iOS / Android shared queues from day one; a cloud/PC client is a later consideration |

## 14. World and art direction

**Setting:** *The Strand*, an archipelago where an ancient tide-god's heartbeat moves the ocean. Coastal city-states fight for control of the Hearts, sunken relics that let whoever holds them command the tide.

**Look:** Bright, painterly, high-contrast. Warm sands and coral vs deep teal water. Characters have strong silhouettes that read at phone size, with each role sharing a visual language (Vanguards are broad and heavy, Wardens carry light sources, Marksmen have long horizontal lines).

**Readability rules:** Every ability telegraph uses team colors on top of skin effects. Water states (shallow / current) use color *and* texture patterns, so colorblind players can read the tide.

## 15. Launch plan

| Phase | Timing (from greenlight) | Scope | Goal |
|---|---|---|---|
| Prototype | Months 0–6 | Graybox map, 6 heroes, tide system, bots | Prove the tide makes matches better, not just different |
| Closed alpha | Months 7–12 | 15 heroes, Ranked, items | Tune match length and balance with ~5k players |
| Soft launch | Months 13–18 | 24 heroes; Philippines, Brazil, Malaysia | Retention and monetization validation |
| Global launch | Month 18–24 | 30 heroes, Clubs, open tournaments | Scale |

### Target metrics at soft launch

| Metric | Target |
|---|---|
| D1 / D7 / D30 retention | 45% / 22% / 10% |
| Median match length | 12–13 min |
| Ranked queue time (median, peak) | < 45 s |
| Games with an AFK-to-bot takeover | < 3% |
| Support/Warden pick rate in role queue | ≥ 18% of queue entries without Fill Bonus |
| Crash rate | < 0.5% of sessions |

## 16. Risks and how we handle them

| Risk | Mitigation |
|---|---|
| Network effects: players stay where their friends are | Lean into regions underserved by competitors' servers or pricing; strong referral and squad-up rewards; launch Skirmish as an easy entry point |
| The tide feels random or gimmicky | The tide is fully predictable and visible. If prototype players can't plan around it, we cut or simplify it before alpha |
| Small launch roster | Attunements double effective variety; fast hero cadence after launch |
| Short matches feel shallow to veterans | Depth lives in tide timing, Shrine choices, and Attunements, not in farm time. Track veteran retention separately |
| Revenue without power sales | Proven cosmetic-led models in the genre; premium Tide-reactive skins as the flagship product |
| Large IP competitors outspend us on marketing | Creator program, community tournaments from day one, and a game that is easy to clip and share |

## 17. Open questions

1. Should the jungle stay role-less, or does the high-ranked game need a dedicated jungler?
2. Is 2 minutes the right tide interval, or should it speed up as the match goes on?
3. Do we allow team free-text chat in Ranked at all?
4. Do we need an original IP partnership or a transmedia plan (animated shorts) to compete for attention with established franchises?
5. Should Skirmish (3v3) count toward a separate ranked ladder?

## Next steps

1. Build the graybox prototype: map, tide system, 6 heroes, bots.
2. Run internal playtests comparing matches with and without the tide to confirm it improves pacing.
3. Write detailed kits for the first 15 heroes.
4. Draft the Attunement and item lists and simulate gold and XP curves to hit the 12–13 min target.
