# Doctrines — editor and modder's toolkit

The modding toolkit of **Doctrines**, a single-player grand strategy game on a decaying Ringworld, in development.
This repository holds the toolkit's releases, changelog and news. The game's source is private; its playtest builds
are at [Doctrines-playtest](https://github.com/TMaluszynski/Doctrines-playtest).

Each release on the [Releases](../../releases) page is a zip with:

- `doctrines-editor.exe`: checks, lists and shows the game's content files and scaffolds a mod folder
  (Windows 10/11 64-bit, no install; SmartScreen may warn about an unknown publisher: *More info* → *Run anyway*).
- `Modding/`: the reference, an index and one `SKILL.md` per domain, written for people and for AI assistants.
  Point your assistant at a skill file and ask it to add a weapon, a race, a unit or a doctrine.
- `README.txt`: how to use the tool; `CHANGELOG.md`: what changed.

## What can be modded

Everything the game acts on is a plain-text record file under `Doctrines_Data/StreamingAssets/Data`: weapons,
shields, armour, kit, relics and mounts; the peoples the men are raised from (races); the units on the muster
rolls; their doctrines (formation, standing order, triggers, signals, fire drill); the armies the AI raises; point
costs and cohesion budgets; weather; roads and the march; scouting; terrain and world generation; how every weapon,
shield and horse is drawn and animated. A mod is a folder under `Mods/` with the same layout: its records replace
base records with the same id and add new ones. Press F9 in the game to reload.

The sim itself (movement, combat, morale, couriers, drills, the campaign clock, terrain generation, rendering) is
code and reads its numbers from those files.

## News

Each release's notes are in [releases/](releases/); the cumulative [CHANGELOG.md](CHANGELOG.md) lists them all.
