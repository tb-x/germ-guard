# Germ Guard

A tower defence game set inside the body, for young kids (around age 5). Germs sneak into the body
and wiggle along blood vessels towards the heart. Your child builds white blood cells beside the
vessels to stop them before they get there.

It has five levels on a body-shaped map, four ways to defend, a sneeze, and seven kinds of germ, including
a King Germ boss. It has music and vibration, and it can be added to the Home Screen and played offline.

## The levels

1. **Scraped Knee** 🦵: germs come in through one scratch. Only zappers, to learn the game.
2. **Runny Nose** 👃: germs come out of both nostrils, down two vessels that merge before the heart.
   Adds the blob nest and the sneeze button.
3. **Tummy Ache** 🍔: germs come in through the mouth, and a second mouth halfway down sends fast ones on a shortcut.
   Adds the antibody maker, Wigglers and Chunkies.
4. **Lungs** 🫁: germs come three ways at once. Adds snot puddles, Corkscrews and Spikies.
5. **Big Fever** 🤒: germs pour in through the nose, the mouth and a scratch, all at once, every kind mixed together.
   The heart has a thermometer in its mouth and heat shimmers off the tissue. The last wave brings the **King Germ**.

## The map and saving

The title screen is a map: a child's body with a glowing spot for each level (knee, nose, tummy, lungs, and a
thermometer by the head for the fever). Tap a spot to play it. **Play** jumps to the newest unlocked level.

- Winning a level unlocks the next spot. Locked spots show a padlock, and the next one to play glows.
- The best stars for each level (1 to 3, from the hearts left at the end) show under its spot.
- Progress is saved in the browser (`localStorage`, keys `germguard.unlocked`, `germguard.stars` and `germguard.muted`).
- The house button in the corner during a level, and on the end card, goes back to the map.

## The defenders

- **Germ zapper** (a neutrophil, 5 drops): shoots little bubbles at germs in reach.
- **Blob nest** (a home for macrophages, 6 drops): comes with one blob, and you can train up to 3 (2 drops each).
  Blobs stand guard on the nearest stretch of vessel, preferring a spot where vessels merge. They grab a germ,
  hold it still and gobble it up. A tired blob lets go, waddles home for a short rest and comes back.
  Blobs never get hurt.
- **Antibody maker** (a B cell, 6 drops): throws Y-shaped antibodies that stick on germs. A germ with an antibody
  on it walks slower and pops faster, and a Spiky loses its armour. The maker picks germs that don't have an
  antibody yet, Spikies first.
- **Snot puddle** (4 drops, up to 3 per level, Lungs level): tap the vessel itself to drop one. Every germ that
  wades through it slows right down.
- **Sneeze** 🤧 (from Runny Nose on): during a wave the Go button turns into a sneeze button. It blows every germ
  back down the vessels. Then it needs 40 seconds to recharge, shown as a shadow sweeping round the button.
  The first time germs get close, a pointing hand and a voice remind your child it's there.
- **Upgrades**: tap a built zapper, nest or antibody maker to upgrade it, twice (6 drops, then 9). Each upgrade adds a gold
  ring and a star, and makes it bigger and stronger. A tapped nest also offers **Train** (+) while it has room for more blobs.

## The germs

| Germ | Looks like | What's special |
| --- | --- | --- |
| Bloop | green blob | the plain one |
| Big Bloop | bigger green blob | tough and slow |
| Wiggler | yellow striped sausage | fast and fragile |
| Corkscrew | teal spinning spring | too wiggly for blobs to grab |
| Chunky | lumpy olive cluster | tough; breaks into 3 Bloops when popped |
| Spiky | purple ball with spikes | shots bounce off until an antibody sticks; then its spikes shrink |
| King Germ | huge grumpy blob with a gold crown | the boss: very tough, slow, tires blobs fast, breaks into 4 Bloops, and costs 3 hearts if it gets through |

The first time a new kind shows up in a wave, the voice says what's special about it.

## How it plays

- Glowing pads sit beside the vessels. Tap one to see what you can build. The price shows as drop icons 💧,
  and anything you can't afford yet is greyed out.
- A bubble over each entry shows which germs come out of it next. Tap **Go!** when ready. Waves never start on their own.
- Popped germs drop energy drops. Tap them to collect, or they fly to the counter by themselves after a few seconds.
- Each cleared wave adds 3 bonus drops from the heart. Drops are scarce, so where and what you build matters.
- The heart has 5 hearts of health. A germ that reaches it costs one (and earns the heart a plaster).
- If all 5 are gone: "Achoo!" and **Try again** replays that wave. Every defender and drop is kept and the heart is refilled.
- Clear all 5 waves to win. You get 1 to 3 stars depending on how many hearts are left.
- A pointing hand and a spoken voice show where to tap first on each level.

## Sound, music and vibration

- Everything is synthesized in the browser: sound effects and music with Web Audio, and spoken lines with the
  browser's speech voice. There are no recorded files.
