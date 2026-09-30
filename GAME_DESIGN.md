# Captain Whiskers: Moon Base Mission — Game Design Document

This file is the source of truth for the game. Read it before making any change.
Current version: **v6** (file: `space-cats-v6.html`, ~1,240 lines, one self-contained HTML file).

## 1. What the game is

- **Players:** Alice (age 8) and her dad Nick. Text must be simple, friendly, and short.
- **Goal:** help space cats leave a crowded Moon Base and pick the best planet for a colony.
- **Learning goal:** real space science (gravity, star types, distance and temperature, time dilation, gas giants, and so on) through decisions, not quizzes.
- **Fun goal:** flying, dodging, discovering, and funny landing animations.
- **Tone:** no harsh losing. A rescue ship always brings everyone home.
- **Devices:** phone (touch drag) and laptop (mouse follow, arrow keys, or WASD).

## 2. Game loop (v6)

1. **Title screen:** watch the story, read how to play, skip to the mission, open the Discovery log, or start a new galaxy.
2. **Story:** 6 animated scenes (Earth, trip to the Moon, Moon life, crowded domes, telescope spots 5 planets, limited fuel).
3. **How to play:** 6 illustrated pages (clues, supplies, flying, things along the way, landing and colonies, tips).
4. **Star map:** 5 shuffled planets, each with telescope clues, a colony checklist, trip cost, and a probe button. Toolbar: Hint, How to play, Discoveries.
5. **Flight (26 s):** dodge obstacles, grab items, pass through zones.
6. **Landing:** 4-second animation, then the full checklist and a "Real science" fact.
7. **Decide:** build the colony here, or go back to the star map.
8. **End:** stars, then the colony is saved and that planet is removed from future missions.

## 3. Rules and numbers

| Thing | Value |
|---|---|
| Start fuel / days | 7 fuel, 26 days |
| Planets per mission | 5: 1 perfect (6/6), 2 good (5/6), 2 poor (4/6 or less) |
| Trip distance | random 1 to 3 per planet (perfect planets are never distance 1) |
| Trip cost | fuel = distance; days = 4 / 6 / 8 for distance 1 / 2 / 3 |
| Leaving heavy gravity (over 1.5× Earth) | +1 fuel |
| Black hole planet | +8 days per trip |
| Robot probe | 1 fuel; reveals ground, water, air, temperature |
| Known from telescope | gravity only |
| Known only on landing | "Safe and calm" |
| Scoring | 6/6 = 3 stars, 5/6 = 2 stars, 4/6 = 1 star, 3 or less = rescue ship |
| Colony saved | score 4 or more; that planet is taken for future missions |
| Galaxy explored | when no 6/6 planets remain or fewer than 5 planets remain; "Start a new galaxy" resets |

**Colony checklist (6 checks):** solid ground, water, air, gravity OK (0.5 to 1.5× Earth), temperature OK, safe and calm.

**Temperature rule (the key thinking skill):** each star has a comfy distance.
Red dwarf = very close (1). Yellow, orange, two suns = medium (3). Blue = very far (5). Black hole = never comfy.
Closer than comfy = too hot; farther = too cold. Planet data must always match this rule.

**Telescope clues shown:** gravity, star, distance from star, day length, size, and "Telescope sees" (a short note, sometimes a trick).

## 4. Flight

- **Zones by progress:** 0–30% open space, 30–55% asteroid belt (dense small rocks), 55–80% comet zone (fast diagonal comets), 80–100% mixed.
- **Hazards:** rocks, grumpy aliens (zigzag), comets. A hit removes 1 shield; with an empty shield, a hit costs 1 day.
- **Shield:** 3 pips, recharges 1 every 4 s. Fish refill it fully.
- **Specials per flight:** 3 discoveries, 2 fuel cans (+1 fuel), 1 mini black hole (pulls the cat within 170 px; touching it costs 1 day), 2–3 of wormhole / tricky can.
- **Wormhole:** 70% chance +15% progress, 30% chance −8%.
- **Tricky fuel can:** looks like a fuel can but has blinking eyes; it damages like an alien.

## 5. Planets (18)

**Perfect (6/6):** Twin Suns, Platypia, Emberglow (tricky: very close to a red dwarf), Dodo Isle, Unicornia (tricky: very far from a blue star), Trilobia.
**Good (5/6):** Chonk (heavy), Groovia the Disco Planet (storms), Fungalia the Mushroom Planet (chilly), Mammothia (ice age), Buzzonia (giant dragonflies), Floatopia (no ground).
**Poor:** Jurassica (4/6, looks like Earth, T. rex), Blaze, Puffy, Tick-Tock, Glassworld (looks blue like Earth), Diamondia.

Each planet has: name, colors, look, gravity, star, star distance, day, size, telescope note, checks with short text, landing animation type, caption, what was found, and a real-science fact. Made-up things are always labeled as made up.

## 6. Discoveries (12)

