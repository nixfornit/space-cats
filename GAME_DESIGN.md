# Captain Whiskers: Moon Base Mission — Game Design Document

This file is the source of truth for the game. Read it before making any change.
Current version: **v13** (file: `space-cats-v13.html`, ~4,260 lines, one self-contained HTML file).

> **Note on versions (Oct 2026):** two different files were called v8. This file continues the **galaxies and cartoons** v8. The other v8 (Zib, diamonds, status, built on v7) was never in the project; v9 re-makes all of its features here, so that file is no longer needed. `GAME_DESIGN_1.md`, `GAME_DESIGN_2.md`, and `GAME_DESIGN_3.md` in the project are old copies and can be deleted.

> **Note on v13 (Oct 12, 2026):** v13 is built on v12 (`claude/space-cats-v12.html`).

> **Note on v12 (Oct 12, 2026):** v12 is built on `space-cats-v11.html` (the copy uploaded Oct 10). `claude/space-cats-v11.html` and `claude/space-cats-v10.html` are older working copies.

## 1. What the game is

- **Players:** Alice (age 8) and her dad Nick. Text must be simple, friendly, and short.
- **Goal (one sentence, since v10):** Alice flies to new planets, explores them, and can say in her own words why a planet is or is not a good home.
- **What Alice likes:** discovering new planets and flying. **What she does not like:** reading and planning. Cartoons, voices, and action work well. Every change should respect this.
- **Learning goal, narrowed to 4 ideas (v10):** (1) living things need ground, water, air, and the right temperature; (2) temperature depends on the star and how far the planet is from it; (3) planets are very different (gas giants have no ground, gravity changes how you move); (4) space is huge and scientists are still finding new things. The older, wider list (time dilation, light-years, wormholes, and so on) lives on in the knowledge stars.
- **Results to look for (our own yardsticks, not research numbers):** she plays 10–15 minutes without someone reading for her; she asks to play again; she tells one fact without being asked; after a few sessions her hot / cold / just right guesses are right more often than wrong.
- **Two ways to play (v10):** **Explorer mode** (easy, the default) and **Captain mode** (the full v9 game). The Game Workshop switches between them.
- **Fun goal:** flying, boosting, dodging, discovering, short cartoons, and funny landing animations.
- **Since v13:** Alice picks her explorer (a cat, a platypus, or an axolotl, each with a super power) and dresses it up. Missions come in **journeys** of 3 (Water Hunters, Signs of Life, New Home Builders), each with its own cartoon. Planets have branching roads with dead ends, flights have comet storms and cannon-firing pirates, a broken ship can be saved with one fun question, and some wormholes lead to another galaxy.
- **Since v12, every play session has a goal:** a numbered mission with one clear goal (for example "Find a planet with water"), always shown in the top ribbon, with a start card and a "Mission complete!" card. Trips have challenges (space police, pirates, a ship that can break), the rover drive is a small quest, and colonies take several trips to build.
- **Tone:** no harsh losing. A rescue ship always brings everyone home. Since v12 a few small things can be lost (a trip when the ship breaks, a little stardust to pirates or the police), but never diamonds, planets, colonies, or status.
- **Devices:** phone (touch drag) and laptop (mouse follow, arrow keys, or WASD).

## 2. Game loop

### 2a. Explorer mode (the default; flow changed in v13)

1. **Start screen:** the hero's name, a progress bar for the current place, one big **Play!** button, **👤 My explorer** (v13, with the explorer's picture), and two small ones: 🗺️ My journey and ⚙️ More. Everything else (Discovery log, story, voice, Workshop, start over) is under More.
2. **Story:** plays by itself only the first time (`SAVE.story`). Two shorter last pages (`STORY_EASY`). No how-to-play pages.
3. **Choose your explorer (v13, first time only; later from the start screen):** 3 big cards (space cat, space platypus, space axolotl), a small cartoon of the explorer flying and showing its super power, Zib says the power, and rows of choices: hat, glasses, face, space suit, and fur (cats only). See section 9e.
4. **Step 1, Place ("Where do we explore?"):** the journey map (section 9c). The place she is in has the orange **▶ Explore** button. Other places have a small Go button.
5. **Journey cartoon (v13):** when a new journey starts: a 13-second cartoon in 3 scenes that explains the goal, with Zib reading each line (tap to skip). Then the **journey card**: the journey's name and icon, its goal, its 3 missions (the current one outlined), **🚀 Start the journey!**, and "Watch the cartoon again". See section 3b.
6. **Mission start card (v12):** for missions 2 and 3 of a journey: "💧 WATER HUNTERS · MISSION 2 OF 3", the goal in big letters, a small cartoon, one tip from Zib, and **🚀 Let's go!**. Starting a mission fills the rockets back up to 3.
7. **Step 2, Planet ("Where do we fly?"):** 3 big planet pictures and one rocket for each trip left. Planets she has not visited come first. A colony that called for help shows up as a red **🔧 Fix** tile; flying there costs one rocket.
8. **Step 3, Guess:** a small cartoon (the star shines, the planet waits on its spot), Zib says one short hint, and 3 big buttons: 🔥 too hot, 😊 just right, ❄️ too cold. A right guess pays 1 💎 (once per planet).
9. **Take-off cartoon → flight → landing cartoon:** boost, stardust, one knowledge star that cannot be skipped, the space police, colony radio news, and since v13 a **comet storm** and **two pirate ships that fire cannonballs** (section 4). After 3 cracks the ship breaks: Zib asks **one fun question**; right, the ship is fixed and the flight goes on; wrong, the tow truck takes the ship back to base and the trip is used up. **3 in 10 mini wormholes** pull the ship into another galaxy (section 4).
10. **Rover quest:** the rover needs help, and one space question fixes it. Since v13 the roads **branch**: 3 forks, each with one dead end, and a small road map in the corner (section 9d). The 5 glowing circles and the treasure chest are on the right roads.
11. **Decide card:** the planet's own small cartoon, 6 big boxes (ground, water, air, gravity, temperature, safety), one short fact from Zib, and one question: "Good home for the cats?" 👍 / 👎.
   - 👍 on a planet with 4 to 6 green lights plays the **colony-building cartoon** (section 10), then a short card: the colony is **started** and needs 3 more trips to finish. 👍 on a worse planet shows "Hmm, not here!"; nothing is lost.
   - 👎 on a planet with 3 or fewer green lights pays 1 💎 ("Good thinking!", once per planet). 👎 on a perfect planet asks once "Wait!".
   - Earth is special: it is perfect, but it is already home, so no colony is built there.
12. **After 3 trips:** "Out of rockets!" Zib says the mission is saved, and "Refuel and fly again!" brings 3 new planets and 3 new rockets.
13. **Mission complete card:** "Mission complete!", a trophy cartoon, +5 💎 (paid once), and **🎯 Next mission!** After mission 3 the button is **🏆 Finish the journey!**, which opens the **journey complete card** (v13): a trophy with the 3 stars, +15 💎 (paid once), and **🌟 Next journey!**, which plays the next journey's cartoon.

### 2b. Captain mode (the v9 game)

1. **Title screen:** shows the current galaxy and "Planets visited: X of Y". Watch the story, read how to play, skip to the mission, open the Discovery log, open the Game Workshop, or start over from the Milky Way. Since v9 it also shows your status and diamonds, and has a **Choose a galaxy to explore** button. A **top ribbon** is on every screen (section 9).
2. **Story:** 6 animated scenes (Earth, trip to the Moon, Moon life, crowded domes, telescope spots 5 planets, limited fuel).
3. **How to play:** 6 illustrated pages (clues, supplies, flying, things along the way, landing and colonies, tips).
4. **Star map (new layout in v9):** 5 planet tiles at the top (picture, name, trip cost, and a badge: 📍 here, ✅ visited, 🤖 probed). Tap a tile to see **one** planet below: telescope clues, colony checklist, trip cost, Fly and Probe buttons. Two pills show where you are and the galaxy's visited count (fuel and days are in the ribbon). Toolbar at the bottom: Hint, How to play, Discoveries. Phones show the tiles as 3 + 2; laptops show 5 in a row.
5. **Take-off cartoon (5 s, new in v8):** space suit on, hop into the rocket, engines on, blast off. Tap to skip.
6. **Flight (26 s by default):** dodge obstacles, grab items, pass through zones. Touching a mini black hole plays the **time cartoon** (5 s). Touching a knowledge star stops the game while Zib reads the fact (new in v9).
7. **Landing cartoon (4.5 s, new in v8):** the rocket comes down, dust, the hero hops out. On planets with no ground, the ship hovers. Tap to skip.
8. **Explore (new in v8):** the funny landing scene keeps playing (no time limit). Tap **5 glowing circles** to explore air, temperature, look around, ground, and water. Then tap "See the colony report".
9. **Colony report:** the full checklist and a "Real science" fact.
10. **Decide:** build the colony here, or go back to the star map.
11. **End:** stars, then the colony is saved and that planet is removed from future missions.
12. **Giant wormhole (new in v8):** when every planet in the galaxy was visited (or no mission can be made), a wormhole opens. 4 picture pages explain how a wormhole works, then a 9-second tunnel flight leads to the next galaxy.

## 3. Rules and numbers

| Thing (Explorer mode, v12) | Value |
|---|---|
| Planets on the map | 3 from the current place, not-yet-visited first; if possible 1 perfect, 1 good, 1 poor |
| Trips | 3 rockets. "Out of rockets" refuels with 3 new planets. Starting a new mission also fills the rockets to 3. A repair trip costs 1 rocket. No fuel, days, or probes |
| Ship (v12) | 3 hearts each flight (🚀❤️❤️❤️ next to the trip bar). A bump with an empty shield cracks 1 heart. 0 hearts: the ship breaks, the tow-truck cartoon plays, the ship goes back to the base, and that trip is used up |
| Diamonds (v12) | knowledge star +5 the first time, +2 after · right hot/cold guess +1 (once per planet) · smart 👎 +1 (once per planet) · 10 stardust +1 · flying diamond +1 · rover fixed with a right answer +1 · all 5 finds +1 (once per planet) · treasure chest +2 (once per planet) · colony started +1 / +2 / +3 · colony finished +3 · colony repaired +3 (+1 if Zib helped) · police question right +1 · mission complete +5 |
| Lost in flight (v12) | stardust only: pirates take up to 5, a police ticket takes up to 3. A broken ship loses the trip. Mini wormholes still always go forward, and there are still no tricky cans |
| Black hole cartoon | plays once each time the game is opened; after that the black hole only spins the ship |
| Mission can start | when at least 1 planet without a colony is left |

