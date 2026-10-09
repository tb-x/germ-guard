# Germ Guard

A tower defence game set inside the body, for young kids (around age 5). Germs sneak into the body
and wiggle along blood vessels towards the heart. Your child builds white blood cells beside the
vessels to stop them before they get there.

It has ten levels on a body-shaped map, an endless Germ Party, seven ways to defend, a sneeze, and seven kinds of
germ, including a King Germ boss. A Germ Book collects everything your child meets, and stars dress up the heart.
A friendly recorded voice explains everything as you go. It has music and vibration, and it can be added to the
Home Screen and played offline.

## The levels

1. **Scraped Knee** 🦵: germs come in through one scratch. Only zappers, to learn the game.
2. **Runny Nose** 👃: germs come out of both nostrils, down two vessels that merge before the heart.
   Adds the blob nest and the sneeze button.
3. **Tummy Ache** 🍔: germs come in through the mouth, and a second mouth halfway down sends fast ones on a shortcut.
   Adds the antibody maker, Wigglers and Chunkies.
4. **Lungs** 🫁: germs come three ways at once. Adds snot puddles, Corkscrews and Spikies.
5. **Itchy Eye** 👁️: two vessels run along the upper and lower eyelids round a big blue iris, so your child has to
   guard both sides.
6. **Earache** 👂: one long vessel spirals in to the heart in the middle. Pads sit between the rings, so a defender
   there reaches two rings at once. The germs here are extra tough.
7. **Big Fever** 🤒: germs pour in through the nose, the mouth and a scratch, all at once, every kind mixed together.
   The heart is sweating and heat shimmers off the tissue. The last wave brings the **King Germ**.
8. **Cut Finger** ✋: a bigger board. Germs get in through two little cuts whose vessels join, then zigzag a long
   way to the heart, with spots in the bends that reach two stretches at once. Every kind of germ except the King.
   Adds the **platelet plug**: tap the vessel to block it.
9. **Sore Throat** 😮: bigger again. Two ways in from the mouth join and wind down; from wave 2 germs also come in
   through the nose, which joins further down. Snot puddles help, and two **tonsils** guard the throat by themselves.
10. **Chickenpox** 🐔: the biggest board, with the heart in the middle. Germs come from four itchy spots, two above
   and two below, each pair joining and winding in from its side. Adds the **memory cell**. The last wave brings
   **two King Germs**.

Levels 8 to 10 are big enough that on a small phone they start a little zoomed in; pinch or scroll to see the rest.
The first seven boards were also made a little bigger: each entry's vessel is three tiles longer (except the eye,
whose entries sit in the corner of the eye), with an extra building spot beside it, and a ring of tissue around
the edge.

## The map and saving

The title screen is a map: a child's body with a glowing spot for each level (knee, nose, tummy, lungs, the left
hand for the finger, the right arm for chickenpox, and next to the head the eye, the ear, the throat and a
thermometer for the fever). Tap a spot to play it. **Play** jumps to the newest unlocked level.

- Winning a level unlocks the next spot. Locked spots show a padlock, and the next one to play glows.
- The best stars for each level (1 to 3, from the hearts left at the end) show under its spot.
- Progress is saved in the browser (`localStorage`): `germguard.stars` keeps the best stars per level name, so
  levels can be added or reordered later. A level opens once the one before it is won. The sound and vibration
  settings are saved too, and so are the Germ Book (`germguard.book`), what the heart wears (`germguard.dress`) and
  the best Germ Party (`germguard.partyBest`).
- The map button in the corner during a level, and on the end card, goes back to the map.

Under **Play** are three more buttons:

- **📖 Germ Book**: a page for every germ and every defender, with a picture and a few words. Tap one to hear the
  voice say what it is. Ones your child hasn't met yet are dark shadows with a "?". Levels already won count as met.
- **🎀 Dress up**: stars won on the levels unlock things for the heart to wear in every level: a party hat (3 stars),
  a bow (6), sunglasses (10), a flower (14), a crown (18) and headphones (22), and colours: pink (8), purple (16)
  and gold (26). There are 30 stars in all. Locked things show how many stars they need.
- **🎉 Germ Party**: opens once the Big Fever is won. An endless game on the Chickenpox board with every defender:
  the waves never stop, each one bigger and tougher than the last, with a King Germ every fifth wave. When the heart
  runs out, the card says how many waves your child stopped, and the best ever shows on the 🎉 button.

## The defenders