- **Music** has three moods: gentle while building, bouncy with drums during a wave, and a minor-key march while
  the King Germ is out. It dips while the voice talks and stops for the win and lose jingles.
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
- `gg.build(padIndex, 'zapper' | 'nest' | 'antibody')`, `gg.upgrade(padIndex)`, `gg.train(padIndex)` and
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
| `BUILDS.zapper` | cost, then reach / seconds between shots / damage for levels 1-3 | 5 drops; 2.7/0.85/1, 2.9/0.6/1, 3.1/0.8/2 |
| `BUILDS.nest` | cost, then guard reach / blob damage per second / blob stamina for levels 1-3 | 6 drops; 2.3/1.8/8, 2.5/2.4/11, 2.7/3.0/14 |
| `BUILDS.antibody` | cost, then reach / seconds between throws / germs per throw for levels 1-3 | 6 drops; 2.8/1.4/1, 3.0/1.0/1, 3.2/0.9/2 |
| `UPGRADE_COSTS` | drops to reach level 2, then level 3 | 6, 9 |
| `TAG_SLOW`, `TAG_DAMAGE` | speed and extra damage for a germ with an antibody on it | 0.7, 1.5 |
| `AB_SPEED` | antibody flying speed, tiles per second | 6 |
| `MUCUS_COST`, `MUCUS_MAX`, `MUCUS_R`, `MUCUS_SLOW` | snot price, puddles per level, reach in tiles, speed inside it | 4, 3, 0.6, 0.4 |
| `SNEEZE_COOLDOWN`, `SNEEZE_PUSH` | seconds to recharge the sneeze, tiles germs get blown back | 40, 5 |
| `TROOP_COST`, `TROOPS_PER_NEST` | drops per extra blob, most blobs per nest | 2, 3 |
| `TRAIN_S` | seconds to train a blob | 1.2 |
| `TROOP_SPEED` | blob walking speed, tiles per second | 1.8 |
| `TROOP_GUARD_R` | how close to its post a blob grabs germs, in tiles | 1.0 |
| `TROOP_REST_S`, `TROOP_RECOVER` | rest time when tired; stamina regained per second while waiting | 4 s, 1 |
| `CHOMP_S` | seconds between blob bites | 0.4 |
| `GERMS` | health, speed, drops, size, how fast each germ tires a blob, and its special trick | see the table above |
| `GERM_HELLO` | what the voice says the first time each germ appears | |
| `CAM_PITCH` | camera angle above the ground, in degrees | 38 |
| `MUSIC_VOL`, `MUSIC_DUCK` | music level, and how far it dips under the voice | 0.15, 0.35 |
| `MUSIC_MOODS` | tempo, chords, melody notes, drums and busyness for the build, wave and boss music | 92 / 124 / 110 bpm |

Each level in `LEVELS` has its own map, colours (`palette`), entry look (`entry`: one style, or a list with one per entry), starting drops
(`startEnergy`), allowed defenders (`builds`, plus `mucus` and `sneeze` switches), the first-tap hint, and `waves`.
A wave is a list of groups: germ kind, how many, seconds apart, an optional start delay, and which entry they
come from (`from`, 0 = the map's `1`).

### Balance as tested with simulated play

Level 1, Scraped Knee:

- Only 2 zappers, no upgrades: lost at wave 4.
- Any plan that keeps building or upgrading: won with all 5 hearts. It's the tutorial level, so it's easy on purpose.

Level 2, Runny Nose:

- Only 2 zappers: lost at wave 2.
- A mix of nests and zappers with no upgrades: won with 1 heart.
- Nests only: won with 2 hearts.
- One nest and one zapper, both upgraded: won with 3 hearts.
- Zappers only with upgrades, or a full build of nest, zappers and upgrades: won with all 5 hearts.

Level 3, Tummy Ache:

- Three zappers and nothing more: lost at wave 4.
- Four mixed defenders and nothing more: lost at wave 4, even when sneezing.
- Building on every pad with upgrades, whether zappers only or a mix: won with all 5 hearts.

Level 4, Lungs:

- Zappers only, even upgraded: lost at wave 3. Nothing can hurt Spikies without antibodies, and the voice says so at the first bounce.
- One antibody maker and four zappers, no snot or upgrades: lost at wave 5.
- A full mix with antibodies, snot, a nest and upgrades: won with all 5 hearts.

Level 5, Big Fever:

- Four defenders and nothing more: lost at wave 2.
- An antibody maker and six zappers, never sneezing: lost at wave 4.
- The same build with the sneeze: won with 3 hearts. The King Germ got about 80% of the way to the heart.
- A full mix of everything with upgrades: won with 4 hearts.

## Made with

Plain HTML and JavaScript. [three.js](https://threejs.org/) 0.170.0 from jsDelivr draws the isometric
board, and every model is built from simple shapes in code. Sounds are synthesized with Web Audio, and
spoken lines use the browser's speech synthesis.