| Thing (Captain mode, and shared rules) | Value |
|---|---|
| Start fuel / days | 7 fuel, 26 days (defaults; the Game Workshop allows fuel 5–10 and days 18–36) |
| Planets per mission | 5 from the current galaxy: 1 perfect (6/6), 2 good (5/6), 2 poor (4/6 or less). Since v10, planets not yet visited are picked first. In the Solar System there is no "1 perfect" rule |
| Trip distance | random 1 to 3 per planet (perfect planets are never distance 1) |
| Trip cost | fuel = distance; days = 4 / 6 / 8 for distance 1 / 2 / 3 |
| Leaving heavy gravity (over 1.5× Earth) | +1 fuel |
| Black hole planet | +8 days per trip |
| Robot probe | 1 fuel; reveals ground, water, air, temperature |
| Known from telescope | gravity only |
| Known only on landing | "Safe and calm" |
| Scoring | 6/6 = 3 stars, 5/6 = 2 stars, 4/6 = 1 star, 3 or less = rescue ship |
| Colony saved | score 4 or more; that planet is taken for future missions |
| Planet "visited" | landing on it (saved in `SAVE.seen`, kept between missions) |
| Wormhole opens | every planet in the galaxy visited, **or** no mission can be made (no 6/6 planet left, or fewer than 5 planets left) |
| Wormhole accident | 1 in 3 chance each trip to land in the surprise galaxy (if not explored yet). If only the surprise galaxy is left, the wormhole always goes there. |
| Diamonds 💎 (v9, changed in v12) | the same list as Explorer mode above. Diamonds are never spent or lost. |
| Ship and repairs (v12) | the same 3 hearts as Explorer mode; a crack also costs 1 day. A repair trip costs ⛽ 1 fuel and 📅 2 days |
| Status (v12) | needs diamonds **and** planets explored **and** finished colonies; see section 3b |
| Choosing a galaxy (v9) | From the title screen. Milky Way, Andromeda, and Triangulum can be chosen; the Cartwheel Galaxy cannot (wormhole accident only). A galaxy you leave by choice is **not** marked finished, so a wormhole can bring you back later. A chosen trip never has an accident. |
| Solar System (v10) | The starting place. 9 real worlds. No colony can be built (Earth is already home; the others score 0 to 2). When all 9 were visited, a card sends the rocket to "other stars" in the Milky Way, with no wormhole. Milky Way ↔ Solar System trips in "Choose where to explore" also need no wormhole |
| All galaxies explored | final card; "Start over from the Solar System" clears colonies, visits, and galaxies (not discoveries, Workshop answers, diamonds, or status) |

### 3b. Journeys and missions (v13), colonies that take time, and status (v12)

**Journeys and missions (v13)** (`JOURNEYS`, `newMission`, `missionEvent`, `journeyIntro`, `journeyCard`, `journeyDoneCard`). A journey has one big goal, its own 13-second cartoon, and 3 missions that must be done in order. The ribbon always shows the journey icon, 3 dots (gold = done, half = now), the current mission's goal, a bar, and x / y.

| Journey | Goal | Mission 1 | Mission 2 | Mission 3 | Cartoon (3 scenes) |
|---|---|---|---|---|---|
| 💧 Water Hunters | find planets with water, so the kittens can drink and grow food | Find a planet with water | Find 2 planets with water | Start a colony on a planet with water | Earth and a water drop · a hot, a frozen, and a blue planet checked with a magnifying glass · kittens by a stream next to a dome |
| 🌱 Signs of Life | find planets where something is alive, from tiny slime to big animals | Find a planet with life | Answer 3 space questions right | Find 2 planets with life | a microscope and wiggly germs · a parade of animals · a telescope and planets with "?" |
| 🏠 New Home Builders | start a colony, finish it, and fix it | Start a new colony | Finish building a colony | Fix a broken colony | the crowded Moon Base dome · domes popping up · a wrench and happy kittens |

