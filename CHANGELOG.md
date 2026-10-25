# Changelog

Newest first. Each entry is also the release's notes.

## Editor 2026-10-25

The third release of the modder's toolkit, matching playtest build 2026-10-25b: the other peoples are data, bodies and gaits are data, and the editor is in the game zip.

**New since editor 2026-10-24 (b)**
- **Elves, dwarves and avians** are peoples in `Data/Peoples/`, with units (`Units/elves.unit`, `dwarves.unit`, `avians.unit`) and hosts (`Armies/peoples.archetype`). A people record gained `quality` (born drill), `courage`, `doctrine-budget`, `accuracy`, `frailty`, `relic-cost`, `rest-hours`, `infravision`, `wings` and `figure`; the peoples skill lists what each does in the sim.
- **Bodies and gaits are data.** `Data/Poses/body/*.body` is the rig (legs, trunk segments, where the upper body stands), `*.gait` how it steps ahead, sideways and back, `*.figure` a people's shape and colouring (height, build, skin, hair, beard, feathers, wings). An animator API takes a code plug-in for movement no data can describe. Worked samples under `Modding/samples/`: a millipede people and a riding dragon.
- **Flight**: a mount with a `flight` block (speed, ceiling, climb) flies; a unit all of fliers takes off and lands by order or rule (`TakeOff`, `Land`), goes straight over rivers, cliffs and walls, and is shot at only by volleys aimed up. No base flier; the dragon sample is the example.
- **Archeotech and dwarven kit**: `Items/archeotech.item` (the lance rifle, the monoblade, powered armour that `carries` weight for its wearer, `no-powder` firearms) and `Items/dwarven.item` (the great axe); pose files for each.
- **Locked formations**: `Data/Formations/locked.formation` describes the testudo and its kin: which ranks and files lock shields to the wall or the roof, the cover each gives, speed and melee factors; shields gained `wall` and `roof` poses. `data show <formation>`.
- **Doctrines**: a unit may start `aloft`; command squads may be of another people.
- **Rules**: `gait.rules` (the sim's pace sideways and back for foot and horse), `sky.rules` (the zenith sun, the eclipse hours, the night colours of fires and flashes), `smoke.rules` (powder smoke: the jet per musket and the bank that drifts along the line).
- **The toolkit**: the poses skill covers bodies, gaits, figures, animators and flight; the equipment skill the new item fields; the rules skill the three new records; `data list` and `check` count body plans and gait sets.

**Instructions**
- The game zip (playtest 2026-10-25b, <https://github.com/TMaluszynski/Doctrines-playtest/releases/tag/playtest-2026-10-25b>) carries `Editor/doctrines-editor.exe` beside the player; this zip is the tool on its own.
- To field the samples, copy `Modding/samples/millipede` or `Modding/samples/dragon` into `Doctrines_Data/StreamingAssets/Mods/`, run `doctrines-editor check`, start the game.

**Still code, on the list**: a `general` API for the commander's plan; attendants and wagon teams as behaviour files; camp, rout and officer constants; sounds from files; hand-made battlefields and maps; factions.

**Download:** the zip under Assets below. Unzip anywhere; README.txt inside says how to run it against your game folder.

## Editor 2026-10-24 (b)

The second release of the modder's toolkit, matching playtest build 2026-10-24h: behaviour is scriptable, the enemy's generals are data, and the editor now ships inside the game too.

**New since the first editor release**
- **Scripting.** A doctrine file may hold `when <expression> -> <action> [once]` rules beside its triggers: `when enemy.cavalry.distance < 200 and self.ammo < 0.3 -> form Square`. The expression reads what the unit sees (`self.*`, `enemy.*`, `friend.*` values and functions such as `enemy.within(150)`) with `and`, `or`, `not`, arithmetic and comparisons. A misspelt name is reported with file, line and the nearest real names.
- **Animal behaviour is a file.** `Data/Behaviours/horse.behaviour` drives the camp's horses and the loose horses on the field: states, rules and verbs (`fright`, `flee`, `wander`, `graze`, `break-loose`, `go`). Change it, or add your own in a mod.
- **The behaviour API** is printed by the tool: `doctrines-editor api` (or `api unit`, `api animal`) lists every value, function and action a script may use, straight from the tables the sim implements.
- **Commanders.** Every AI army is led by a commander with a perk, both records in `Data/Commanders/*.commander`: how he fights (his plan: advance, bounds, engagement range, strike force, flanking, scouts, baiting, withdrawal) and what his headquarters is (guard, station, habits). Archetype kinds carry a `role` (scout, skirmish, line, flank, strike); four new hosts. `data list commanders`, `data show <id>`.
- **Doctrines gained vocabulary**: trigger conditions `NoEnemyInSight`, `NoOrdersFor`, `FriendAtGripsWithin`, `FlankThreatened`, `AmmoBelow`, `Every`; actions `Charge`, `FireAtWill`, `HoldFire` and `drill <countermarch|volley|platoon|advancing>`.
- **Items**: firearms and crossbows have `armour-piercing`, `shield-piercing` and `stopping`; every weapon has `fragility` and `unused-fragility` (whether a freed prisoner can rearm from the fallen).
- **Rules**: `points.rules` gains `captain-budget` and retuned `drill-budget` (5 9 14 20 27).
- **The toolkit**: a new `behaviour-scripts` skill; `armies-and-ai` covers commanders, perks and roles; `new-mod` makes a `Commanders` folder.

**Instructions**
- The game zip (playtest 2026-10-24h, <https://github.com/TMaluszynski/Doctrines-playtest/releases/tag/playtest-2026-10-24h>) now carries `Editor/doctrines-editor.exe` beside the player, so this zip is only needed on its own if you want the tool without the game.
- Run `doctrines-editor api` to see what a rule may read, write the rule in your doctrine or behaviour file, `doctrines-editor check`, F9 in the game; the battle log names each rule that fires.

**Still code, on the list**: a `general` API for the commander's plan; attendants and wagon teams as behaviour files; camp, rout and officer constants; sounds from files; hand-made battlefields and maps; factions.

**Download:** the zip under Assets below. Unzip anywhere; README.txt inside says how to run it against your game folder.

## Editor 2026-10-24

First release of the modder's toolkit. The game's content is plain-text files; this is the reference and the checking tool for them.

**New since the 24 October (f) playtest build**
- The content moved out of code into record files under `Doctrines_Data/StreamingAssets/Data`: items (weapons, shields, armour, kit, relics, mounts); peoples (the stock men are raised from; a new race is a file); the units on the muster rolls; the doctrine presets; the AI's army archetypes; point costs; weather; roads and the march; scouting; the clock; relief, cover and world generation; the pose files for how weapons and horses are drawn.
- Mods: a folder under `Mods/` with the same layout. A record with a base id replaces it; a new id adds. Several mods load in name order.
- F9 in the running game reloads every file. Problems are listed in `output_log.txt` with file and line.
- One record format for every file: `item sword` at the margin, indented `key value` fields, `#` comments, quotes for names with spaces.
- Firearms and crossbows have three new `ranged` fields, each 0..1: `armour-piercing` (the share of the struck armour's protection the missile ignores), `shield-piercing` (the share of a shield's toughness that does not count), `stopping` (the least chance a hit puts the man down whatever he wears). Musket 0.7/0.9/0.8, arquebus 0.5/0.7/0.6, crossbow 0.3/0.4/0.25, bows 0.

**In the zip**
- `doctrines-editor.exe`: `check` lists every problem in your files; `list` and `show <id>` print what the game sees (a unit with its computed load, speed, protection and points); `new-mod <name>` scaffolds a mod folder. Run it from the game folder or set `DOCTRINES_DATA`.
- `Modding/`: the reference. `README.md` first, then one `SKILL.md` per domain: equipment, peoples, units and doctrines, armies and AI, rules and weather, poses and animation, maps and terrain, audio and art, tools and checks. Each lists every field, its unit and what the sim does with it, with examples, and says what is still code.

**Still code:** camp, rout and officer constants; fire-drill parameters; sounds loaded from files; hand-made battlefields and maps; factions; the peoples' appearance.

**Download:** the zip under Assets. Unzip anywhere; README.txt says how to run it against your game folder.


