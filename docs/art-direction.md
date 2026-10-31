# Tidebreak — Art Direction & Visual Development Plan

> Companion to the [game concept](game-concept.md). Version 0.1.
> Target engine: Unity 6 LTS, Universal Render Pipeline (URP).

This document sets how Tidebreak looks, and the visual work we finish **before production code starts**. In a mobile MOBA the art isn't decoration: it decides whether players can read a fight on a six-inch screen, and it sets the performance budget every system has to live within. So we lock the look first.

## 1. Order of work: what we decide before code

Some visual decisions shape everything after them. We make them in this order:

1. **Camera and scale.** How big a hero is on screen decides texture sizes, ability ranges, map dimensions, and UI layout.
2. **Readability rules.** Which colors, shapes and values are reserved for gameplay information.
3. **The water.** It's the game's signature and its most expensive visual system. It must show three states and a reversible direction, cheaply.
4. **Character language.** Silhouettes and shape language per class.
5. **The visual target.** One finished slice of the map, in Unity, running on a budget phone.
6. **Production pipelines.** Budgets, naming, import settings, and quality tiers that every artist and programmer works within.

Steps 1–5 are done in a **Unity look-dev project** using shaders, scene setup, and Timeline only. No gameplay code is needed. Gameplay prototyping happens in parallel with graybox art and throwaway code (see the concept document's launch plan).

## 2. Visual pillars

1. **Readable at arm's length.** Every frame must answer three questions in under a second: where am I, where are they, what's about to hit me.
2. **The sea is the star.** Land is warm and calm so the water, which carries gameplay information, can be the most alive thing on screen.
3. **Painterly, not noisy.** Big shapes, soft gradients, hand-painted texture with restraint. Detail goes where the eye should go.
4. **One world, two cities.** The two sides of the map feel like rival cultures, without ever competing with the blue/red team colors.

## 3. Camera and scale

| Parameter | Starting value (to be tested) | Why |
|---|---|---|
| Projection | Perspective, narrow field of view (~30–35° vertical) | Near-orthographic clarity with some depth |
| Pitch | ~50° down | Shows hero faces and weapons, keeps ground readable |
| Hero height on screen | ~10% of screen height on a 6.1" phone | Large enough for silhouettes and animation to read |
| Hero offset | Own hero sits slightly below screen center | More view in the direction of the enemy base |
| Team flip | Red team's camera rotated 180° | Both teams see their own base in the bottom-left |

**Consequences of the team flip for art:**
- Every area of the map must look good from both directions. No "back side" of props.
- The key light is high and only slightly angled, so the lighting doesn't feel wrong from either side.
- Directions are named by landmark (Cliffs, Mangroves), never "up/down", and the current arrow on the HUD is drawn relative to each player's screen.

**Camera test (Phase 0):** build the graybox map with simple capsules for heroes, capture screenshots at the target camera settings, and view them on real phones (a budget Android and a small iPhone) at arm's length. Adjust before any other art is made.

## 4. Readability rules

These are reserved for gameplay information and environment art may not use them:

| Channel | Reserved for | Environment rule |
|---|---|---|
| Saturated blue / cyan | Allies, ally abilities | Environment blues stay desaturated (sea teal, slate) |
| Saturated red / orange | Enemies, enemy abilities | Environment warm colors stay earthy (sand, coral, terracotta) |
| Pure white, high brightness | Ability telegraphs, hit flashes, the current's foam lines | Environment highlights capped below this brightness |
| Chevron and arrow shapes | The river current's direction | Never used as decoration |
| Hard-edged ground circles | Ability areas | Environment ground decals use soft edges |

**Value structure:** ground is mid-value and low-contrast; heroes are higher-contrast with a rim light; effects are the brightest thing on screen. A grayscale screenshot of a teamfight should still read.

**Colorblind support:** team colors have three presets (default, deuteranopia/protanopia, tritanopia). The current never relies on color alone: it's shown with shape (chevrons), motion (foam and debris moving), and sound.

## 5. The world on the map

**Two cities, one coast.** The two bases belong to rival city-states. Their identities come from materials and shapes, not from team colors:

| | **Solmere** (one base) | **Gloam Harbor** (the other) |
|---|---|---|
| Inspiration | Sun-bleached Mediterranean and Southeast Asian port towns | Volcanic island fishing ports, lantern festivals |
| Materials | White stone, terracotta, coral, brass | Black basalt, weathered wood, paper lanterns, sea-glass |
| Shapes | Domes, arches, round towers | Stacked angular roofs, stilts, tall masts |
| Accent color | Warm gold | Soft lantern teal-green |

Because the teams' cameras flip, each player sees their own city at the bottom-left. Which city you belong to is chosen by the side you're placed on, and allies/enemies are still marked with blue/red outlines and health bars.

**Zones:**

| Zone | Look | Readability note |
|---|---|---|
| **Cliff lane** | Pale cliffs, wind-bent pines, gull nests, crashing surf on the outer edge | Surf animates gently so it never looks like an ability |
| **Causeway** (mid) | A half-sunken stone road with broken statues of old tide-priests | Statues fade out (dithered) when a hero is behind them |
| **Mangrove lane** | Root tangles, boardwalks, tidepools, fireflies at Surge | Roots stay below hero waist height near the lane |
| **Jungle** | Coastal forest: palms, ferns, giant shells, coral outcrops (the "reef walls" Grothmaw can burrow through) | Brush has a clear painted border so players know exactly where hiding starts |
| **River** | The Vein: a wide tidal channel with sandbars at low tide | See section 6 |
| **Spillways** | Carved stone channels from the river into the jungle | Dry and dusty at low tide or upstream; white water downstream |

## 6. The water: the signature system

The water carries the game's most important information. Its visual design comes before any other environment work.

### Requirements

1. Show three states clearly: **low tide** (shallow, still), **high tide** (deep, flowing one way), and **the Turn** (slack, then churning, then committing).
2. Reverse direction in real time, smoothly, across the whole river.
3. Read in under one second, in grayscale, on a budget phone.
4. Cost no more than ~15% of the frame budget on the low tier.

### Look by state

| State | Look |
|---|---|
| **Low tide** | Clear turquoise shallows over warm sand; sandbars exposed; caustic light patterns (high tier); tidepools glinting. Calm, inviting, warm. |
| **High tide** | Deeper teal, the sandbars gone. Strong **current lines**: chevron-shaped foam streaks pointing downstream, floating debris (driftwood, kelp, lanterns) moving with the flow, spray where water hits rocks on the downstream side. |
| **The Surge** | Sky turns overcast with gold and magenta breaks; water darkens; foam brighter; occasional distant lightning. The game feels like it's building to a finale. |

### The Turn, shot by shot

| Time | Visual | Audio | HUD |
|---|---|---|---|
| −15 s | Water starts to pull back from the shore slightly | Low swell begins | Tide clock pulses |
| 0.0 s | **Slack water:** level rises; all current lines and debris stop; ripples go circular | Everything hushes, a single held tone | "THE TIDE TURNS" |
| 1.0 s | **Churn:** whirlpools open along the river; debris spins in place | Rumble builds, panned to the center | — |
| 2.5 s | **Commit:** a white surge wave rolls from the upstream end to the downstream end | Rushing water, panned in the direction of flow on stereo devices | Arrow appears on the HUD and minimap |
| 3.0 s+ | Current lines and debris stream downstream; spillways burst open with white water | Steady current loop | Arrow stays on the minimap for the rest of the high tide |

The design rule: during slack water and the churn, **nothing hints at the direction**. The whirlpools are symmetrical, and the audio stays centered.

### Technique in Unity (URP)

- **Flow maps:** two baked flow maps for the river, one per direction (toward the Cliffs, toward the Mangroves). A single global shader value from −1 to +1 blends between them. Slack water is 0. Reversal is one number animating over time, so the whole river turns at once at almost no cost.
- **Current lines:** a chevron pattern texture scrolled along the flow map. It's a shape, not just a color, so it reads in grayscale and for colorblind players.
- **Tide height:** a global "tide level" value drives both the water surface height and a wet-sand mask in the terrain shader, so the shoreline darkens and shrinks as the tide rises.
- **Debris:** GPU-instanced meshes moving along splines down the river; their direction follows the same global value.
- **Foam:** shoreline foam from a baked distance-to-shore texture; spillway white water from simple flipbook particles.
- **Built with Shader Graph**, with a hand-written HLSL fallback for the low tier if Shader Graph output is too heavy.

### By quality tier

| Feature | Low | Medium | High / 120 fps |
|---|---|---|---|
| Flow maps + chevrons | Yes | Yes | Yes |
| Tide height + wet sand | Yes | Yes | Yes |
| Debris | 20 objects | 40 | 80 |
| Depth coloring | Painted vertex color | Depth texture | Depth texture |
| Refraction / caustics | No | No | Yes |
| Reflections | Baked cube map | Baked cube map | Planar reflection of the sky only |

Everything that carries **information** (chevrons, debris direction, tide height) exists on every tier. Only the beauty layers scale down.

## 7. Characters

### Shape language by class

| Class | Base shape | Silhouette traits |
|---|---|---|
| **Vanguard** | Squares | Broad shoulders, low center of mass, heavy weapons or shells |
| **Striker** | Triangles | Forward lean, pointed weapons, flowing cloth that trails movement |
| **Arcanist** | Circles and spirals | Floating elements, glowing focus objects, robes |
| **Marksman** | Long horizontals | Long weapons held across the body, light builds |
| **Warden** | Verticals and a light source | Staffs, lanterns, banners; each carries a visible light |

Positions (like Jungle) have **no visual language**, because any class can play them. A jungle-natural hero looks like their class.

### Rules

- **Proportions:** about 5–6 heads tall. Heads, hands, and weapons are oversized for readability.
- **Silhouette test:** every hero concept is shown as a solid black shape at 64 px tall. It must be recognizable and distinct from every other hero.
- **Color blocking:** 60% main color, 30% secondary, 10% signature accent. No hero's main color may be a saturated team blue or red.
- **Animation:** strong anticipation poses on every ability (the "tell" players react to), snappy follow-through, idle animations that reflect personality.
- **The tide on characters:** characters get a wet sheen and dripping particles when standing in river water. It's a small detail that reminds players where they are.

### Skins

- A skin may change everything except the **silhouette class**, **ability telegraph shapes**, and **team color outlines**.
- Every skin passes the same 64 px silhouette test and a "teamfight screenshot" readability review.
- **Tide-reactive** premium skins change visuals between low tide, high tide, and the Turn (for example, a coral armor that blooms at high tide).

### Character budgets

| | Low tier | Medium | High |
|---|---|---|---|
| Triangles (in-game) | ~4k | ~8k | ~12k |
| Texture | 512² | 1024² | 1024² + detail mask |
| Bones | 45 | 60 | 60 |
| Max heroes animated on screen | 10 + minions | 10 + minions | 10 + minions |

Lobby, shop, and splash models use separate higher-detail versions loaded only on those screens.

## 8. Effects (VFX) language

- **Team color edges on every telegraph:** the outline of an ability area is always ally blue or enemy red, even if a skin changes the fill.
- **Shape grammar:**
  - Solid hard edge: damage lands here.
  - Dashed edge: something is coming; get out.
  - Filling area: a timer; when full, it triggers.
  - Arrow: a dash or projectile path.
- **Brightness budget:** the brightest effects are reserved for ultimates and crowd control. Basic attacks are subtle.
- **Water-themed abilities** must not use chevron shapes, so they can't be confused with the current.
- **Performance:** Unity's Particle System for broad device support (VFX Graph only for menus on high-end devices). Strict overdraw budgets: transparent particles may cover no more than about 1.5× the screen on the low tier during a full 10-hero teamfight.

## 9. HUD and UI

- **Theme:** nautical instruments — brass rings, tide gauges, compass marks — kept flat and minimal in-match, richer in menus.
- **Tide clock:** a ring around the match timer that fills like a rising wave, turning into the direction arrow at the Turn.
- **Thumb zones:** abilities in the bottom-right arc, movement stick bottom-left, minimap top-left, information along the top. Nothing important under the thumbs.
- **Health bars:** team color with clear segments; the player's own bar is distinct (gold border).
- **Text:** minimum 11 pt on the smallest supported phone; one clear sans-serif typeface for gameplay, a display face with a hand-lettered feel for titles.

## 10. Audio direction (briefly)

The tide is information, so it's also a sound.

- The river's sound changes by state: lapping at low tide, a steady rush at high tide.
- The Turn has its own audio signature (hush, rumble, rush) and stays centered until the commit.
- On stereo devices, the commit wave pans in the direction of flow.
- Each city has its own music motif, and the Surge combines them.

## 11. Unity setup for art

| Area | Setting |
|---|---|
| Render pipeline | URP, Forward rendering; Forward+ evaluated for the high tier |
| Lighting | Baked lightmaps and light probes for the environment; one realtime directional light for hero shadows on medium/high; blob shadows on low |
| Post-processing | Color grading on all tiers; bloom on medium/high only; no depth of field or motion blur in matches |
| Anti-aliasing | FXAA on low, 2× MSAA on medium/high |
| Batching | SRP Batcher on; GPU instancing for foliage, debris, and minions |
| Texture compression | ASTC (4×4 for heroes and UI, 6×6 for environment) |
| Content delivery | Addressables groups: core map + launch heroes in the install; skins and high-resolution packs downloaded on demand |
| Shaders | Shader Graph with a small shared library (toon-ramp lit, environment, water, foliage); custom HLSL only where profiling demands it |
| Cinematics | Timeline + Cinemachine for trailers, splash screens, and hero intros |

### Quality tiers

| Tier | Example device class | Target | Render scale |
|---|---|---|---|
| **Low** | 3 GB RAM Android, 2021+ budget chip | 30 fps | 0.75 |
| **Medium** | Mid-range Android, older iPhones | 60 fps | 0.85–1.0 |
| **High** | Recent flagships | 60 fps | 1.0 |
| **Ultra** | Flagships with 120 Hz screens | 120 fps | 0.85–1.0 |

The game picks a tier automatically from a device list and a short benchmark, and players can change it.

### Frame budgets (low tier, full teamfight)

| | Budget |
|---|---|
| Draw calls | < 150 |
| Triangles on screen | < 250k |
| Water | ≤ 15% of frame time |
| Memory (whole game) | < 1 GB on a 3 GB device |

### Art toolchain

- **Concept:** Photoshop or Procreate.
- **3D:** Blender (or Maya if the team prefers), with hand-painted and Substance 3D Painter textures.
- **Flow maps:** painted in a flow-map tool or generated in Houdini from the river spline.
- **Naming, import presets, and folder structure** documented in the art bible and enforced by Unity asset-import scripts.

## 12. Phase 0: visual development plan (months 0–4)

| Step | Weeks | Output | Done when |
|---|---|---|---|
| 1. Art bible and mood boards | 1–4 | Pillars, references, color palettes, the two cities, readability rules | Art director, game director, and lead tech artist sign off |
| 2. Camera and scale test | 3–6 | Graybox map in Unity with capsule heroes; screenshots and paintovers at target camera | Heroes and ranges read on real phones at arm's length |
| 3. Hero silhouettes | 4–10 | 3–5 concepts for each of the 8 prototype heroes; class lineup sheet | Every hero passes the 64 px test and is distinct from the others |
| 4. Water and the Turn | 4–12 | Storyboard and animatic of the Turn; flow-map water shader in a look-dev scene with a direction slider | Testers name the direction within 1 s of the commit, including in grayscale, on a low-tier phone |
| 5. The visual target ("beauty corner") | 10–16 | One jungle quadrant, a river section with spillways, and 2 heroes (Isra Coil and Kesh Varo) at final quality, all tide states, playable with a simple scripted Turn | Runs at 30 fps on the low-tier reference phone within the frame budgets |
| 6. Readability playtest | 14–16 | Screenshot and video tests of mid-fight moments | 9 out of 10 testers find their own hero, the enemy, and the current direction in under 1 s |
| 7. Pipeline documentation | 12–16 | Budgets, import presets, naming, quality-tier settings, skin readability checklist | Ready for production artists and gameplay programmers |

**Gate:** production gameplay code begins only when the visual target runs within budget on the low-tier phone and passes the readability playtest. Anything that fails changes the art plan before it changes the code plan.

### Phase 0 team

| Role | Count | Focus |
|---|---|---|
| Art director | 1 | Owns the vision and the gates |
| Concept artists | 2 | Cities, zones, heroes, the Turn storyboard |
| Technical artist | 1–2 | Water, shaders, quality tiers, Unity pipelines (the most critical hire) |
| Environment artist | 1 | The beauty corner |
| Character artist / animator | 1 + 1 | The two visual-target heroes |
| VFX artist | 1 | Telegraph language and the Turn |
| UI/UX designer | 1 | HUD, tide clock, thumb-zone layout |

## 13. Risks

| Risk | Mitigation |
|---|---|
| The water costs too much on budget phones | Information layers are cheap by design; beauty layers scale by tier; profile on real devices from week 4 |
| The Turn's random direction is hard to read instantly | Shape + motion + sound + HUD arrow all say the same thing; tested in grayscale |
| Painterly style becomes muddy at phone size | Value-structure rules and grayscale checks; reduce texture detail rather than add it |
| Skins break readability | Fixed telegraph shapes and team outlines; every skin passes the same checks |
| The flipped camera exposes unfinished "back sides" | All environment work is reviewed from both team views |