- **Germ zapper** (a neutrophil, 5 drops): shoots little bubbles at germs in reach.
- **Blob nest** (a home for macrophages, 6 drops): comes with one blob, and you can train up to 3 (2 drops each).
  Each blob guards its own spot: the first takes the best tile near the nest (where vessels merge, if there is one),
  and the others spread out at least two tiles apart, onto different vessels where they can, so one nest covers
  several stretches instead of crowding one corner. They grab a germ,
  hold it still and gobble it up. A tired blob lets go, waddles home for a short rest and comes back.
  Blobs never get hurt.
- **Antibody maker** (a B cell, 6 drops): throws Y-shaped antibodies that stick on germs. A germ with an antibody
  on it walks slower and pops faster, and a Spiky loses its armour. The maker picks germs that don't have an
  antibody yet, Spikies first.
- **Snot puddle** (4 drops, up to 3 per level, Lungs level): tap the vessel itself to drop one. Every germ that
  wades through it slows right down.
- **Platelet plug** (5 drops, up to 2 at a time, Cut Finger and the Germ Party): tap the vessel itself. Germs have
  to stop at it and chew; the two at the front chew it away, faster for big germs and the King, and then it crumbles
  and can be built again. Germs queue up behind it, which makes them easy to zap.
- **Tonsils** (Sore Throat): two pink lumps beside the throat that you don't build. Every 2 seconds they squeeze, which
  hurts every germ near them. They can't hurt a Spiky until an antibody sticks on it.
- **Memory cell** (6 drops, Chickenpox and the Germ Party): it remembers every kind of germ your child has ever
  beaten (saved as `germguard.beaten`), and a brand-new kind after 3 of them pop on the level. It throws gold
  antibodies at remembered germs, two at a time: like an orange one, it slows the germ down and breaks a Spiky's
  armour, but the germ takes more than twice the damage instead of one and a half. It can swap an orange antibody for
  a gold one. Its two upgrade paths are Reach and Speed (faster, then three at a time).
- **Sneeze** 🤧 (from Runny Nose on): during a wave the Go button turns into a sneeze button. It blows every germ
  back down the vessels. Then it needs 40 seconds to recharge, shown as a shadow sweeping round the button.
  The first time germs get close, a pointing hand and a voice remind your child it's there.
- **Upgrades**: tap a built defender to improve it. Every defender has two upgrade paths, and each path can be taken
  twice, so a fully upgraded one has four upgrades. The card shows the path's sign and how far along it is:

  | Defender | Path | Does | Drops | Looks |
  | --- | --- | --- | --- | --- |
  | Zapper | Reach ◎ | shoots further | 5, 8 | blue rings round the base that pulse like sonar |
  | Zapper | Power ⚡ | shoots faster, then harder | 6, 9 | extra purple lobes, then a soft lavender glow |
  | Blob nest | Bite 🦷 | its blobs chomp harder (and grow) | 6, 9 | a red flag on the roof, then a gold one |
  | Blob nest | Energy 🔋 | its blobs hold on longer before they tire | 5, 8 | a chimney, then puffing smoke |
  | Antibody maker | Reach ◎ | throws further | 5, 8 | blue rings round the base |
  | Antibody maker | Speed ⚡ | throws faster, then two at once | 6, 9 | more antennae, then a golden glow |

  For every defender the base also turns silver after the first upgrade and gold after the third, and a gold star
  circles overhead for each upgrade. A tapped nest also offers **Train** (+) while it has room for more blobs.
- **Selling**: a tapped defender or snot puddle also offers a red ✕ card showing the drops you'd get back (three
  quarters of everything spent on it). The first tap turns the card into "sure?", and only a second tap sells it,
  so a stray tap can't undo your child's work. The drops pop out and the pad is free again.

## Learning about the body

The game names the real body parts and cells, and says what they do:

- **First time each defender is placed:** its real name floats above it (Neutrophil, Macrophage, B cell, Mucus) and
  the voice explains what it does. For example: "This is a neutrophil, a kind of white blood cell. Neutrophils rush to
  germs first and zap them!" The build cards also show the real names, for a parent to read out.
- **First sneeze:** "A sneeze blows germs out of your nose. Remember to sneeze into your elbow!"
- **Platelets, tonsils and memory cells** each get a voice line the first time they're used: platelets plug a cut
  to stop the bleeding, tonsils guard the back of the throat, and memory cells remember germs your body has beaten.