After the third journey they start again with bigger numbers (level 2 doubles the counts, level 3 triples them; "finish" and "fix" stay at 1).
- **Counts when:** water: the rover finds water ✓. Life: the rover reaches the 👀 "look around" circle on a planet with life; a find card says "🌱 Life found!". Colony on a water planet: 👍 builds a colony on a planet with water. Quiz: any question answered right. Colony, finish, fix: as in v12.
- **Planets with life** (`hasLife`): every planet with animals (platypuses, dodos, unicorns, trilobites, axolotls, capybaras, quokkas, koalas, octopuses, mammoths, penguins), plants or mushrooms (Twin Suns, Fungalia, Emberglow's black forests, Buzzonia), dinosaurs (Jurassica), sky jellies (Floatopia), fish (Splashia), glowing plankton (Glowmere), green slime (Gloop), and Earth. In the Solar System only Earth has life, which matches real science.
- A mission can need another place: colonies cannot be built in the Solar System, so a colony mission there says "Fly to another place on the journey map!". If "Fix a colony" comes up with no colony at all, it becomes "Start a new colony".
- Saves from v12 start the first journey from mission 1; everything else (planets, colonies, diamonds, status) stays.

**Colonies take time** (`SAVE.build`, `colonyTick`, `showRadio`, `repairTrip`).
- A new colony starts at stage 1 ("The first dome is up!"). At the start of every flight each colony grows one stage: 2 "The farm is planted!", 3 "The power is on!", 4 "All finished!" (+3 💎). So a colony is finished 3 trips after it was started.
- During the flight, a **radio panel** (📡) brings this news one item at a time, with Zib's voice.
- At the start of a flight, if no colony is broken, there is a 1 in 4 chance that one colony (only one whose first dome is up) breaks something: the water machine, air machine, solar panel, dome, or farm robot. The radio says **🆘 SOS**. A broken colony stops growing until it is fixed.
- **Fixing:** the map shows a red 🔧 tile. The repair trip plays a short cartoon (flying back to the colony, the broken machine sparking), then Zib asks one space question. Right: "Fixed!", +3 💎. Wrong twice: "We fixed it together!", +1 💎. The colony is fixed either way.
- The ribbon chip shows 🏠 finished colonies, 🏗️ colonies being built, and 🔧 when one needs help. The journey map shows 🏠, 🏗️, or 🔧 on each colony planet.
- Saves from before v12: all their colonies count as finished.

**Status** (`RANKS` = [diamonds, name, planets explored, finished colonies]). A status needs all three:

| Status | 💎 | 🪐 planets explored | 🏠 finished colonies |
|---|---|---|---|
| Space Cadet | 0 | 0 | 0 |
| Junior Scientist | 30 | 5 | 1 |
| Scientist | 80 | 10 | 3 |
| Senior Scientist | 150 | 16 | 5 |
| Lead Scientist | 240 | 22 | 7 |
| Chief Scientist | 350 | 30 | 9 |
| Professor of Space | 500 | 40 | 12 |

"Planets explored" counts every planet she has landed on (the Solar System too). A status already earned in an older save is kept. The ribbon shows what the next status still needs, for example "💎12/30 🪐4/5 🏠0/1" (a ✓ when one part is done), and a bar that fills up.

### 3c. Quiz questions (new in v12)

`quizCard(o)` asks one multiple-choice question from the facts (section 6): a small cartoon, Zib reads the question, then 3 big answer buttons (A, B, C) that Zib also reads.
- Questions come from facts she has already found first (so the quiz repeats what she learned), and not from the last 12 questions asked (`SAVE.qa`).
- Right: the button turns green, Zib says "Yes!" and a short fact. Wrong: the right answer turns green, Zib reads the whole fact, and she gets **one more question**; if that one is wrong too, "Zib helps!" and the game goes on. The space police ask only once.
- Used by: the rover quest (every landing), colony repairs, and the space police.

### 3d. Colony checklist and the temperature rule

**Colony checklist (6 checks):** solid ground, water, air, gravity OK (0.5 to 1.5× Earth), temperature OK, safe and calm.

**Temperature rule (the key thinking skill):** each star has a comfy distance.
Red dwarf = very close (1). Yellow, orange, two suns = medium (3). Blue = very far (5). Black hole, pulsar, no star = never comfy.
Closer than comfy = too hot; farther = too cold. Planet data must always match this rule (the test checks it).

**Telescope clues shown:** gravity, star, distance from star, day length, size, and "Telescope sees" (a short note, sometimes a trick).

**Explore points (v8):** 5 circles, each shows one checklist answer and one short "why" line. Exploring is optional. Since v9, exploring all 5 circles gives +1 💎, once per planet. Gravity is not a circle because the telescope already measures it.

## 4. Flight

- **Zones by progress:** 0–30% open space, 30–55% asteroid belt (dense small rocks), 55–80% comet zone (fast diagonal comets), 80–100% mixed.
- **Hazards:** rocks, grumpy aliens (zigzag), comets, and since v13 pirate cannonballs. A hit removes 1 shield. With an empty shield, a hit cracks the ship: one of 3 hearts. With 1 heart left, a warning: "One more bump and the ship breaks!" **(v13)** 0 hearts: `shipBroke()` plays a 2.4-second cartoon (the ship sputters and sparks), then Zib asks **one fun question** (`quizCard`, one try). Right: "Fixed! Keep flying!", 2 hearts, a full shield, 2.5 s of safe time, and the flight goes on. Wrong: the tow-truck cartoon (`tow`, 4.2 s), then "Back at the base", and the trip is used up. In Captain mode a crack also costs 1 day.
- **Comet storm (v13):** at 44% of the trip, "☄️ COMET STORM!" with a siren and a voice line. For about 6 seconds a fast comet comes every quarter second, and the sky glows orange.
- **Pirate cannonballs (v13):** the two pirate ships (60% and 78%) fire a slow cannonball at the cat about every 1.4 seconds while they cross. A cannonball hits like a rock. Ramming the pirate ship now also costs a shield (and the pirates still take up to 5 stardust).
- **Galaxy wormholes (v13):** touching a mini wormhole has a **3 in 10** chance to pull the ship into another galaxy (`galaxyJump`): the 9-second wormhole cartoon (wiggly), then a card "🌀 Surprise! The Andromeda Galaxy!" with the galaxy's picture, a real fact under "📖 Real science", and 3 choices: **Stay and explore here** (new planets and 3 rockets there), **Back to** the place she came from, or **Somewhere else** (the journey map). The galaxy is picked at random from the ones not finished yet; it can be the surprise Cartwheel Galaxy. From the Solar System it never picks the Milky Way (we are already in it). The trip is used up; the journey and mission stay. The other 7 in 10 wormholes work as before.
- **Super powers (v13, section 9e):** cat: the shield refills every 2 s instead of 4. Platypus: stardust, diamonds, and fish within 190 px slide toward the ship. Axolotl: a crack heals every 10 s.
- **Boost (v10):** hold the BOOST button (bottom right), the space bar, or the mouse button. Everything rushes past 1.8× faster, the flight ends sooner, the stars turn into streaks, and the flame grows.
- **Stardust (v10):** every few seconds a wavy trail of 7 small stars appears. Each one plays a note that climbs higher along the trail. 10 stardust = 1 💎. The count (✨) is next to the trip bar.
- **Sounds (v10, more in v12):** made in code with the Web Audio API (`SFX`, `sfx()`); no sound files. Take-off, landing, grab, diamond, bump, boost, wormhole, good / problem, a little fanfare, and since v12 a police siren, radio beeps, a splash, a pirate "arr", and a broken-ship clunk.
- **Shield:** 3 pips by default (Workshop: 2, 3, or 4), recharges 1 every 4 s. Fish refill it fully (fish do not fix cracks).
- **Specials per flight (v13):** 1 knowledge star (36% of the trip), 2 diamonds, 2 fuel cans (Captain mode only), 1 mini black hole (54%), 1 space police saucer (18%), **1 comet storm (44%)**, **2 pirate ships (60% and 78%)**, 2–3 of mini wormhole / tricky can (Explorer: wormholes only).
- **Mini black hole (v8):** touching it pauses the flight and plays a 5-second cartoon: a slow clock near the black hole, a fast clock back home, and "A black hole's gravity is so strong that it stretches time!" Then 1.5 s of no damage.
- **Mini wormhole (in flight):** since v13, 30% chance it leads to another galaxy (see above). Otherwise: Explorer mode always +15% progress; Captain mode 70% chance +15%, 30% chance −8%. (This is different from the giant wormhole between galaxies.)
- **Tricky fuel can:** looks like a fuel can but has blinking eyes; it damages like an alien.
- **Knowledge star (v9, changed in v12):** only **one per trip**, and it **drifts toward the cat**, so it is never missed. Touching it sets `state = 'fact'`: the flight freezes, Zib reads a joke and the fact next to a cartoon. The button says "🔊 Listen... 9" and stays locked until Zib has had time to read (6 to 16 seconds, by the number of words), then "Got it! +5 💎" (+2 for a fact already found). Each new star picks a different group of facts than the last one. Then a happy dance, a new status if one was reached, and the flight goes on with 1.5 s of safe time.
- **Space police (v12, made up):** a flying saucer with a flashing light and a little officer in a police hat. A toast and the voice say "Space police! No boosting!". For 7 seconds it follows the cat along the top of the screen with a siren. **Boosting while it is there, or touching it,** gets you pulled over: a 4.5-second cartoon ("Wee-woo! You were zooming much too fast!"), then one space question. Right: "Have a safe flight!" +1 💎. Wrong: a little ticket, −3 stardust. Then the flight goes on.
- **Space pirates (v12, made up):** a wooden pirate ship with a black sail and jets crosses the screen in a wave. Touching it: "Arr!", the pirates take up to 5 stardust. No shield damage.
- **Colony radio (v12):** see section 3b. News comes at 15% of the trip and then every 18%.

## 5. Places and planets (45 planets: our Solar System and 4 galaxies)

**Our Solar System (v10, the starting place): 9 real worlds, marked `real: true`.** All numbers are real: gravity at the surface or cloud tops, day length, and the facts below. They follow the same temperature rule (the Sun is a yellow star; Earth is at the comfy middle spot).

| World | Gravity (× Earth) | Spot | Landing scene | Key fact |
|---|---|---|---|---|
| Mercury | 0.38 | very close | hot | 88-day year; about 800°F by day, about -290°F at night |
| Venus | 0.9 | close | hot (thick clouds) | hottest planet, about 870°F; a day longer than its year; spins backwards |
| Earth (`home: true`) | 1.0 | middle | earth (new) | the only planet known to have life; about 70% ocean; Goldilocks zone |
| Mars | 0.38 | far | dust (rusty red) | rust-red dust; Olympus Mons, more than 2× Mount Everest; rovers |
| Jupiter | 2.5 | very far | sink + Great Red Spot | more than 1,300 Earths fit inside; the storm is over 150 years old |
| Saturn | 1.1 | very far | sink + rings in the sky | would float in water; more than 250 moons; rings of ice and rock |
| Uranus | 0.9 | very far | sink | spins on its side; coldest clouds; a gas that smells like rotten eggs |
| Neptune | 1.1 | very far | sink + wind | fastest winds, over 1,200 mph; 165-year trip around the Sun |
| Pluto (dwarf planet) | 0.06 | very far | cold, slow high jumps | smaller than our Moon; heart-shaped ice plain; New Horizons, 2015 |

The Solar System is stored in `GALAXIES` with `sys: true` (it is **last** in the list so `GALAXIES[0]` is still the Milky Way). It is not a galaxy: the text says it is inside the Milky Way, and wormhole logic skips it.

The galaxies are real. Their planets are made up (cards say "a pretend planet"). Order: Solar System → Milky Way → Andromeda → Triangulum. The Cartwheel Galaxy is the surprise galaxy, reached only by a wormhole accident.

| Galaxy | Perfect (6/6) | Good (5/6) | Poor |
|---|---|---|---|
| **Milky Way** (12) | Twin Suns, Platypia, Dodo Isle, **Koalia** (v10, koalas) | Chonk (heavy), Mammothia (ice age), Floatopia (no ground), **Pengwinia** (v10, penguins, cold), **Eyeball** (v10, one side always faces its red star; winds) | Jurassica (4/6, T. rex), Tick-Tock (black hole), Glassworld (looks like Earth) |
| **Andromeda** (10) | Emberglow (tricky: very close to a red dwarf), Unicornia (tricky: very far from a blue star), Trilobia | Groovia the Disco Planet (storms), Fungalia the Mushroom Planet (chilly), Buzzonia (giant dragonflies) | Blaze, Puffy, Diamondia, **Sprinkle** (v10, ice world with water jets, like Enceladus) |
| **Triangulum** (8) | Axolotia (axolotls), Capybaria (tricky: very close to a red dwarf, capybaras in hot springs), **Octopia** (v10, tricky: very far from a blue star, octopuses) | Boingo (gravity too weak), Splashia (ocean world, no ground) | Frostbite (like Pluto), Smogball (like Venus), **Lavaland** (v10, volcanoes, like Io) |
| **Cartwheel** (6, new, surprise) | Quokka Rock (two suns, quokkas), Glowmere (tricky: very far from a blue star, glowing seas) | Dusty (no water, like Mars), Gloop (no oxygen yet, like young Earth) | Pulsaria (circles a pulsar), Lonesome (rogue planet with no star, 3/6) |

Each planet has: name, `gal`, colors, look, gravity, star, star distance, day, size, telescope note, checks with short text, landing animation type (`react`), caption, what was found, and a real-science fact. Made-up things are always labeled as made up.

**Star types:** yellow, orange, two suns, red dwarf, blue, black hole, **pulsar** (new), **no star** (new). Stars that are never comfy have `hint` text, and `dist` text when "distance from star" needs special words.

**Galaxy facts used:** Andromeda about 2.5 million light-years away; Triangulum about 2.7 million light-years, about 40 billion stars; Cartwheel about 500 million light-years, ring shape from a galaxy crash.

**Wormhole science (keep it honest):** wormholes are an idea from Einstein's math; nobody has found one; the game's wormhole is made up (the last story page says this). The paper-fold picture and "a wormhole would look like a ball" are standard physics explanations.

## 6. Discoveries (71 since v12)

- **Space and time (9, new in v8):** 8-minute-old sunshine, a light-year, starlight from long ago, space-time (trampoline), a tiny bit of time travel (Space Station astronauts), the Big Bang, a day longer than a year (Venus), short and long years (Mercury, Neptune), atomic clock.
- **Things in space (12):** old satellite, comet, Ed White's lost glove, tardigrade, Voyager golden record, space whale (made up), ancient meteorite, space ice, faraway galaxy, dino-shaped rock (made up), James Webb telescope, Moon footprints.
- **50 new facts in v12**, in 5 new groups (the full list is below): Gravity (6), Stars and constellations (15), Comets and space rocks (5), Water and life (8), The big universe (16).

The Discovery log shows all 7 groups, each with "found / total".

Since v9 every discovery has a Zib joke (`JOKES`) and a small animated cartoon (`TOONS`), both keyed by the discovery id. Cartoons must stay true to the science (the comet's tail points away from the Sun; Sputnik is next to a beach ball of the same size; Venus finishes its trip around the Sun when its spin is only 93% done; the clock in space is the slower one).

**v12 facts** are stored with their own joke (`j`), a short label for the cartoon (`cap`), a group (`g`), and a quiz question (`q`) with 3 answers (`a`, the right answer first; the game shuffles them). Their cartoon is `emojiToon`: the fact's emoji bounces, sparkles circle, and the label explains it. 12 of the older facts also got a quiz question (`OLD_Q`), so **62 facts** can be quiz questions.

**To add a discovery:** add it to `DISCOVERIES` with `id`, `g`, `title` (starting with one emoji), `fact`, `j`, `cap` (28 characters or fewer), `q`, and `a`. Write for an 8-year-old, keep it true, and label anything made up. Jokes are in Zib's voice ("I") and must not use "he", "she", "his", "him", or "her". Wrong answers should be clearly wrong (some can be silly), never a second true answer.

**Science notes for v12 facts** (so they stay accurate): "more than 6,000 exoplanets" is the NASA count passed in 2025; Europa Clipper launched in 2024 and arrives in 2030 ("is on its way"); the Andromeda crash is written as "might", because a 2025 study found it is only about a 50-50 chance; "more stars than sand" is an estimate ("Scientists think"); the neutron-star spoonful "as heavy as a mountain" follows NASA's comparison; Jupiter's gravity is measured at its cloud tops.

**The 50 new facts (v12):**

**🍎 Gravity (6)**

- **🍎 Gravity pulls** — Gravity is a pull. Earth pulls on you, so you always come back down when you jump. The Sun's gravity keeps all the planets going around it.
- **🌙 Super jumps on the Moon** — The Moon's gravity is much weaker than Earth's. On the Moon, you would weigh about 6 times less, so you could jump much, much higher!
- **🏋️ Heavy on Jupiter** — Jupiter's gravity is about 2 and a half times as strong as Earth's. A cat that weighs 10 pounds at home would feel like 25 pounds there!
- **🧑‍🚀 Why astronauts float** — Astronauts on the Space Station float because they and their station are falling around Earth together, all the time. Gravity is still there!
- **🌊 The Moon pulls the sea** — The Moon's gravity pulls on Earth's oceans. That makes the tides: the sea comes up the beach and goes back out, about twice a day.
- **🥔 Why planets are round** — Big things in space are round because their own gravity pulls them into a ball. Small asteroids have weak gravity, so many are lumpy, like potatoes!

**⭐ Stars and constellations (15)**

- **☀️ The Sun is a star** — The Sun is a star, just like the stars you see at night. It looks big and bright because it is much, much closer to us.
- **🟡 A giant Sun** — The Sun is so big that more than 1 million Earths could fit inside it!
- **🌈 Stars come in colors** — Stars come in colors! Red stars are the coolest. Blue stars are the hottest. Our Sun is in the middle.
- **☁️ Star nurseries** — New stars are born in giant clouds of gas and dust called nebulas. Some nebulas are so big that light takes years to cross them!
- **💥 A supernova** — When a giant star runs out of fuel, it can explode. This is called a supernova. For a little while, it can shine brighter than a whole galaxy!
- **✨ You are made of stardust** — Lots of the stuff in your body, like the iron in your blood, was made inside stars a long, long time ago. You are made of stardust!
- **🔭 Our nearest star friend** — After the Sun, the closest star to us is Proxima Centauri. Its light takes more than 4 years to get here!
- **🏖️ More stars than sand** — Scientists think there are more stars in the universe than grains of sand on all of Earth's beaches!
- **⭐ Why stars twinkle** — Stars twinkle because the air around Earth is always moving, and it wiggles their light. Out in space, stars do not twinkle at all!
- **🧲 A neutron star** — A neutron star is the tiny leftover of a giant star that exploded. It is about as wide as a city, but one spoonful of it would weigh as much as a mountain!
- **🔴 The Sun will grow old** — In about 5 billion years, our Sun will puff up into a huge red giant star. Do not worry: that is a very, very long time from now!
- **🌟 Constellations** — A constellation is a group of stars that people imagined as a picture, like a hunter, a bear, or a swan. Scientists use 88 of them to map the sky.
- **🥄 The Big Dipper** — The Big Dipper is 7 bright stars that look like a giant spoon. They are part of a constellation called the Great Bear.
- **🧭 The North Star** — The North Star, called Polaris, stays in almost the same spot in our sky all night. For hundreds of years, sailors used it to find which way is north.
- **🏹 Orion the Hunter** — Orion is a constellation shaped like a hunter. Three bright stars in a row make the hunter's belt. You can spot them on winter evenings.

**☄️ Comets and space rocks (5)**

- **🌠 Shooting stars** — A shooting star is not a star at all! It is a tiny piece of space rock, often smaller than a pea, burning up as it zooms into the air.
- **☄️ Halley's Comet** — Halley's Comet comes back near Earth about every 76 years. Its next visit is in 2061. How old will you be?
- **🪨 The asteroid belt** — Between Mars and Jupiter there are millions of space rocks called asteroids. They are so far apart that spaceships fly through safely!
- **❄️ Giant comet tails** — A comet is small, but when it gets near the Sun, its ice turns into gas. Then its tail can stretch for millions of miles!
- **🕳️ Moon craters** — The Moon is covered in holes called craters. Space rocks crashed into it long ago. With no wind or rain, the holes are still there.

**💧 Water and life (8)**

- **🥣 The Goldilocks zone** — Around every star there is a "just right" zone. Planets there are not too hot and not too cold, so water can stay liquid.
- **💧 Life needs water** — Every living thing we know needs water: plants, animals, and even tiny germs. That is why scientists look for water on other worlds.
- **🧊 An ocean under the ice** — Jupiter's moon Europa has a salty ocean hidden under its ice. A spacecraft called Europa Clipper is on its way there to learn more!
- **🏜️ Mars had rivers** — Long ago, Mars had rivers and lakes. Today its water is frozen into ice, at the poles and under the ground.
- **🪐 Planets around other stars** — Scientists have found more than 6,000 planets around other stars! They are called exoplanets, and scientists keep finding new ones.
- **7️⃣ A family of 7 planets** — A small red star called TRAPPIST-1 has 7 rocky planets about the size of Earth. A few of them are in the "just right" zone!
- **🌍 Only one home so far** — So far, Earth is the only place where we have found life. Scientists are still looking: on Mars, on icy moons, and around other stars.
- **🌧️ Titan's strange rain** — Saturn's moon Titan has rain, rivers, and lakes. But they are not water! They are made of methane, which turns liquid when it is super cold.

**🌌 The big universe (16)**

- **⚫ What is a black hole?** — A black hole is a place where gravity is so strong that nothing can get out, not even light. That is why it looks black.
- **📸 A picture of a black hole** — In 2019, scientists showed the first picture of a black hole. It looked like a glowing orange ring, like a donut!
- **⚡ The fastest thing** — Light is the fastest thing there is. In just one second, it could zoom around Earth about 7 times!
- **🤫 Space is silent** — Sound needs air to travel. Space has almost no air, so it is silent. A big explosion in space would make no sound at all!
- **🥛 Why the Milky Way?** — On a very dark night, our galaxy looks like a pale, milky stripe across the sky. That is how it got its name!
- **💫 Galaxies might bump** — The Andromeda Galaxy and our Milky Way are moving toward each other. Billions of years from now, they might crash and join into one giant galaxy. Scientists are still checking if it will really happen!
- **🙈 Invisible stuff** — Most of the stuff in the universe is invisible! Scientists call it dark matter. They know it is there because its gravity pulls on stars, but nobody knows what it is yet.
- **💙 Blue sunsets on Mars** — On Earth, sunsets are orange and red. On Mars, sunsets look blue! The fine Mars dust spreads the sunlight in a different way.
- **🌕 Moonlight is sunlight** — The Moon does not make its own light. It shines because sunlight bounces off it.
- **🌓 Does the Moon change shape?** — The Moon seems to change shape every month. But it is always round! We just see different amounts of its sunny side.
- **🌀 A six-sided storm** — At Saturn's north pole there is a giant storm shaped like a hexagon, with 6 sides. It is wider than Earth!
- **👃 Space smells funny** — Astronauts say that after a spacewalk, their suits smell a bit like burnt steak or hot metal!
- **🌅 16 sunrises a day** — The Space Station zooms around Earth about 16 times every day. So the astronauts can see about 16 sunrises and 16 sunsets every day!
- **👣 First steps in space** — Yuri Gagarin was the first person in space, in 1961. Just 8 years later, in 1969, astronauts walked on the Moon!
- **💡 The brightest dot** — Often the brightest dot in the night sky, after the Moon, is not a star at all. It is the planet Venus!
- **🌌 Northern lights** — The northern lights happen when tiny bits from the Sun hit the air high above Earth and make it glow green, pink, and purple.

## 7. Saving

- Inside Claude: saved with `window.storage` (key `moonbase-mission-save`). Fields: `colonies`, `found`, `cfg` (Workshop answers), since v8 `gal` (current galaxy id), `seen` (planets visited), `done` (galaxies finished), and since v9 `gems` (diamonds), `rank` (last announced status), `read` (planets whose explore diamond was paid), `from` (the galaxy you came from, for the take-off picture).
- `fixSave()` repairs old or broken saves: a v7 save starts in the Milky Way, and its colonies count as visited planets; a v8 save gets 0 diamonds and Space Cadet.
- v10 adds `v10` (set once; an older save that was in the Milky Way is moved to the Solar System, and keeps its colonies, visits, and diamonds), `story` (the story was watched), and the `read` list also holds `g:<planet>` (guess diamond paid) and `n:<planet>` (smart-no diamond paid). The new Workshop answers default to Explorer mode, sounds on, voice on.
- v13 adds `picked` (the explorer was chosen), `jn` (journey number, from 0), `jstep` (mission 0–2 inside the journey), `jshown` (the journey's cartoon and card were shown), `jpaid` (journey reward paid), `jdone` (journeys finished), and `vname` (the chosen voice). The mission object also has `step`. A v12 save starts journey 1 at mission 1 and is asked to choose an explorer once.
- v12 adds `build` (each colony's stage 1–4 and what is broken: `{ s, b }`), `mis` (the current mission: goal key, count needed, count so far, number, started, done, paid), `mpos` and `mnum` (where we are in the mission list, and how many missions so far), and `qa` (the last 12 quiz questions). The `read` list also holds `c:<planet>` (treasure paid). `fixSave()` treats older colonies as finished, drops a broken mission, and keeps an earned status even under the harder rules.
- Downloaded or hosted file: `window.storage` does not exist, so progress resets on reload. **Planned fix later** (see roadmap).
- Never use `localStorage` inside Claude's preview; it fails there. It is fine on GitHub Pages.

## 8. Game Workshop (since v7)

A form on the title screen. Alice and Dad answer questions, and the game changes. Answers are saved with the colonies.
The form is built from one list in the code (`WORKSHOP`). Each section is a tab. Each question has a key in `CFG`.

| Section | Questions (key: choices, default first) |
|---|---|
| 📖 Story | `player` (v9): who is playing, shown in the ribbon (empty = hero name only) · `hero`: name, "Captain Whiskers" · `pron`: he / she / they · `base`: base name, "Moon Base Meow" · `extra`: own last story page (empty = no extra page) |
| 🐱 Characters | `char` (v13): cat, platypus, axolotl · `fur` (cats only): orange, gray, black, white, pink, blue · `hat`: nothing, bow, crown, party hat, cap (v13), flower (v13) · `glasses` (v13): none, round, star, sunglasses · `face` (v13): nothing, curly mustache, fluffy beard, freckles · `suit` (v13): white, pink, blue, gold, green, purple · `alien`: green, purple, red, blue · `zname` (v9): the mascot's name, "Zib" · `zib` (v9): mascot color: purple, teal, pink, blue, orange |
| 🧠 Strategy | `mode` (v10): Explorer (easy), Captain (harder) · `fuel`: 7 (5–10) · `days`: 26 (18–36, steps of 2) · `fly`: normal 26 s, short 16 s, long 38 s · `rocks`: normal, a few (×1.5 spawn gap), lots (×0.65) · `pips`: 3, 2, 4 |
| 🎨 Graphics | `sky`: purple, blue, black, teal, pink · `stars`: normal 90, few 35, lots 220 · `toons` (v9): show the take-off and landing cartoons: yes, no · `sound` (v10): yes, no · `voice` (v10): read the words out loud: yes, no · `flame`: orange, blue, green, pink, rainbow |
| ✏️ Design | `theme` (card color): lavender, mint, peach, sky, lemon · `btn`: orange, pink, green, blue, yellow · `text`: normal, big · `font`: playful, plain, storybook |
| 📝 Wish list | `next`: hero powers, build the colony, sounds, design my own planet · `idea`: free text. "Show all our answers" makes a text summary to copy and paste to Claude. |

How it works:
- `tx()` puts the hero name, he/she/they, the base name, and (v9) the mascot's name into all game text (cards, toasts, speech bubbles, story, cartoon labels). Typed text is escaped, so it cannot break the page.
- The game's own text is still written with "Captain Whiskers", "his", and "him". **Keep writing new text that way**; `tx()` swaps the words. Do not use "his" or "him" for anyone except the hero. Write the mascot as "Zib" (no "he" or "she"); `tx()` and `zx()` swap in the Workshop name.
- `cleanCfg()` checks saved answers when loading. Unknown or broken answers go back to the default.
- Strategy answers start with the next mission. All other answers are used right away.
- "Go back to the original game" needs two taps and resets only the Workshop answers (not colonies or discoveries).
- **To add a question:** add it to `WORKSHOP`, add a default in `CFG_DEFAULT`, use `CFG.<key>` in the game, and add it to this table.
- Limits: canvas labels (for example "Boing!") keep the playful font. Kittens use the same fur and hat as the hero. The rocket in the cartoons uses the Workshop flame color, and the hero in its window uses the fur and hat.

## 9. Zib, diamonds, status, and the top ribbon (new in v9)

- **Zib** is the mascot: a friendly alien scientist with one big eye, goggles, and a flask (`drawZib`). Zib is **not** the grumpy alien you dodge. The Workshop can change Zib's name and color.
- **Ribbon look (v12):** the diamond counter is bigger (40 px). The status bar now shows what the next status needs (💎, 🪐, 🏠). A **mission row** fills the bottom of the ribbon: since v13 the journey icon and 3 dots (gold = done), then the mission goal, a gold bar, and x / y (✅ when done). The colonies chip shows 🏠 finished · 🏗️ building · 🔧 needs a fix. About 148 px tall on a phone, 119 px on a laptop.
- **Ribbon look (v11):** taller and brighter. Left: a big hero face with a gold ring, the name, the status as a gold badge with its own icon (`RANK_ICON`), and a bar that fills up toward the next status ("3 more 💎"). Right (first row on phones): a **big diamond counter**. The small chips (shield, colonies, trips or fuel, days, sound) sit in a second row on phones and in the middle on laptops. About 115 px tall on a phone, 84 px on a laptop.
- **Flying diamonds (v11):** `addGems(n, x, y)` makes up to 6 diamonds fly from where they were found to the counter (`flyGems`), each with a rising note; the counter jumps and shows "+n" (`gemPop`). Switched off for "reduce motion".
- **Sound button (v10):** the 🔊 chip in the ribbon turns sounds and the voice on or off together (`toggleSound`). In Explorer mode the ribbon shows 🚀 trips left instead of ⛽ fuel and hides 📅 days.
- **Top ribbon** (`#ribbon`, always on screen, `updateRibbon()` runs every frame but only redraws when something changed): hero face, player name and hero name, 🎓 status, 🛡️ shield pips (the "life"; full when not flying), 🏠 colonies built (all galaxies), ⛽ fuel and 📅 days (hidden until a mission starts), 💎 diamonds. The ribbon's height is measured and stored in `--rib` / `ribH`; cards, the trip bar, toasts, and speech bubbles start below it. On phones the ribbon has two rows.
- **Diamonds** (`addGems`): the total only goes up. There is nothing to buy yet; diamonds only raise the status.
- **Happy dance** (`celebrate`, bigger in v12: a big gold "+5 💎" pops up, Zib is 120 px, more diamonds fly): every time diamonds arrive, one of 6 dances plays and never the same one twice in a row: Zib jumps, spins, wiggles, zooms across the screen, the hero does a flip, or diamonds rain down. While flying, the dance is small and in the bottom-left corner so it does not hide the cat. Dances are switched off for people who turn on "reduce motion".
- **New status** (`maybeRank`, `rankToon`): a full-screen card. First a drum roll, then a different joke cartoon for each status: goggles that are too big, bubbles everywhere, a serious mustache, a tiny rocket parade, a hat that covers the hero, and for Professor of Space a square hat, fireworks, and Zib falling over. It never interrupts flying: it waits for a knowledge star pause, the colony report, or the colony screen.
- **Choose a galaxy** (`galaxyPicker`, `chooseGalaxy`): a card per galaxy with a picture, a real fact, and the visited count. Choosing one plays "How a wormhole works" and the tunnel flight (`wormPick` tells `wormFlight` where to go).

## 9b. Read-aloud voice (new in v10)

- `say(text)` uses the browser's own voice (Web Speech API). No files. `say([[text, true], [text2, false]])` speaks several parts; `true` means Zib's squeaky high voice.
- **v13, a nicer voice:** `voiceScore` ranks the device's English voices: "Natural" or "Neural" voices first (Microsoft Edge), then "Premium" and "Enhanced" (Apple), then known good voices (Ava, Samantha, Zoe, Allison, Aria, Jenny, Ana, Emma, Google US English...). Joke voices and old robot voices (Albert, Bubbles, Zarvox, Fred, Junior, Ralph, Kathy, and others) are never used. The list updates when the device finishes loading its voices (`voiceschanged`).
- **v13, smoother reading:** text is spoken one sentence at a time (Chrome sometimes stops long speech in the middle). The narrator is a little slower (rate 0.92, pitch 1.02), and Zib is less squeaky (rate 1.0, pitch 1.45, before: 1.7).
- **v13, voice chooser:** More → 🗣️ Choose the voice lists the 10 best voices on the device, best first, with ▶ to listen and **Use** to pick one (saved in `SAVE.vname`). It also tells grown-ups where to download nicer voices (iPhone / iPad: Settings → Accessibility → Spoken Content → Voices; Edge: "Natural" voices).
- Since v12 it also reads: mission start and complete cards, quiz questions and their answers, the rover quest, find cards with the reason why, radio news and SOS calls, the police stop, the broken ship, pirates, and bump tips on the rover road.
- It reads: story pages, the guess card, the landing speech bubble and guess result, every explore circle, the decide card (what was found + real science + the question), "Hmm, not here!", colony results, mission complete, new status, and knowledge stars (Zib's joke in the squeaky voice, then the fact).
- `plain()` removes tags and emoji and says "degrees Fahrenheit" and "times". `hush()` stops the voice; every new card stops the old voice first. "🔊 Read to me" buttons repeat the last text (`sayAgain`), even when the voice is switched off.
- **Limits:** the voice is still the device's computer voice, so it sounds different on each device; v13 picks the best one, but cannot make a poor voice better. The headless test browser has no voices at all, so the ranking and the chooser were tested for errors only, **not by ear**. Real recordings are on the roadmap. It was tested for errors in Chromium, **not by ear**, and **not inside Claude's preview** (some previews block speech; then the game stays silent and everything else works).
- **Rule for new text:** anything Alice must understand to keep playing has to be spoken. Keep it short.
- **Rule for cards (v11):** a card in Explorer mode has a picture or cartoon, at most one short thing from Zib (`zsay`), and big buttons. Long text goes under "📖 More". Zib's lines use the squeaky voice (`say(text, true)`).

## 9c. The journey map (new in v11)

`journeyScreen(pick)` shows the story so far, in story order: Moon Base (with a Story button), Solar System, Milky Way, Andromeda, Triangulum, and the surprise galaxy (a "?" until it was reached).
- Each place shows its picture, "x of y planets", and one circle per planet: a small planet picture when discovered (with 🏠 if it has a colony), a "?" when not. Tapping a discovered planet makes Zib say its short fact (`sticker`).
- The top shows totals: planets discovered of 45, and colonies.
- With `pick = true` it is step 1 of a mission ("Where do we explore?"). `galaxyPicker()` now just opens it.
- Progress also shows as a bar (`progressHTML`) on the start screen, on "Mission complete!", and on the colony result card. Landing on a new planet shows "New planet discovered! x of y".

## 9d. The rover (new in v11, a quest since v12)

After landing, `startRove()` sets `state = 'rove'` (both modes).
- The hero hops from the parked rocket onto the rover (1.1 s). If she made a hot / cold guess, Zib first says if it was right.
- **The quest (v12):** the rover needs help. One of 3 problems (`QUESTS`): 🔋 the battery is empty, 🛞 a wheel fell off (only on planets with ground), or 🔑 Zib lost the key. A card with a cartoon (the planet's scene, the rover with smoke, the problem's icon) asks one space question (section 3c). Right: +1 💎. Then the rover can drive.
- **Controls:** ◀ ▶ buttons, arrow keys or A / D, or hold a finger or the mouse button to the left or right of the rover. ⬆, the up arrow, W, or the space bar jumps.
- **Gravity you can feel:** jump height and hang time follow the planet's real gravity (clamped to 0.18–2.5× Earth so jumps stay on screen). Pluto and Mercury: high, slow jumps. Chonk: tiny hops.
- **Branching roads (v13):** the road is a little tree (`R.segs`). The first road leads to a **fork** with an up road and a down road; one goes on, the other is a **dead end**. There are 3 forks. Only the right roads have the 5 glowing circles and, at the very end, the treasure chest.
  - At a fork the rover stops at a signpost (⬆ and ⬇), Zib says "A fork in the road! Up or down?", and two big buttons appear: **⬆ Up road** and **⬇ Down road** (or the up and down arrow keys).
  - The down road looks darker, the up road a little lighter, and each starts with a sign.
  - A dead end has a red-and-white barrier and 🚧: "Dead end! Drive back to the fork and try the other road." Driving left past the start of a road goes back to its fork. About 6 in 10 dead ends hide a 💎 (+1).
  - **Road map:** a small map in the top-left corner draws the roads found so far: gold for good roads, pink for dead ends (✗ when reached), dashed lines for roads not tried yet, 🎁 at the end, and a blue dot for the rover.
  - **Platypus power:** the signpost shows 🚫 on the dead-end arrow, and Zib says which road is the dead end.
  - Sizes: each road is about 1.1 screens (at least 620 px) times 1.0–1.3; dead ends are 0.6 of that. Driving the right roads without bumps takes about 13 s on a phone and 18 s on a laptop. Obstacles are on every road (also dead ends), sized to the planet's gravity as in v12. A test drove all 45 planets, taking the right roads, and reached the treasure on every one; another test tried a dead end first and came back.
- **The road (v12)** had no forks. Between the circles there are 1 or 2 things to jump over: **rocks**, **pools** (water if the planet has water, lava if it is hot, purple goo otherwise), and **space pirates** (made up: a little green alien with a hat, an eye patch, and a wooden sword; at most 2 per planet). Planets with no ground get **storm puffs** and pirates instead. The first one is always a rock (or a storm puff).
- Planets with no ground (gas giants, ocean worlds, Floatopia): the rover floats on two jets.
- All 5 finds pay 1 💎 once per planet. "Done ➜" (top right) appears only after all 5 finds, or after 120 seconds (v13; was 90), so the quest comes first.

## 9e. Explorers and their super powers (new in v13)

`CHARS` holds the 3 explorers. The hero is still drawn by `drawCat`, which now draws the chosen animal. The powers are made up; each card has a real science fact under "📖 Real science".

| Explorer | Default name | Super power | What it does | Real science |
|---|---|---|---|---|
| Space cat | Captain Whiskers | Cat reflexes | the shield refills twice as fast | cats can twist in the air and land on their feet |
| Space platypus | Professor Paddles | Electric sense | stardust, diamonds, and fish slide toward the ship; on the rover, the dead-end road is marked 🚫 | platypuses close their eyes underwater and find food by sensing tiny electric signals with their bills |
| Space axolotl | Lottie the Axolotl | Regrow | a crack on the ship heals every 10 s | axolotls can grow back a lost leg, a tail, and even parts of their heart |

- **Looks:** hat (nothing, bow, crown, party hat, cap, flower), glasses (none, round, star, sunglasses), face (nothing, curly mustache, fluffy beard, freckles), space suit color (white, pink, blue, gold, green, purple), and fur color for the cat. The platypus is brown with a dark bill and a flat tail; the axolotl is pink with 3 feathery gills on each side and a big smile.
- **Name:** picking an animal changes the hero's name to that animal's default name, unless the name was typed in the Workshop.
- The colony kittens are drawn as the same animal as the hero.
- The Workshop's Characters tab has the same choices.

## 10. Cartoons (new in v8)

One small engine: `playToon(kind, seconds, next)` sets `state = 'toon'`; `drawToon()` draws it; when the time is up (or on a tap after 0.8 s) `endToon()` runs `next`.

| Cartoon | Length | When | What it shows |
|---|---|---|---|
| `takeoff` | 5 s | after "Fly here" | suit on → hop in → engines on → blast off (from the Moon Base, a wormhole gate, or the planet) |
| `touchdown` | 4.5 s | after the flight | rocket lands, dust, hero hops out (hovers if there is no ground) |
| `blackhole` | 5 s | touching a mini black hole | bent space, slow clock near the hole, fast clock back home |
| `colony` (v11) | 8 s | after 👍 on a planet with 4–6 green lights (both modes) | on the planet's own scene: a dome pops up, a second dome and a tunnel, a farm, one machine that fixes the planet's first problem (heater, cooler, wall, gym, water machine, balloons, or a garden on a perfect planet), a solar panel, 5 kittens hop out of the rocket, a flag. No-ground planets get a platform held by balloons |
| `worm` | 9 s | giant wormhole trip | fly into the ball → light tunnel (wiggles if it is an accident) → new galaxy appears |
| `police` (v12) | 4.5 s | pulled over by the space police | red and blue flashes, the saucer comes down next to the rocket: "Wee-woo!", "You were zooming much too fast!", "Answer my space question, and you can go!" |
| `broke` (v13: 2.4 s) | 2.4 s | the ship's 3rd crack | the ship sputters, smokes, and sparks; then one fun question |
| `tow` (v13) | 4.2 s | wrong answer after the ship broke | Zib's TOW saucer pulls the ship off the screen: "Back to the base for repairs!" (the second half of the old `broke` cartoon) |
| `journey` (v13) | 13 s | a new journey starts | 3 scenes with a line from Zib each (section 3b), the journey's name at the bottom |
| `repair` (v12) | 4.5 s | a repair trip | the rocket lands next to the colony's domes, the broken machine sparks: "Oh no! The water machine is broken!" |

v12 card cartoons (drawn into the card canvas): `missionToon` (the goal icon in a glowing circle with a rocket going around it, or a bouncing trophy with confetti), `questPic` (the planet scene with the smoking rover), `colonyPic` (the colony's domes and the broken machine sparking, or fixed with happy kittens), `copPic`, and `brokePic` (Zib with a hammer and a bandaged rocket).

"How a wormhole works" (4 pages) reuses the story player (`storyMode = 'worm'`, text in `WORM_STORY`, pictures in `drawWormStory`).

## 11. Code map (v13)

v10 additions, in file order: 15 new entries at the end of `POOL`; the `sol` entry in `GALAXIES`; `mode` / `sound` / `voice` in `WORKSHOP`; boost controls (`boostEl`, `boosting`); the **sound and voice block** (`audio`, `tone`, `SFX`, `sfx`, `say`, `hush`, `plain`, `toggleSound`); `hop`, `atHome`, `wasSeen`, `leaveSol`; the **Explorer block** just before `mapScreen` (`ICON`, `STAR_KID`, `tempTruth`, `lightsHTML`, `starPic`, `mapEasy`, `pickEasy`, `guessScreen`, `guessEasy`, `decideEasy`, `yesEasy`, `noEasy`, `afterNo`, `missionEnd`, `homeCard`); `spawnBits`, `drawBit`; creatures `penguin`, `koala`, `octopus`; scene `earth` and extras in `sink` / `cold` / `dust`. Each mission remembers its own mode in `G.easy`, so changing the Workshop answer starts with the next mission.

v11 additions: ribbon (`RANK_ICON`, `gemPop`, `flyGems`); `progressHTML`, `titleScreen`, `play`, `moreScreen`; `sticker`, `journeyScreen`; the **card block** (`cardCanvas`, `drawCard`, `miniScene`, `guessToon`, `zsay`, `shortFact`, `steps3`); the **rover block** (`startRove`, `foundItem`, `roveDone`, `updateRove`, `drawRover`, `drawRove`); `drawColonyToon`. `drawScene(p)` now takes a planet. A card's cartoon is drawn every frame into `#cardCvs` (480 × 270) by `drawCard`, which lets the scene code believe the small canvas is the whole screen. The old tap-circle code (`showExplore`, `explorePt`) is still in the file but is no longer used.

v13 additions: `CHARS` and `SUIT` (before `ALIEN`); `char`, `glasses`, `face`, `suit`, and new hats in `WORKSHOP` and `CFG_DEFAULT`; `drawGlasses`, `drawFace`, and a new `drawCat` (cat, platypus, axolotl); `voiceScore`, `voiceList`, and sentence-by-sentence `say(x, zib, force, voice)`; the **v13 block** just before the v12 block (`setHeroName`, `heroPic`, `explorerToon`, `explorerScreen`, `pickChar`, `xOpt`, `explorerDone`; `JOURNEYS`, `MICON`, `hasLife`, `curJourney`, `jLevel`, `needFor`, `newMission`, `journeyIntro`, `journeyCard`, `startJourney`, `journeyDoneCard`, `nextJourney`, `journeyPic`, `drawJourneyToon`; `wormTargets`, `galaxyJump`, `wormLanded`, `wormBack`; `voiceScreen`, `tryVoice`, `useVoice`); the old `MISSIONS` list and `missionOk` are gone; rover roads (`reachFork`, `forkGo`, `reachDeadEnd`, `drawRoadMap`, `R.seg` / `R.segs` / `R.mains` instead of `R.items` / `R.obs` / `R.L`); `towHome`, `drawBall`. HTML adds `#rvFork`.

v12 additions: the 50 new facts at the end of `DISCOVERIES`, then `OLD_Q`, `FACT_GROUPS`, `groupOf`; jokes copied into `JOKES`; `emojiToon` and `factGroup` before `openFact`; new sounds in `SFX`; the **v12 block** just before `mapScreen` (`pickQuiz`, `quizCard`, `quizPick`, `quizAgain`, `quizNext`; `BREAK`, `STAGE`, `buildOf`, `colsDone`, `colsBuilding`, `colsBroken`, `colonyTick`, `radioOff`, `showRadio`, `repairTrip`, `repairCard`; `MISSIONS`, `MTEXT`, `MSAY`, `missionOk`, `newMission`, `missionEvent`, `missionStartCard`, `startMission`, `missionDoneCard`, `nextMission`; `coreHTML`; `pullOver`, `shipBroke`; drawings `drawSaucer`, `drawCop`, `drawPirateShip`, `drawPirate`, `drawPoliceToon`, `drawBrokeToon`, `drawRepairToon`, `copPic`, `brokePic`, `colonyPic`, `missionToon`, `questPic`); `fixTiles` before `pickEasy`; the rover block now has `QUESTS`, `ROVE_SAY`, `questCard`, `roveBump`, `openChest`. HTML adds `#rbMis` (in the ribbon), `#hull` (in the HUD), and `#radio`. `#overlay` now has `z-index: 14` so cards sit above the rover buttons. New state `'quiz'` (the flight is frozen while the police ask). `RANKS` entries now have 4 parts.

One HTML file: CSS, then HTML (`#ribbon`, `#hud`, `#boost`, `#rove`, `#toast`, `#radio`, `#overlay`, `#explore`, `#caption`, `#fact`, `#cheer`, `#party`), then one script.
Script sections in order: star and planet data (`STARS`, `POOL`), galaxies (`GALAXIES`, `galaxy`, `inGalaxy`), `DISCOVERIES`, Game Workshop, setup and controls (`playToon`, `endToon`), save (`fixSave`), **v9 block** (`RANKS`, `zx`, `snap`, `drawZib`, `drawGem`, `updateRibbon`, `celebrate`, `addGems`, `maybeRank`, `rankToon`, `JOKES`, `TOONS`, `openFact`, `closeFact`, `drawFact`, `galaxyPicker`, `chooseGalaxy`), game setup (`prepareGame`, `newGame`, `pickNextGalaxy`, `galaxyDone`, `wormFlight`, `arriveGalaxy`, `tripCost`, `known`), screens (title, story and wormhole story, rules, discovery log, hints, star map (`planetPic`, `pickPlanet`, `mapScreen`), explore points `EXPLORE` / `showExplore` / `explorePt`, landing report, build colony, rescue), flight (`startFlight`, `spawnObstacle`, `spawnSpecial`, `update`), drawing (flight objects, creatures, `drawPlanet`, `drawCat`, `drawScene`, `drawStory`, v8 block: `drawRocket`, `drawGalaxy`, `drawWormSphere`, `drawTunnel`, `drawClock`, `drawTakeoff`, `drawTouchdown`, `drawBHToon`, `drawWormFlight`, `drawWormStory`, then `draw`), main loop.

**To add a planet:** add it to `POOL` with a `gal` (use `real: true` only for real worlds). Keep each galaxy able to make a mission (at least 1 perfect planet and 5 planets). If it needs a new landing scene, add a `case` in `drawScene` and a ground color in `GROUND`.
**To add a galaxy:** add it to `GALAXIES` (real name and real fact) and give it at least 5 planets with at least 1 perfect one.

## 12. Rules for making changes (for Claude)

- Read this file first. Make **targeted changes**; do not rewrite working code.
- Keep one self-contained HTML file with no outside libraries, unless we decide to split files.
- Keep all text readable for an 8-year-old. Keep science accurate and label made-up content.
- **Before adding anything, ask: does this add reading or planning for Alice?** If yes, put it in Captain mode only, or make it a picture, a sound, or a spoken line.
- Every fact needs a true, simple quiz question with the right answer first, and the other two answers clearly wrong.
- Test before sharing, in a real browser (Playwright with Chromium works in Claude's sandbox). Since v12 also: every fact's cartoon, every quiz question has 3 different answers, all 45 rover roads can be finished with jumps, the police / broken ship / repair / mission flows, and the mission list from start to level 2. Tests that run the game faster than real time must also wait for real timers (the quest card opens with `setTimeout`). syntax check; data rules (temperature rule, gravity rule, every galaxy can make a mission); draw every landing scene, cartoon, and story page; simulated full campaigns through all 4 galaxies (also starting from a chosen galaxy); all 21 knowledge star pauses, every status cartoon, and all 6 dances; both modes (Explorer and Captain) from the Solar System to the end; every Workshop answer; save/load round trip and an old save; one real-time click-through of a whole trip; screenshots at laptop and phone size. In test scripts, never run `pkill -f` with a word that is also in the command itself.
- After each change, update **Changelog**, **Roadmap**, and any rules or numbers above.

## 13. Roadmap

Note (v10): Alice found the game too complex. She likes discovering planets and flying, and does not like reading and planning. So the plan changed: simplify first. "Choose your character" and "Build the colony" both add planning, so they are **paused** (kept at the end of this section).
Note (v12): Dad asked for more challenge and a clear goal. v12 adds challenge through action (dodging, jumping, quick questions read out loud) rather than reading and planning.

### v14: Talk to the planet (next)
- **Talk to creatures:** on the rover drive, stop next to a platypus, koala, or octopus. It says 1–2 short lines; pick one of 2 picture questions ("What do you eat?"); the answer is a real fact. Talking animals get a "pretend" label.
- **Things to find on the road** that belong to each planet (a rock sample, a hidden surprise), maybe at the end of some dead ends.
- **Sticker book:** the journey map's planet circles become full stickers with a picture and one sentence. It replaces the Discovery log.
- **Picture answers:** some quiz questions with pictures instead of words.
- **More journeys:** for example "Star Gazers" (knowledge stars and constellations) or "Gravity Testers" (planets with heavy and light gravity).

### v15: Our own voices, and saving everywhere
- Record Alice and Dad for the key lines (in-game recording or audio files). The computer voice stays as the fallback.
- Use `localStorage` when hosted (GitHub Pages) and `window.storage` inside Claude. A "Save code" button.

### Open questions from v13 (ask Alice and Dad)
- Which explorer does Alice pick? Is any power too strong (the platypus dead-end hint makes the roads easier)?
- Is a 13-second journey cartoon too long? Should it be shorter the second time?
- Are 3 forks per planet the right number? Are dead ends fun or annoying?
- Comet storm and two pirate ships: too hard with the 3-crack ship? Is one question to save the ship the right amount of help?
- 3 in 10 wormholes leave the place she is exploring. Too often?
- Does the voice sound better on Alice's device? Which voice did you pick in the chooser?

### Open questions from v12 (ask Alice and Dad)
- The knowledge star button waits until Zib has read (up to 16 seconds). Too long?
- The ship breaks after 3 cracks (with a full shield first, that is 6 bumps in a row). Too hard, too easy?
- Is the space police fun every trip, or should it come only sometimes?
- Colonies take 3 trips to finish, and a breakdown comes about 1 trip in 4. Right amount?
- Status steps (Junior Scientist: 30 💎, 5 planets, 1 finished colony). Too slow?
- Is the rover road (13 s on a phone, 19 s on a laptop) the right length? On heavy-gravity Chonk the hops are tiny, so jumps need good timing.
- Wrong quiz answer: one more question, then Zib helps. Right amount of help?
- Should starting a mission refill the rockets, or should the rockets only refill at "Out of rockets"?

### Open questions from v11 (ask Alice and Dad)
- Is the colony cartoon (8 s) fun every time, or should later colonies be shorter?
- Should Captain mode keep the rover, or go back to the quick tap circles?
- Should later places on the journey map be locked until the one before is finished? Today every place except the surprise galaxy can be chosen.

### Open questions from v10 (ask Alice and Dad)
- Is one guess per planet the right amount of thinking? Should the picture show the "comfy spot" after a wrong guess?
- Are 3 planets and 3 trips right, or would 4 planets and 3 trips make the choice more interesting?
- Diamonds now come faster (guesses, smart "no", stardust). In a test run with every guess right, Professor of Space came before the last galaxy. Raise the status steps?
- Is the knowledge star pause still fun now that Zib talks, or does it break the flying?
- Do the old Milky Way planets she already knows feel stale? They can be removed or swapped (v10 only puts new planets first).

### Paused: Build the colony
The old plan was a 5-turn strategy mode on a 4×4 grid with 8 buildings. If it comes back, make it "decorate your colony" with stickers, or keep the strategy version for Captain mode only.

### Backlog (ideas, not scheduled)
- Open questions from v9: status steps; should diamonds buy something (hats, rocket colors)? Should the player also choose the galaxy at each giant wormhole?
- Open question from v8: should the rocket also be drawn during the flight?
- Moons as places to visit in the Solar System (our Moon, Europa, Titan, Enceladus, Io). Dwarf planet Ceres. The asteroid belt between Mars and Jupiter as a flight zone.
- A map screen that shows the Solar System and all 4 galaxies. More surprise galaxies (Whirlpool, Sombrero).
- A parked rocket in the landing scenes. Explore circles placed on real things in each scene.
- Alice designs her own planet (name, gravity, star, distance), and the game checks whether the temperature makes sense.
- More knowledge stars (71 since v12). Achievements.
- More Workshop questions: number of trips, status speed, happy dances on/off, boost on/off.

## 14. Changelog

- **v1:** Firefly in the Rain (test game).
- **v2:** Captain Whiskers space game: real planets, fact cards, quizzes, clues.
- **v3:** Part 2 made-up planets. (Separate underwater spin-off: Captain Meowf, half cat and half dog.)
- **v4:** Moon Base Mission: strategy rules, fuel and days, probes, colony checklist, shuffled planets, no quizzes.
- **v5:** Animated story, illustrated how-to-play pages, Captain's hints.
- **v6:** 5 planets per mission, temperature puzzle (star + distance), 18 planets, flight zones, comets, wormholes, mini black holes, tricky fuel cans, 12 discoveries, permanent colonies, "galaxy explored" ending.
- **v7:** Game Workshop: a form with 6 sections (Story, Characters, Strategy, Graphics, Design, Wish list) and 21 questions that change the game and are saved.
- **v8:** Galaxies and cartoons.
  - 12 new planets (30 total) and 2 new star types (pulsar, no star). 7 new landing scenes and 3 new animals (axolotl, capybara, quokka).
  - Planets are split into 4 real galaxies: Milky Way (9), Andromeda (9), Triangulum (6), Cartwheel (6, surprise). We use "galaxies", not "universes", because the Milky Way is a galaxy and there is only one known universe.
  - Giant wormhole: opens when every planet in a galaxy was visited (or no mission is left). 4-page "How a wormhole works" story, a tunnel-flight cartoon, and a 1-in-3 chance of a wormhole accident that leads to the surprise galaxy.
  - Take-off cartoon (suit, hop in, engines, blast off) and landing cartoon (touchdown, hop out).
  - Landing scenes no longer end after 4 seconds. 5 glowing circles let you explore the planet before the colony report.
  - Black hole cartoon (5 s) that explains why time slows down.
  - 9 new "space and time" discoveries (21 total), found first; the Discovery log has two groups.
  - Save now keeps the galaxy, visited planets, and finished galaxies. Old saves still load.
  - "Start a new galaxy" became "Start over from the Milky Way".
  - Roadmap renumbered: character powers v9, colony building v10, saving everywhere v11.
- **v9:** Zib, diamonds, status, ribbon, simpler map, galaxy choice (all built on the galaxies v8).
  - Knowledge stars stop the flight. Zib the mascot alien reads the fact with a joke and one of 21 animated cartoons (9 new ones for the space-and-time facts).
  - Simpler star map: 5 planet tiles, one planet's details at a time.
  - Top ribbon on every screen: who is playing, status, shield, colonies, fuel, days, diamonds.
  - Diamonds from knowledge stars, flying diamonds, exploring all 5 circles, and new colonies. 6 different happy dances.
  - 7 statuses from Space Cadet to Professor of Space, each announced with its own funny cartoon.
  - Choose a galaxy to explore first (title screen). A chosen trip uses the wormhole story and tunnel flight.
  - Game Workshop: 4 new questions (player name, mascot name, mascot color, take-off and landing cartoons on/off). 25 questions in total.
  - Small fixes: toasts show above cards; the flight can no longer end in the same moment a cartoon starts.
  - Roadmap renumbered: character powers v10, colony building v11, saving everywhere v12.
- **v10:** Explorer mode, our Solar System, more planets, boost, sounds, and a voice.
  - New goal and a narrower learning goal (section 1), because the game was too complex for Alice.
  - **Explorer mode** (the new default): 3 planets, 3 trips, one hot / cold / just right guess, lights instead of a checklist, a 👍 / 👎 choice, no how-to-play pages, the story only the first time, and nothing to lose in flight. The full v9 game is still there as **Captain mode** (Game Workshop → Strategy).
  - **Our Solar System** is the new starting place: Mercury, Venus, Earth, Mars, Jupiter, Saturn, Uranus, Neptune, and Pluto, with real numbers and facts. New Earth landing scene; Jupiter's Great Red Spot, Saturn's rings in the sky, Neptune's wind, Pluto's slow high jumps, rusty red Mars.
  - **6 more made-up planets** (45 in total): Koalia, Pengwinia, Eyeball, Sprinkle, Lavaland, Octopia. 3 new animals: koala, penguin, octopus.
  - **New planets first:** every mission picks planets she has not visited before the ones she knows.
  - **Boost** (button, space bar, or mouse button) and **stardust trails** (10 = 1 💎).
  - **Sounds** made in code, and a **read-aloud voice** from the device; Zib has a squeaky voice. One 🔊 button in the ribbon turns both off.
  - Game Workshop: 3 new questions (how to play, sounds, voice). 28 questions in total.
  - Older saves keep everything and start with the Solar System tour.
  - Roadmap changed: flight fun v11, planet exploring v12, own voices and saving v13. Character powers and colony building are paused.
- **v11:** Zib cards with cartoons, the rover, the colony cartoon, a bigger ribbon, the journey map, and a simpler start.
  - **Cards:** the guess card and the decide card are short, sit in the middle, have a small live cartoon (the star and planet; the planet's own landing scene), and Zib says one thing in a speech bubble and out loud. Long text moved under "📖 More". Other Explorer cards were cut to one line from Zib.
  - **Rover:** after landing, the hero hops on a rover and drives to 5 glowing circles. Finds pop up in the middle with Zib. Jumps follow the planet's real gravity. This replaces the tap circles in both modes.
  - **Colony cartoon:** domes, a farm, a machine for the planet's problem, a solar panel, kittens, and a flag.
  - **Ribbon:** taller, with a big diamond counter, a gold status badge with an icon, and a bar toward the next status. Diamonds fly from where they were found up to the counter.
  - **Journey map:** every place in story order, every planet discovered, every colony. It is also step 1 of each mission.
  - **Start screen:** Play, My journey, More. A row of steps (Place → Planet → Guess → Fly) guides the start of a mission.
  - Knowledge star card: the joke is now only spoken; the card shows the title and the fact.
  - Roadmap: creature talks, sticker book, and the flight "big moment" moved to v12.
- **v12:** Missions with goals, 50 new facts with quiz questions, a harder and funnier flight, the rover quest, colonies that take time, and harder status.
  - **50 new real space facts** in 5 new groups (gravity, stars and constellations, comets and space rocks, water and life, the big universe), each with a Zib joke, a small cartoon, and a quiz question. 12 older facts also got questions. 71 facts in all; the Discovery log shows 7 groups.
  - **Missions:** a numbered goal (12 kinds, then harder rounds), a start card and a "Mission complete!" card with cartoons and +5 💎, and a mission row with a progress bar always in the top ribbon. "Mission complete!" after 3 trips is now "Out of rockets!"
  - **Flight:** one knowledge star per trip that drifts to the cat and cannot be skipped (button locked while Zib reads; +5 💎). Space police saucer (no boosting! pulled over: cartoon and a question). Space pirate ship (takes stardust). The ship has 3 hearts; 3 cracks break it, with a tow-truck cartoon back to the base. Colony radio news.
  - **Rover quest:** fix the rover with a question first, then a road about twice as long with rocks, pools, storm puffs, and pirates to jump over (sized to each planet's gravity), bigger find cards with the reason why, and a treasure chest at the end. "Done" waits until the 5 finds are done.
  - **Decide card:** 6 big boxes for ground, water, air, gravity, temperature, and safety.
  - **Colonies take time:** 3 more trips to finish (radio news each trip), sometimes a machine breaks (SOS), and a repair trip with a question fixes it.
  - **Status:** each status needs diamonds, planets explored, and finished colonies (Junior Scientist: 30 💎, 5 planets, 1 colony). The ribbon shows what is still needed. Bigger diamond counter and a bigger "+n 💎" celebration.
  - Roadmap renumbered: Talk to the planet v13, our own voices and saving v14.
- **v13:** Choose your explorer, journeys with cartoons, branching roads, harder flights, galaxy wormholes, and a nicer voice.
  - **Explorers:** a space cat, a space platypus, or a space axolotl, each with a super power (cat reflexes: faster shield; electric sense: stardust comes to you and dead ends are marked; regrow: cracks heal) and a real science fact. Dress-up: 6 hats, 4 glasses, 4 face choices (mustache, beard, freckles), 6 space suit colors, and fur colors for the cat. Picker on the start screen; first-time players see it after the story.
  - **Journeys:** missions now come in journeys of 3 with one big goal: 💧 Water Hunters, 🌱 Signs of Life, 🏠 New Home Builders. Each has a 13-second cartoon with Zib's voice, a journey card, and a "Journey complete!" card (+15 💎). The ribbon always shows the journey icon, 3 progress dots, and the current mission. New mission kinds: find planets with life, start a colony on a planet with water.
  - **Branching roads:** 3 forks per planet, each with a dead end (some hide a diamond), up and down road buttons, signposts, and a road map in the corner.
  - **Harder flights:** a comet storm, two pirate ships that fire cannonballs, and when the ship breaks, one fun question to fix it and keep flying (a wrong answer still means the tow truck).
  - **Galaxy wormholes:** 3 in 10 mini wormholes pull the ship into another galaxy. Stay, go back, or pick somewhere else.
  - **Voice:** picks the best voice on the device (Natural, Premium, Enhanced first), reads one sentence at a time, a softer Zib, and a voice chooser in More.
  - Roadmap renumbered: Talk to the planet v14, our own voices and saving v15. "Choose your character" is done, so it was taken off the paused list.