Old satellite, comet, Ed White's lost glove, tardigrade, Voyager golden record, space whale (made up), ancient meteorite, space ice, faraway galaxy, dino-shaped rock (made up), James Webb telescope, Moon footprints.

## 7. Saving

- Inside Claude: colonies and discoveries are saved with `window.storage` (key `moonbase-mission-save`).
- Downloaded or hosted file: `window.storage` does not exist, so progress resets on reload. **Planned fix in v9** (see roadmap).
- Never use `localStorage` inside Claude's preview; it fails there. It is fine on GitHub Pages.

## 8. Code map (v6)

One HTML file: CSS, then HTML overlays (`#hud`, `#toast`, `#overlay`, `#caption`), then one script.
Script sections in order: star and planet data (`STARS`, `POOL`, `DISCOVERIES`), setup and controls, save, game setup (`prepareGame`, `tripCost`, `known`), screens (title, story, rules, discovery log, hints, star map, landing, build colony, rescue), flight (`startFlight`, `spawnObstacle`, `spawnSpecial`, `update`), drawing (flight objects, creatures, `drawPlanet`, `drawCat`, `drawScene`, `drawStory`, `draw`), main loop.

## 9. Rules for making changes (for Claude)

- Read this file first. Make **targeted changes**; do not rewrite working code.
- Keep one self-contained HTML file with no outside libraries, unless we decide to split files.
- Keep all text readable for an 8-year-old. Keep science accurate and label made-up content.
- Test before sharing: syntax check plus a simulated run of all scenes and a full campaign.
- After each change, update **Changelog**, **Roadmap**, and any rules or numbers above.

## 10. Roadmap

### v7: Choose your character (next)
The player picks a character before each mission. Each has a strength and a weakness.

| Character | Strength | Weakness |
|---|---|---|
| **Captain Whiskers** (pilot cat) | 4 shield pips, shield recharges faster (3 s), fuel cans give +2 | No special science tools |
| **Professor Meowf** (half cat, half dog scientist) | 1 free probe per mission, hints also reveal the "Safe and calm" clue for one planet, discoveries also give +1 day | Steers a bit slower, 2 shield pips |

- Character select screen with a drawing of each and 2–3 short lines.
- Landing captions can differ by character (for example, Meowf's dog half digs on sandy planets).
- Later idea: **Engineer Mittens**, who gets building discounts in colony mode (v8).

### v8: Build the colony (strategy mode)
After "Build the colony here," a short building phase begins.

- **Length:** 5 turns (each turn = 1 month).
- **Start:** 10 cats; supplies = 3 per leftover fuel + 1 per leftover day.
- **Board:** a 4×4 grid on the planet surface; tap an empty square to build.
- **Buildings (cost in supplies):**
  - Dome (4): houses 10 cats. Needed if air is ✗.
  - Farm (3): feeds 10 cats.
  - Water pump or ice melter (3): needed if water is ✗ or only ice.
  - Heater (3): needed if temperature is ✗. Cooling tower (3) if too hot.
  - Storm wall (4): needed if "safe and calm" is ✗ because of weather.
  - Gravity gym (4): needed if gravity is ✗ (keeps cat muscles strong).
  - Solar panel (2): +2 supplies per turn. Weaker near red dwarfs (science!).
  - Wind turbine (2): +2 supplies per turn. Stronger on stormy planets like Groovia.
- **Each turn:** build, then one random planet event (dust storm, meteor shower, friendly mammoth visit, rainbow, etc.). If needs are met, the population grows.
- **Goal:** reach 30 cats by turn 5. Colony stars are added to exploration stars.
- **Key idea:** the planet's ✗ marks decide what you must build first, so exploring and building connect. A 2-star planet can still become a great colony with smart building.

### v9: Saving that works everywhere
- Use `localStorage` when hosted (GitHub Pages) and `window.storage` inside Claude.
- Add a "Save code" button: copy a short code, paste it later to restore colonies and discoveries.

### Backlog (ideas, not scheduled)
- Harder mode: 7 planets, fewer supplies.
- Sounds (Tone.js or simple beeps) with a mute button.
- Alice designs her own planet (name, gravity, star, distance), and the game checks whether the temperature makes sense.
- More discoveries and planets. Achievements (for example, "Visited a black hole").

## 11. Changelog

- **v1:** Firefly in the Rain (test game).
- **v2:** Captain Whiskers space game: real planets, fact cards, quizzes, clues.
- **v3:** Part 2 made-up planets. (Separate underwater spin-off: Captain Meowf, half cat and half dog.)
- **v4:** Moon Base Mission: strategy rules, fuel and days, probes, colony checklist, shuffled planets, no quizzes.
- **v5:** Animated story, illustrated how-to-play pages, Captain's hints.
- **v6:** 5 planets per mission, temperature puzzle (star + distance), 18 planets, flight zones, comets, wormholes, mini black holes, tricky fuel cans, 12 discoveries, permanent colonies, "galaxy explored" ending.