- **Every win card** shows and reads out a "Did you know?" fact about that body part: why a cut goes red and warm,
  how snot traps germs, stomach acid and hand washing, the tiny hairs that sweep mucus out of the airways, the germ
  fighters in tears, what earwax is for, and why a fever helps (plus "rest and drink water").

- **Picture cards**, only for what a level brings that no earlier level had, shown between waves with one big OK:
  - a **new defender** gets a picture strip of what it does (zapper ➜ bubble ➜ germ 💥; nest ➜ blob ➜ germ; antibody
    maker ➜ Y ➜ germ 🐢; snot ➜ germ 🐢) and one short sentence;
  - a **new germ** gets a card with one row per defender on that level, marked ✓ (works), ✗ (doesn't) or ⭐ (the
    special answer). The Spiky card, for example, shows the zapper ✗ "bounces off", the nest ✗ "won't grab it", the
    antibody maker ⭐ "breaks its armour!" and snot ✓ "slows it down". The Chunky card also shows it splitting in 3.

  So the Knee shows the zapper and, before wave 4, the Big Bloop; the Nose the nest; the Tummy the antibody maker,
  the Wiggler and the Chunky; the Lungs snot, the Corkscrew and the Spiky; the Fever the King Germ before its last
  wave. The Eye and the Ear bring nothing new, so they show no cards. The words and marks are in `DEFENDER_TIP`,
  `GERM_TIP` and `HOW`.

Each explanation plays once per visit, like the germ introductions. The words are in `LINES` (`meet-*`) and each
level's `fact`.

## The germs

| Germ | Looks like | What's special |
| --- | --- | --- |
| Bloop | green blob | the plain one |
| Big Bloop | bigger green blob | tough and slow |
| Wiggler | yellow striped sausage | fast and fragile |
| Corkscrew | teal spinning spring | too wiggly for blobs to grab |
| Chunky | lumpy olive cluster | tough; breaks into 3 Bloops when popped |
| Spiky | purple ball with spikes | shots bounce off, and blobs won't grab it, until an antibody sticks; then its spikes shrink |
| King Germ | huge grumpy blob with a gold crown | the boss: very tough, slow, tires blobs fast, breaks into 4 Bloops, and costs 3 hearts if it gets through |

The first time a new kind shows up in a wave, the voice says what's special about it.

## How it plays

- Glowing pads sit beside the vessels. Tap one to see what you can build. The price shows as drop icons 💧,
  and anything you can't afford yet is greyed out.
- A bubble over each entry shows which germs come out of it next. Tap **Go!** when ready. Waves never start on their own.
- Popped germs drop energy drops. Tap them to collect, or they fly to the counter by themselves after a few seconds.
- Each cleared wave adds 3 bonus drops from the heart. Drops are scarce, so where and what you build matters.
- The heart has 5 hearts of health. A germ that reaches it costs one (and earns the heart a plaster).
- **New building spots open up as a level goes on:** before wave 3 and again before wave 5, an extra pad springs up
  with sparkles and a chime, and the pointing hand shows where it is. The later one is the better spot, ready for
  the hardest wave. In the maps they're the letters `c` and `e` (any of `b` to `e` opens before wave 2 to 5).
- **The heart's health** shows in three places: the hearts in the top bar, a row of hearts floating over the heart
  itself, and the heart: a plaster for every germ that got through, and a face that goes from smiling to straight
  to worried. Each hit floats up a "💔 -1" (or -3 for the King Germ). On its very last heart, the heart races and
  both heart rows pulse red.
- During a wave, the **2×** button next to the sneeze makes everything run twice as fast; tap again for normal speed.
  It stays on for later waves until turned off.
- If all 5 are gone: "Achoo!" and **Try again** replays that wave. Every defender and drop is kept and the heart is refilled.
- Clear all 5 waves to win. You get 1 to 3 stars depending on how many hearts are left.
- A pointing hand and a spoken voice show where to tap first on each level.
- **Zoom and scroll**: pinch (or use the mouse wheel) to zoom in and out, and drag the board to scroll around it.
  A quick tap still builds; a finger has to move a little before it scrolls instead. While zoomed in, a 🔍 button
  under 🏠 glides back out to the whole board. Each level starts showing the whole board, unless the board is so
  big that its tiles would be tiny: then it starts zoomed in on the first spot to build on. When a new building spot
  opens off screen, the view glides over to it, and the bubbles for entries that are scrolled away stay at the edge.
- 🏠 in the corner goes back to the list of all games.

## Sound, music and vibration

- **Voice**: every spoken line is a recorded clip (see the audio credits below): level introductions, wins, what
  each new germ does, and hints. Lines that come one after another queue up instead of cutting each other off.
  If a clip can't load (for example when the game is opened straight from disk), the browser's own voice says it.
- **Sound effects**: the sneeze, a blob's chomp, a germ's pop, the heart's bonk, the King Germ's arrival and the
  win fanfare are recorded clips. Everything else (shots, building, drops and so on) is synthesized with Web Audio,
  and each recorded effect has a synthesized fallback.
- **Music** is made up in code, no recordings. Every body part has its own little tune: a chiptune hop for the
  Knee, sniffly plucks for the Nose, a wobbly polka for the Tummy, a soft flute for the Lungs, twinkly bells for
  the Eye, an echo for the Ear and a hot, jumpy one for the Fever. The map has its own tune, and the King Germ
  has a grumpy minor-key march. While building a tune plays slow and gentle; in a wave it speeds up with drums
  and a bouncier bass. It dips while the voice talks and stops for the win and lose jingles.
- The 🎵 button next to Play turns the music off (sounds and voice stay on), and is remembered.
- The 🔊 button mutes everything: effects, music and voice. Audio starts with the first tap, and on an iPhone
  the silent switch mutes it.
- **Vibration** comes on building, upgrading, the sneeze, a germ reaching the heart, the King Germ arriving, and
  winning or losing. It works on Android. On iPhone (iOS 18+) it uses the system tap trick from Matma, which only
  works right after a touch. The 📳 button next to Play turns it off, and it only shows on devices that can vibrate.
- The screen gives a little shake when the heart is hit, on a sneeze, and when the King Germ arrives.

## Home Screen and offline

The game has a web app manifest, icons (`icon.svg`, plus `icon-180.png` and `icon-512.png` rendered from it in
headless Chrome) and a service worker (`sw.js`, the same as the other tb-x games apart from its cache prefix
`germ-guard-`). After one visit it works without internet, including three.js and the font. Because it serves
from the cache first and refreshes in the background, a new version shows up one launch late.

## Running it

Serve the folder and open it in a browser:

```bash
python -m http.server 5209
```

Then go to http://localhost:5209/. Opening `index.html` straight from disk mostly works too.

For testing, add `#debug` to the URL. The browser console then has a `gg` handle:

- `gg.loadLevel(i)` loads a level.
- `gg.build(padIndex, 'zapper' | 'nest' | 'antibody')`, `gg.upgrade(padIndex, path)` (`'reach'`, `'power'`, `'bite'`, `'energy'` or `'speed'`; without a path, the one that makes it bigger), `gg.train(padIndex)` and
  `gg.trap(col, row)` build and improve defenders.
- `gg.spawn(kind, entry, dist)` adds a germ.
- `gg.sneeze()` sneezes.
- `gg.unlockAll()` opens every level on the map, and `gg.goHome()` goes back to the map.
- `gg.step(seconds)` runs the game forward without waiting.
- `gg.game.instant = true` makes drops count straight away instead of flying to the counter.

## Tuning knobs

These are at the top of the script in `index.html`:

| Knob | What it does | Now |
| --- | --- | --- |
| `HEART_SPARKLES` | germs the heart can take before the wave is replayed | 5 |
| `WAVE_BONUS` | bonus drops after each cleared wave | 3 |
| `DROP_AUTOCOLLECT_S` | seconds before an untapped drop collects itself | 4 |
| `SHOT_SPEED` | zapper shot speed, in tiles per second | 9 |
| `BUILDS` | for each defender: its cost, and its two upgrade paths (`tracks`), each with a label, sign, the drops for its two steps (`costs`) and the numbers at steps 0-2 (`steps`) | see the upgrades table above |
| `BUILDS.zapper` | Reach: range 2.7, 3.0, 3.3 tiles; Power: seconds between shots / damage 0.85/1, 0.6/1, 0.8/2 | 5 drops |
| `BUILDS.nest` | guard reach 2.3 tiles; Bite: blob damage per second 1.8, 2.4, 3.0; Energy: blob stamina 8, 11, 14 | 6 drops |
| `BUILDS.antibody` | Reach: range 2.8, 3.1, 3.4 tiles; Speed: seconds between throws / germs per throw 1.4/1, 1.0/1, 0.9/2 | 6 drops |
| `TAG_SLOW`, `TAG_DAMAGE` | speed and extra damage for a germ with an antibody on it | 0.7, 1.5 |
| `AB_SPEED` | antibody flying speed, tiles per second | 6 |
| `MUCUS_COST`, `MUCUS_MAX`, `MUCUS_R`, `MUCUS_SLOW` | snot price, puddles per level, reach in tiles, speed inside it | 4, 3, 0.6, 0.4 |
| `PLUG_COST`, `PLUG_MAX`, `PLUG_HP`, `PLUG_CHEW` | platelet plug price, plugs at a time, how much chewing it takes, chewing per second per germ (times its bite) | 5, 2, 36, 2 |
| `TONSIL_R`, `TONSIL_RELOAD`, `TONSIL_DAMAGE` | tonsil reach in tiles, seconds between squeezes, damage per squeeze (tonsils are `t` on a map) | 1.7, 2, 1.5 |
| `MEMORY_KILLS`, `MEMORY_DAMAGE` | pops of a never-beaten kind before memory cells remember it; extra damage with a gold antibody | 3, 2.2 |
| `PARTY_POINTS`, `PARTY_GROW`, `PARTY_TOUGH`, `PARTY_KING_EVERY` | Germ Party: first wave size (a bloop is 1 point), points added per wave, extra toughness per wave, a King every this many waves | 10, 7, 0.1, 5 |
| `PARTY_KINDS` | which germs come to the party, their points, and the first wave each can turn up in | Spikies from wave 5 |
| `DRESS`, `HEART_COLOURS` | what the heart can wear and its colours, with the stars each needs | |
| `SNEEZE_COOLDOWN`, `SNEEZE_PUSH` | seconds to recharge the sneeze, tiles germs get blown back | 40, 5 |
| `FAST_SPEED` | how much faster waves run with the 2× button on | 2 |
| `TROOP_COST`, `TROOPS_PER_NEST` | drops per extra blob, most blobs per nest | 2, 3 |
| `TRAIN_S` | seconds to train a blob | 1.2 |
| `TROOP_SPEED` | blob walking speed, tiles per second | 1.8 |
| `TROOP_GUARD_R` | how close to its post a blob grabs germs, in tiles | 1.0 |
| `TROOP_SPREAD` | how far apart a nest's blobs stand, in tiles | 1.9 |
| `TROOP_REST_S`, `TROOP_RECOVER` | rest time when tired; stamina regained per second while waiting | 4 s, 1 |
| `CHOMP_S` | seconds between blob bites | 0.4 |
| `GERMS` | health, speed, drops, size, how fast each germ tires a blob, and its special trick | see the table above |
| `GERM_HELLO` | what the voice says the first time each germ appears | |
| `SELL_REFUND` | share of everything spent that selling gives back (rounded down) | 0.75 |
| `CAM_PITCH` | camera angle above the ground, in degrees | 38 |
| `ZOOM_MIN_TILE` | a board whose tiles would show smaller than this (pixels) starts zoomed in; every current level fits even on a small phone | 20 |
| `ZOOM_MAX_TILE` | zooming in stops when a tile is this many pixels wide | 130 |
| `DRAG_START` | how far a finger moves (pixels) before a tap turns into scrolling | 12 |
| `MUSIC_VOL`, `MUSIC_DUCK` | music level, and how far it dips under the voice | 0.22, 0.35 |
| `SONGS` | each tune: key, scale, tempo, lead sound, bass and drum pattern, a chord per bar and the melody written as scale degrees (8 eighths a bar) | 96–120 bpm |
| `LEADS`, `BASSES`, `DRUMS` | the lead sounds, bass patterns and drum patterns the tunes pick from | |
| `ASSET_V` | bump after replacing any file in `assets/`, so phones fetch the new clips | 2 |
| `CLIP_VOL`, `VOICE_VOL` | sound-effect clip level and voice level | 0.8, 1 |
| `CLIP_TRIM` | per-clip volume trims, measured to even out the clips; lower one if a sound is too loud | |
| `SNEEZE_PEAK` | seconds into the sneeze clip where the "CHOO" lands, when the germs get blown back | 1.0 |
| `LINES` | the words for every voice line (the clip is `assets/say-<key>.mp3`) | |

Each level in `LEVELS` has its own map, colours (`palette`), entry look (`entry`: one style, or a list with one per entry), starting drops
(`startEnergy`), allowed defenders (`builds`, plus `mucus` and `sneeze` switches), the first-tap hint, an optional
`toughness` that multiplies every germ's health (Knee 1.35, Nose 1.25, Tummy 1.1, Earache 1.6, Finger 2.15, Throat 1.5, Chickenpox 1.4), its spot on the map, and `waves`.
The intro and win words are also voice lines, so changing them means recording new clips.
A wave is a list of groups: germ kind, how many, seconds apart, an optional start delay, and which entry they
come from (`from`, 0 = the map's `1`).
Maps can be any size: the shadows grow with the board, and a board too big to show at a readable size on a phone
starts zoomed in and is scrolled around (a 30 × 30 test board worked).

### Balance as tested with simulated play

Tested on 2026-10-09 with an automatic player in three styles. It plays each level the way a child might, and uses
**Try again** (which keeps everything built) when a wave is lost:

- **Thoughtful** keeps building a mix (zappers first, a nest, then antibody makers, and an antibody maker straight
  away when Spikies are in the next wave), drops snot where vessels merge, takes the new spots when they open, and
  spends spare drops on upgrades. It also sneezes when germs get close.
- **Lazy** builds three defenders and stops.
- **Zappers only** builds and upgrades nothing but zappers.

The numbers are hearts left after each wave; ✗ is a lost wave that was tried again.

| Level | Thoughtful | Lazy | Zappers only |
| --- | --- | --- | --- |
| 1 Scraped Knee | won, 5 5 5 5 5 | lost at wave 3 | (same as thoughtful) |
| 2 Runny Nose | won, 4 4 4 4 4 | lost at wave 3 | won, 5 5 5 5 5 |
| 3 Tummy Ache | won, 4 4 4 4 4 | lost at wave 2 | won, 5 5 5 5 5 |
| 4 Lungs | won, 5 5 5 5 5 | lost at wave 3 | lost at wave 3 (Spikies) |
| 5 Itchy Eye | won, 5 4 4 4 4 | lost at wave 3 | lost at wave 4 (Spikies) |
| 6 Earache | won, 5 5 5 5 5 | lost at wave 2 | lost at wave 4 |
| 7 Big Fever | won, 4 4 4 4 4 | lost at wave 2 | lost at wave 3 (Spikies) |
| 8 Cut Finger | won, 5 5 5 5 4 | lost at wave 2 | lost at wave 4 |
| 9 Sore Throat | won, 5 5 4 4 3 | lost at wave 2 | lost at wave 3 |
| 10 Chickenpox | won, 5 5 5 5 2 | lost at wave 1 | lost at wave 3 |

Tuning so far: the early levels got tougher germs and busier last waves, and the King Germ went from 130 to 340
health. After the boards grew, the Itchy Eye needed 20 starting drops (was 18), the Big Fever 25 (was 23), and the
Tummy Ache's Wigglers now come out of the short second entry a little later. In the Big Fever the King Germ gets
about 71% of the way to the heart. In Chickenpox one of the two Kings nearly makes it (98%), and that wave usually
costs the heart 3. The Knee is still easy on purpose, as the tutorial; stopping early loses everywhere, and the
Spiky levels can't be won without antibodies.

With the platelet plug, the tonsils and the memory cell added, the thoughtful player also drops plugs on the Cut
Finger once germs are coming, and builds a memory cell on Chickenpox from wave 2. The first memory cell only
remembered germs popped on the same level, so on Chickenpox it was worse than the zapper it replaced and the King
wave was lost; now it remembers every germ ever beaten (the King too, from the Big Fever) and throws gold antibodies.
The Germ Party lasted 4 to 14 waves in six simulated runs, usually ending at the first King (wave 5) or around wave 14.

The new big levels first had long, separate vessels with spots that each reached only one of them, and even the
thoughtful player lost there. Joining the entries into a shared vessel that zigzags, with spots in the bends,
fixed that: now a defender in the right place covers two stretches, as on the first seven levels.
The Earache's germs have `toughness: 1.6` and a gentler first wave, after the first version (2.5× health, a
16-germ first wave) turned out to be unwinnable in wave 1.

## Made with

Plain HTML and JavaScript. [three.js](https://threejs.org/) 0.170.0 from jsDelivr draws the isometric
board, and every model is built from simple shapes in code. Music and most sounds are synthesized with
Web Audio; the voice and six sound effects are ElevenLabs clips.

## Audio credits

Voices and sounds: [elevenlabs.io](https://elevenlabs.io). The credit also shows on the game's title screen and end card.
All clips were made on 2026-10-09 with an ElevenLabs **free** plan, so they may only be used non-commercially
and must credit ElevenLabs. The game must stay free (no ads, payments or sponsorship), and the clips are not
covered by any licence on this game's code.

Every clip is listed below.

**Spoken lines** (69 clips): ElevenLabs Text to Speech, stock voice "Jessica" (Playful, Bright, Warm), model Eleven
Multilingual v2, free plan, made 2026-10-09. The words are also in `LINES`, `GERM_HELLO` and each level's `intro`,
`win` and `fact`.

| File | Words |
| --- | --- |
| `say-intro-knee.mp3` | "Oh no, a scratch on the knee! Germs are sneaking in. Tap a glowing spot to build a germ zapper." |
| `say-win-knee.mp3` | "Hooray! You stopped all the germs. The knee is all better!" |
| `say-intro-nose.mp3` | "Achoo! A runny nose! Germs are coming from both sides. Try the new blob nest: its blobs grab the germs and gobble them up!" |
| `say-win-nose.mp3` | "Hooray! No more sniffles!" |
| `say-intro-tummy.mp3` | "Uh oh, a tummy ache! Germs came in with the food. New: the antibody maker. Its antibodies stick on germs, so they slow down and pop faster!" |
| `say-win-tummy.mp3` | "Hooray! The tummy feels great!" |
| `say-intro-lungs.mp3` | "Cough cough! Germs are in the lungs, coming three ways. New: tap the vessel to drop sticky snot there. Germs get stuck in it!" |
| `say-win-lungs.mp3` | "Hooray! Big deep breaths!" |
| `say-intro-eye.mp3` | "Blink blink, an itchy eye! Germs are sneaking along both eyelids. Guard the top and the bottom!" |
| `say-win-eye.mp3` | "Hooray! The eye is bright and clear!" |
| `say-intro-ear.mp3` | "Ouch, an earache! The germs go round and round the ear to reach the heart. Build in between the rings to zap two at once!" |
| `say-win-ear.mp3` | "Hooray! The earache is gone!" |
| `say-intro-fever.mp3` | "Oh no, a big fever! Germs are coming from the nose, the mouth and a scratch, all at once. Use everything you have!" |
| `say-win-fever.mp3` | "You did it! The fever is gone, and the heart feels great!" (re-recorded once levels came after it) |
| `say-intro-finger.mp3` | "Ouch, a cut on the finger! Germs are getting in through two little cuts. The way to the heart is long, so build all along it!" |
| `say-win-finger.mp3` | "Hooray! The finger is all healed!" |
| `say-intro-throat.mp3` | "Ow, a sore throat! Germs are coming in through the mouth, and soon through the nose too. Sticky snot helps here as well!" |
| `say-win-throat.mp3` | "Hooray! The throat feels much better!" |
| `say-intro-pox.mp3` | "Itchy, itchy! Chickenpox spots everywhere, and germs are coming from all four sides. The heart is in the middle. Two King Germs are coming, so get ready!" |
| `say-win-pox.mp3` | "You did it! The spots are gone, and you beat the biggest germ army ever!" |
| `say-hello-big.mp3` | "A big germ is coming! It takes lots of pops." |
| `say-hello-wiggler.mp3` | "Watch out for the wigglers. They are fast!" |
| `say-hello-corkscrew.mp3` | "Corkscrew germs are too wiggly for the blobs to grab!" |
| `say-hello-chunky.mp3` | "A chunky germ! When it pops, it breaks into little ones." |
| `say-hello-spiky.mp3` | "Spiky germs have armour! Stick an antibody on them first." |
| `say-hello-king.mp3` | "Uh oh, it's the King Germ! It's huge. Use everything you have!" |
| `say-go.mp3` | "Here they come!" |
| `say-go-last.mp3` | "Last wave! Here they come!" |
| `say-cleared.mp3` | "Great job! Build more, then tap Go." |
| `say-lost.mp3` | "Achoo! The germs got through. Let's try that wave again!" |
| `say-retry.mp3` | "Build more, then tap Go." |
| `say-again.mp3` | "Here we go again!" |
| `say-first-build.mp3` | "Great! Tap Go when you're ready." |
| `say-nope.mp3` | "Pop germs to get more drops!" |
| `say-sneeze-hint.mp3` | "Quick! Press the sneeze button!" |
| `say-bonk.mp3` | "Bonk! Spiky germs need an antibody maker!" |
| `say-bonk-wait.mp3` | "Bonk! Wait for an antibody to stick on the spiky germ." |
| `say-sell.mp3` | "Tap again to sell it." |
| `say-meet-zapper.mp3` | "This is a neutrophil, a kind of white blood cell. Neutrophils rush to germs first and zap them!" |
| `say-meet-nest.mp3` | "This is a macrophage nest. Macrophages are big white blood cells. Their name means big eater, and they gobble up germs!" |
| `say-meet-antibody.mp3` | "This is a B cell. B cells make antibodies, little Y shapes that stick to germs, so they slow down and pop more easily!" |
| `say-meet-mucus.mp3` | "That's mucus. Grown-ups call it snot! It's sticky, so germs get stuck in it. That's why your nose runs when you have a cold." |
| `say-meet-sneeze.mp3` | "Achoo! A sneeze blows germs out of your nose. Remember to sneeze into your elbow!" |
| `say-meet-plug.mp3` | "These are platelets! They stick together like a plug to stop bleeding. Germs have to stop and chew through them!" |
| `say-meet-tonsil.mp3` | "These are your tonsils! They guard the back of your throat and squeeze the germs that go past." |
| `say-meet-memory.mp3` | "This is a memory cell. It remembers germs you have beaten before, and marks them with gold antibodies, so they pop fast!" |
| `say-memory-remember.mp3` | "The memory cell remembers that germ now!" |
| `say-upgrade-reach.mp3` | "Now it can reach further!" |
| `say-upgrade-power.mp3` | "Now it zaps harder!" |
| `say-upgrade-bite.mp3` | "Now its blobs bite harder!" |
| `say-upgrade-energy.mp3` | "Now its blobs can keep going for longer!" |
| `say-upgrade-speed.mp3` | "Now it makes antibodies faster!" |
| `say-new-spot.mp3` | "Look, a new building spot!" |
| `say-intro-party.mp3` | "It's a germ party! The germs keep on coming. How many waves can you stop?" |
| `say-party-over.mp3` | "What a party! You did so well!" |
| `say-book-hello.mp3` | "This is your germ book. Tap a picture to hear about it!" |
| `say-book-bloop.mp3` | "This is a Bloop, the everyday germ. One bubble pops it!" |
| `say-dress-hello.mp3` | "Dress up your heart! Win more stars to get more things to wear." |
| `say-dress-locked.mp3` | "Win more stars to get this one!" |
| `say-fact-knee.mp3` | "Did you know? When you scrape your knee, white blood cells rush there to fight the germs. That's why a cut gets a bit red and warm." |
| `say-fact-nose.mp3` | "Did you know? Snot traps germs before they can get inside you. A runny nose is your body cleaning itself!" |
| `say-fact-tummy.mp3` | "Did you know? Your tummy has acid that kills lots of germs in your food. Washing your hands before you eat helps too!" |
| `say-fact-lungs.mp3` | "Did you know? Tiny hairs in your airways sweep sticky mucus up and out, and the germs go with it." |
| `say-fact-eye.mp3` | "Did you know? Tears wash germs out of your eyes, and they even have germ fighters in them!" |
| `say-fact-ear.mp3` | "Did you know? Earwax is sticky, so it catches dust and germs before they get deep into your ear." |
| `say-fact-fever.mp3` | "Did you know? A fever is your body turning up the heat to make it hard for germs to grow. Rest and drink water to help!" |
| `say-fact-finger.mp3` | "Did you know? When you cut yourself, tiny bits in your blood called platelets stick together like a plug. That stops the bleeding and keeps germs out!" |
| `say-fact-throat.mp3` | "Did you know? Your tonsils, at the back of your throat, are like guards that catch germs you breathe in or swallow." |
| `say-fact-pox.mp3` | "Did you know? After your body beats chickenpox, it remembers that germ. So if it comes back, your body knows how to beat it straight away!" |

**Sound effects**: ElevenLabs Sound Effects, free plan, made 2026-10-09.

| File | Sound | Length |
| --- | --- | --- |
| `sfx-sneeze.mp3` | cartoon sneeze, "ah... ah... achoo!" | 1.8 s |
| `sfx-chomp.mp3` | a blob's squishy chomp | 0.6 s |
| `sfx-pop.mp3` | a germ popping like a slime bubble | 0.5 s |
| `sfx-ouch.mp3` | a soft cartoon bonk when a germ reaches the heart | 0.8 s |
| `sfx-king.mp3` | the King Germ's goofy grumble and rumble | 2.5 s |
| `sfx-win.mp3` | short victory fanfare with chimes | 2.5 s |
